---
title: "First Time Webserver"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by neleininger on 2007-12-04
Hello everyone, I am setting up my first web server and have everything running except two things. I followed the perfect server guide for Ubuntu 7.10 at howtoforge.com. I want to build all of my websites using dreamweaver on the mac with OS X 10.5 and the upload then to my server locally over my network,instead of through ftp. i was wondering how to open up the folder were my website will live on the server so my mac can make a connection over the local network.

My second question is since using this setup and ISPconfig i cannot get my E-mail program to pop3 my mail server that has been setup. I was wondering if any knew where i could find some good instructions to get this working. I have scoured the help files for ISPconfig and haven't been able to figure anything out.

Thanks for all your help in advance.

---

### Post by sethvath on 2007-12-04
I'm assuming your webserver sits on the same network you're using right now and it is bridged (network bridge)? ie 192.1.1.1 (home network) 192.1.1.2 (web server)

If so you can simply key in [http://192.1.1.2/](http://192.1.1.2/) in your web browser and you should be able to access your webserver

---

### Post by neleininger on 2007-12-05
Yes it does sit on the same router, however that is not the problem. I want it to share a folder with my mac so i can have dream weaver browse for the folder and find it on my server. I cannot find a way to have my server only broadcast that folder on my local network, and not out into the internet.

---

### Post by shankscomp on 2008-01-13
Sounds like you need to install SAMBA on the webserver and have one of the shared folders be the website you're trying to edit...  However, that can open up security holes.

---

