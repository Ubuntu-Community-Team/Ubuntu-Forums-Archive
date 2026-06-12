---
title: "No Internet"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Rhyader on 2007-10-16
I'm trying out Ubuntu on a computer that I recently set up. It has Windows running OK, and the network card and internet access are working in Windows.  Doing anything with Ubuntu, however, has been pretty hard. As far as I can tell, Ubuntu thinks that all updates and all commands to install something must get files from the internet or a network. Which makes it pretty hard to do anything if you don't already have this access!   My first experiment is to try to make the wireless card work. From what I've read people report success with using some sort of software thingy that lets them convert the windows driver for use with ubuntu. To do this I have to get something called "bcm4318-fwcutter".   Commands using "apt-get" do not work, because I think ubuntu is trying to read from the internet.  I've looked at the /etc/apt/sources.list file and this seems to be true. I can't read from the internet with ubuntu: that's what I'm trying to set up. I could download files in windows, then copy them to a linux partition.  
  
So I guess I would ask 
+ How can I install anything in ubuntu without it coming from the internet?
+ Can "apt-get install" commands install from a local source? 
+ Can I get ubuntu, through /etc/apt/sources.list or otherwise, to read from a local directory? 
+ How could I find something, such as "bcm4318-fwcutter", from http://us/archive/ubuntu.com/ubuntu while I'm running windows?

---

### Post by rbprogrammer on 2007-10-16
you can download the file here: [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/)

i would recommend downloading one of the [ .deb ] files since they are the easiest to install.  also, depending on your computer architecture will determine which version to download.  for instance, for my computers, i would download bcm43xx-fwcutter_006-1_i386.deb, but if i were to run the 64-bit version of ubuntu, then i would download bcm43xx-fwcutter_006-1_amd64.deb.

as far as copying it to a linux partition, you have a few options.  you can either try a flash/thumb drive that is formatted as FAT32 and then in linux just copy it to you desktop.  or you can get the driver for windows ( [here]("http://www.fs-driver.org/") ) that allows you to write to linux partitions.  then your can just save it to your linux desktop.

hope that helps you.

---

### Post by Rhyader on 2007-10-16
It seems to be working now ! 
I had to download bcm43xx-fwcutter_006-1_i386.deb and use it. Apparently a ".deb" file is an executable install package After that I had a bcm43xx-fwcutter command and could use bcm43xx-fwcutter on the wl_apsta-3.130.20.0.o file.  After that, following instructions HERE
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-e11c3138afb4f9fb637d8f0a6d234add934830cc]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-e11c3138afb4f9fb637d8f0a6d234add934830cc")
will make it work.

---

