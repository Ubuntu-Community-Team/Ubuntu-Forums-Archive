---
title: "creating web page"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ggnewman on 2007-06-28
I am a very new user to Linux. I am helping my son school to update their school website, unfortunately for my I am only well verse to windows. I am trying to upload the web page design from my publisher to the Linux server at school what do I need to do. Please help?:(

---

### Post by Rocket2DMn on 2007-06-28
Typically you need to upload the html file to the webserver computer.
gFTP is a popular file transfer program that I and many other users like.  You will have to have login permissions to the computer at school as well as it's IP.
if you don't have it installed yet, you can run
```
sudo apt-get install gftp
```

---

### Post by ggnewman on 2007-06-28
Thanks for answering my question - Rocket 2DMn . But can I upload it from my home computer into the Linux server, having their password. Like Nuvu actual have a software u can download and you can just type in the ftp and I believe one can also update the web site directly from the web broswer of their computer. The reason I ask is because the school is hoping that I can still support them remotely. Thanks;)

---

### Post by Rocket2DMn on 2007-06-28
Some servers let you access ftp through a browser by just typing the address 
[ftp://serverip : port](ftp://serverip : port) (no spaces - port may not be necessary)
There are ftp clients for windows as well, and if you're using firefox, you can use the extension FireFTP.  Some web design programs allow access via built in ftp connections to the server as well.

---

### Post by wigglydiggly on 2007-06-28
Its very easy to upload a website using Nuvu or any other modern website design software.  The only question to be answered is "Do you have the webserver properly configered for FTP uploading.  One of the best FTP servers availible with linux is ProFTP.  Once installed it only a matter of configering both router and FTP server "Remote Host" config files.  I've only been using linux for a year or so, and I use "Webmin" to help configure the servers.  Webmin is a web based administration tool that eliminates the need to edit config file in text.  I've found lots or HOWTO's on this site and through google.  I would also like to thank you personally for helping out with "our" schools.  Its good people like you that makes this a better world.  Good luck!!

---

### Post by ggnewman on 2007-07-03
Actually the school does use Webmin. So how do I config. the server so that I can upload it remotely.

---

