---
title: "java runtime Firefox plugin"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by Nopposan on 2005-06-29
I need to use the Java Runtime Environment in order to participate in an online chat with Linksys so they can help me install a wireless notebook adapter on this Ubuntu- OS-only Compaq laptop.  

I thought I already had the JRE installed, but Firefox thinks otherewise.  However, the main thing is that I don't know how to install any software package that has been downloaded to my desktop; I only know how to use the Synaptic package manager and the archives & packages already listed there.

Help me, please!

---

### Post by sonny on 2005-06-29
I guess this link will help you: 
[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

And for installing software, I recomend you fisrt to look up for simething in the repositories using synaptics, and installing from there, you can also do some simple task in the command prompt.
> Code:
$ apt-cache search "one-word-description"
$sudo apt-get install "program-name" 
At the word description you should something like "java to search for some java plugings, libraries or any program that is related to java.
Have a look to the [www.ubuntuguide.org](www.ubuntuguide.org) to find out more about ubuntu and linux in general.

---

### Post by obx-jdt on 2005-06-29
[QUOTE=Nopposan]I need to use the Java Runtime Environment in order to participate in an online chat with Linksys so they can help me install a wireless notebook adapter on this Ubuntu- OS-only Compaq laptop.  

I thought I already had the JRE installed, but Firefox thinks otherewise.  However, the main thing is that I don't know how to install any software package that has been downloaded to my desktop; I only know how to use the Synaptic package manager and the archives & packages already listed there.

Help me, please![/QUOTE]
in the (java) file you downloaded, there is a "read me" file. It'll tell you exactly what to do/how to install it. Follow the instructions word for word. 
Learning to install things on Linux, and useing the command line can be difficult at first. But once you install something from the command line one time, you'll have made a huge step in learning the basics of UNIX/Linux. On the Sun/Java download page, there are instuctions also. I assum you want to install Java system wide, and not just for 1 user. So you'll need to use 'su' (super user), or log in as root.
Make sure you you download the [Linux (self-extracting file)](http://jdl.sun.com/webapps/download/AutoDL?BundleId=10149) and not the RPM (RPM=RedHat Pakage Manager).
[This will take you to the insructions for installing it.](http://www.java.com/en/download/help/5000010500.xml#selfextracting) Print them up, and it'll be easier for you to install that way instead of having to jump back and forth between windows.
Good luck, and let us know what happens ;-)
Here's an example of that you'll need to write in the treminal to install java....

su (this will prompt you for your root password)
now you'll need to navagate to the directory where you saved the installer to.
/home/Nopposan/desktop/jre-1_5_0_04-linux-i586.bin
then hit enter....after about 5-10 seconds, java should be installed.
If you get permission denied, right click on the installer, perrmissions, and check "exicutable". Try again.

---

### Post by Kvark on 2005-06-29
Just install the package called "jre" with apt-get/synaptic, firefox will recognize it right away. Takes a few minutes and requires no skill at all.

...or if you feel like it, you can download from sun's website and spend hours trying to figure out how to get it to work with firefox.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=Kvark]Just install the package called "jre" with apt-get/synaptic, firefox will recognize it right away. Takes a few minutes and requires no skill at all.

After you do this of cource:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

> ...or if you feel like it, you can download from sun's website and spend hours trying to figure out how to get it to work with firefox.

Using synaptic is a much easier option.

---

### Post by Nopposan on 2007-01-24
Thanks everybody.  I succeeded in installing the java runtime; 'think I used synaptic but I'm not certain anymore.  'Sorry it took me so long to respond.

---

