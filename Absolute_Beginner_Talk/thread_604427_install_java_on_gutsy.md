---
title: "install java on gutsy"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by nblue on 2007-11-06
Hello fellow ubuntuer :) I have two newbie question
1/ it about installing java 
I want to install the java JDK on ubuntu. I have download the JDK from sun website. I have extract the .bin file onto /usr/local/lib
After that, I change directory to /usr/local/bin and do what I assume as set class path in window: sudo fn sh ../lib/javafolder/bin/* . 
However, when I do java -version it still say java 1.4 
I even do the install alternatives java thing but it say something about nothing to update because there only java 1.4
Is there any other way to install java or is there something i miss ?

2/I'm using the pendrivelinux website usb bootable with Gutsy and it seem they have swap contain the copy of the live cd with the tmp folder and it only have 700MB. Thus, anything I do that require tmp folder fill up very quick. Is there anyway to change the setting so that ubuntu till use the tmp folder on the dedicated ext3 that I have on the usb drive.
I don't know if my question 2 is clearly or not, but the main problem I want to sold is to install java on ubuntu or hopefully I will learn to install things after this.

---

### Post by kevinatkins on 2007-11-06
Hi,

In relation to your Java problem, search Synaptic for sun-java5-jdk or sun-java6-jdk and install from there - much easier!

You may need to enable the Universe / Multiverse repositories - I can't remember!

---

