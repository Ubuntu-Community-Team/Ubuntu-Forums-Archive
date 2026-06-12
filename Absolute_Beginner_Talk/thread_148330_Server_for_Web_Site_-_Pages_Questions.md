---
title: "Server for Web Site - Pages Questions?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-21
Hello All !!!

I am experimenting with Setting Up a Web Server.
I have the following questions?

_Question 1_:
I would like to know if the Rights shown below (I got with an "ls -l" command) are the correct Rights I should given to my Web Server's Home Page:

1. drwxr-xr-x  2 root root 4096 Mar 21 04:40 apache2-default
2. -rwxr-xr-x  1 root root 6497 Mar 22 00:31 bbb.html
3. lrwxrwxrwx  1 root root   21 Mar 22 01:25 phpmyadmin -> /usr/share/phpmyadmin

_Question 2_:
Right now, whenever from my Mozilla Firefox Internet Browser, I visit the address "localhost/var/www", I see the Web Page named "apache2-default"
If I would like to see the (above) listed #2 choice, how would I have to go about it?
Do I have to delete the file named "apache2-default" & rename the file "bbb.html" to the name "apache2.default"?
So, the Home page of the Web Site I create MUST have the name "apache2-default"?
OR: It is flexible & I can give ANY name I want to my Home Page?
If the later is the case, where would I declare the NEW name of my default Home page? (what would I have to search&replace)

_Question 3_:
Do I need the (above) listed #3 choice - i.e. the file named "phpmyadmin -> /usr/share/phpmyadmin" inside the "/var/www" folder?
Can I delete it? (Why does it have to be inside there?)

_Question 4_:
How can I find what my current IP is (I know it is NOT static) from my Internet Service Provider?
Note:
I want to be able to find it & then probably ask you to visit me & see if you can IN FACT see my Web Page...
This would be the ONLY way to verify that my Web Page is Visible to the outside world!!! (I am also behind a Router...).

Thanks in advance for your help!!!

---

