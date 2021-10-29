1. Find the count of log statements in the attached file "access.log" with successful response (status code 200):

ANSWER: cat access.log | grep 200 | wc -l

2. Write command to find the filenames containing words DEBUG, ERROR, and INFO in any directory of the filesystem.

ANSWER: 
find / -name DEBUG 
find / -name ERROR 
find / -name INFO

3. What would be the sed command to convert the string input "Ab1Cd2Ef3Gh4Ij5….." to "abcdefghij…."?

ANSWER: echo "Ab1Cd2Ef3Gh4Ij5….." | sed 's/./\L&/g'

4. Write a shell/python script/program to return true if the opening and closing braces
are complete, otherwise false.

e.g:

a. Input string:

List { information {{about the FILEs (the current directory by default). Sort entries
alphabetically if} none of -cftuvSUX }nor --sort } is specified.

Output: True

b. Input string:

Performs { the specified action on the files. { Valid actions are view, cat (uses only
"copious output" rules { and sends output to STDOUT) , compose, com‐posetyped, edit and
print. If no action is specified, the action will be determined by how the program was called.}

Output: False

ANSWER: Done this question in Python Language.

line=input("Input string: ")
count_i = 0;
count_j = 0;
for i in range(0,len(line)):
    if (line[i] == '{'):
        count_i = count_i+1;
for j in range(0,len(line)):
    if (line[j] == '}'):
        count_j = count_j+1;
if (count_i == count_j):
    print ("True");
else:
    print ("False");




5. Write steps to create and publish a docker image to the docker repository. e.g., Run tomcat image with a customized landing page, and should be accessible at: http://localhost:8080/

ANSWER:
Step1:
First create a Docker file.

vim Dockerfile

Inside Dockerfile:-
FROM tomcat:latest
CMD systemctl start tomcat
CMD systemctl enable tomcat

Step2:
Build the image on local machine with the username of docker hub as prefix and then / the name you want, We can also specify versions to the image.

docker build -t kanishka05/tomcat:v1 .

Here I have used . as I am running this command in the same directory.

Step3:
Upload to the Docker Hub

docker push kanishka05/tomcat:v1

Later we can use this image anywhere by just downloading 

docker pull kanishka05/tomcat:v1

BONUS_QUESTION
6. Given the following snippet of nginx server configuration:
server {
        listen 80 default_server;
        root /var/www/html;
        server_name *.senpiper.com senpiper.com;
}
Write a location block for requests “/api” that will server the requests from backend
controller “/welcome/home”.

ANSWER:
server{ 
       listen 80 default_server;
       root /var/www/html;
       server_name *.senpiper.com senpiper.com;
       location /api {
         return 307 /welcome/home;
       }
}

It is an Example of rewrite.
