---
title: "Desktop lamp server combo"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2006-06-20
I need to setup my box as a desktop and server, I use this box for everyday surfing, emails and crap like that, but i would like to install apache, mysql, php and ampache to catalog and stream my mp3, ogg music library.  I noticed on the ubuntu site that they have a lamp server setup iso image.  My question is does ubuntu offer the lamp server package for download and install on my ubuntu desktop setup.  This server will be on my lan so it will not recieve much traffic.  Or will i have apt-get everything i need.

Thank in advance for any help

---

### Post by rai4shu2 on 2006-06-20
I think you will have to apt-get what you need.

---

### Post by tbresson on 2006-06-21
You have to select the packages you want yourself.

Open up Synaptec and search for Apache2, PHP5 and Mysql.
Check the Apache2, the PHP5 and the mysql-server and remember to select the php5-mysql + php5-mysqli.

Recently something seems to have changed though, so if you have problems connecting to the mysql server from php run this command:

sudo dpkg-reconfigure php5-mysql

And don't forget to set the mysql password after install with:
mysqladmin -u root password YourPassWordHere

Then you should be ready to go :D

---

### Post by hotbrainz on 2006-06-21
A very easy way of setting up LAMP whihc  I used is XXAMP

Use the link in my signature. Worked like a gem. Up and running in 10 minutes.

---

### Post by mumushi on 2006-06-21
[QUOTE=hotbrainz]A very easy way of setting up LAMP whihc  I used is XXAMP

Use the link in my signature. Worked like a gem. Up and running in 10 minutes.[/QUOTE]

i tried installing it and its working great my problem is i dont have previledge creating new databases in pma :(

---

### Post by mumushi on 2006-06-21
i am really new using php apache and mysql any guide that will help me be acquianted with it is much appreciated. i wanted to run my own site :). its possible right?

---

### Post by mumushi on 2006-06-21
one more thing. as i explored and check the tools if it all works i found out that when i used phpadmin it ask me for a user name and pass when i input the username and pass it tell me that i could not log into MySql Server. i very sure i inputed the correct username and pass. What seems to be the problem here? Any help is greatly appreciated. thanks!

---

### Post by houstonbofh on 2006-06-21
Did you use the username and password for mysql, or for ubuntu?  It is looking for a mysql username and password.

---

### Post by mumushi on 2006-06-22
[QUOTE=houstonbofh]Did you use the username and password for mysql, or for ubuntu?  It is looking for a mysql username and password.[/QUOTE]

i used /opt/lampp/lampp security in the terminal and had set a password for mysql. that same password was the one i inputed when i log in to mysql. im very sure i didn't use the one for my ubuntu.

---

### Post by ubuntu27 on 2006-06-22
***Bump***

---

### Post by cjssmo on 2006-07-21
answered my own question, If you want a lamp server along with the ubuntu desktop all you have to do is download the server iso image, burn it to cd, install the lamp server from cd.  Once it is installed all you have to to then is use "sudo apt-get install ubuntu-desktop" and there yea go you have apache, mysql, php and the ubuntu desktop installed all on the same box, very painless.  I used phpmyadmin to set up mysql server and bam up and running.  I use this perticular setup with "Ampache" which is a php script which catalogs your mp3, oggs, flac etc and allows you to remotely stream them, it is really cool
Hope this helps someone

---

### Post by loudernet on 2006-12-02
I am a super noob but want to do the same thing as in your post

how do you use
"sudo apt-get install ubuntu-desktop"

I installed the LAMP server and get a command promp.

I typed "sudo apt-get install ubuntu-desktop" in the command prompt and it says -bash: sudu: command not found.

any tips would be awesome.

Thanks

---

### Post by ttheis on 2006-12-12
You just mis-spelled "sudo" as "sudu"

I have also done this and it works like a charm!

-Tom

---

