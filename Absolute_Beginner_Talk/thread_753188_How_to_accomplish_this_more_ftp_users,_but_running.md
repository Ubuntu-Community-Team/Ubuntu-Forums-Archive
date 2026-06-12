---
title: "How to accomplish this: more ftp users, but running under www-data"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by ildefonse on 2008-04-12
Hi all,

Could someone help me with the following situation? I am running Ubuntu server, with proftpd.

1) /var/www/ is owned by www-data, as well as all the sub directories.
2) I want to add a new user to the system, which will be able to access a specific subdirectory inside /var/www/, let's say, /var/www/somecustomer/, plus that directory's subdirectories and files.
3) I want this user to be able to log on to FTP, and have that as it's home directory.
4) I want the files created by that user there, still be writable by www-data, as I use that user to connect to the ftp server myself.

So far what I did and tried is:

1) Added the new user.
2) Changed his home directory to match /var/www/somecustomer/
3) Added the user to the group www-data
4) Changed ownership of /var/www/somecustomer/ to somecustomer, leaving the group as www-data
5) Changed file permissions for this directory to 775.

Result: When I log in with FTP, I am disconnected straight away, and in the log file I see that the chdir operation to /var/www/somecustomer/ is not allowed.

Question: How do I fix this in the best way possible? Maybe there is another way to do it that I am not aware of.

I read manuals on proftpd, I did searches on the forum, google, etc,. but I couldn't find what I need.

Thank you for your time in advance.

PS: I will need to do this for several users, each with their own directory. What are the steps you would recommend?

---

### Post by hyper_ch on 2008-04-12
hmmm, maybe it would be better to setup a isp-like server directly....

[http://www.howtoforge.com](http://www.howtoforge.com) has "perfect howtos" for setting up such a server... I'd recommend to use debian but you can of course also use ubuntu. There are (almost identical) howtos for both.

If you follow it, you will have a fully function server with mail, ftp, web and the ability to manage different users easily.

---

