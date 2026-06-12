---
title: "Making a local LAN repositary"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Ntweat on 2008-04-10
We are in a college which does not have a good net connection due to which many users are not able to switch to Linux (Ubuntu or Kubuntu ) from windows even when they want to and it takes alot of to update individual computers so we have decide to make a local LAN repository from which users can update... but no one has any idea how to so we will be very happy if any1 helps us.... We even have a server ready to store the repositories... 


Thanking every1 in advance  :guitar:

---

### Post by dstew on 2008-04-10
Here is a HowTo that shows how you should structure your repository so that it works with the apt-get program: [http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

---

### Post by SimonHickling on 2008-04-10
Have a look at apt-cacher.  It will run on your server and then you amend your clients sources.list to point at your server.  The first "upgrade" will then cache on the server and the subsequent "upgrades" will get the files from the server.

---

### Post by dstew on 2008-04-10
Here is something else: [apt-mirror]("http://apt-mirror.sourceforge.net/"). Because you are really trying to create a mirror of the regular archives, and not a custom archive, right? This might be better if everyone on your network is upgrading different systems at different times.

---

### Post by Ntweat on 2008-04-11
Well we just want regular updates.. instead of comps contacting the servers for updates it should jst download from the local lan server...

and ya the comps are different from intel to AMD laps desktops everythinh

---

### Post by hyper_ch on 2008-04-11
here's the info crom canonical:  [http://www.ubuntu.com/getubuntu/mirror/1](http://www.ubuntu.com/getubuntu/mirror/1)

---

### Post by Ntweat on 2008-04-11
another question i installed apt-mirror but how will users use the server...


Thanks hyper_ch will have a look..

---

### Post by Ntweat on 2008-04-11
hyper_ch its jst types of mirror i need to create 1... if there is a turtorial on how to create the server and config the client it will be very helpful

thanks

---

### Post by dstew on 2008-04-11
I think you just set up a regular server system, and people can get the files by TCP/IP and associated protocols like ftp or http. I think apt-get uses TCP/IP but I don't know for sure.

---

### Post by Ntweat on 2008-04-12
we tried putting the deb files on the server but problem is that the comps dont get updated when the server is updated the updates have to be done manually best is to create a repo server

---

### Post by hyper_ch on 2008-04-12
you'll have to create a mirror and update the mirror and then set the sources.list in the other computers to use the repos on your mirror.

---

### Post by Ntweat on 2008-04-13
Thanks... will try downloading apt-mirror downloading the 41 GB of files and set the sources.list of all computers to the server

---

### Post by phynix on 2008-04-25
This post worked for me. Try it out. What it does is when a client computer requests a package the server provides it then chaches the updates for the next client who needs it. The only limit is how fast your local lan connection is. Hope this helps.

[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

---

