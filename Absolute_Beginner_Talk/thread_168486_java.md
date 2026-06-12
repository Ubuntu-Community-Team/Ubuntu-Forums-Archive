---
title: "java"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by themagicmnm on 2006-04-30
I just switched from debian to ubuntu
I'm trying to install jdk-1.5, but I'm having a lot of trouble

when I:
sudo apt-get install fakeroot java-package

it says that it can't find java-package

also when I:
fakeroot make-jpkg jdk......

it says that it can't find the command make-jpkg

Also if I break down and just try to run the binary:
./jdk-1.5......

it doesn't let me do that either.  Any suggestions?

---

### Post by nalmeth on 2006-04-30
I know this is a lazy way, but 
[AUTOMATIX]("http://www.ubuntuforums.org/showthread.php?t=138405")
If it says command missing, just try to "sudo apt-get install that_command"

---

### Post by testube_babies on 2006-05-01
If Automatix doesn't work (for instance, if you are using Dapper) go to [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) to find detailed install instructions.

---

### Post by joshrobinson on 2006-05-01
download the jre 1.5 bin from the sun java website


put it in /usr/java  you have to make the dir java
use sudo nautilus to have a root file browser

or sudo mkdir java while in the usr directory
rename the bin java.bin for ease of typing filenames

sudo chmod +x java.bin
sudo ./java.bin

hit q to get past the terms agreement
type yes to install

java -version
if it doesnt come back with 1.5.0 you need to make a symbolic link

go into /usr/bin you will see a file named java.. rename it to java2

go into the /usr/bin folder with terminal


ln -s /usr/java/(java folder name)/bin/java  
the java folder name in /usr/java is probibly jre1.5.0_06

so

ls -s /usr/java/jre1.5.0_06/bin/java

do java -version again and it should be 1.5.0 this time

---

### Post by nanotube on 2006-05-01
you can find java installation instructions if you follow the link in my sig and go to the Install Sun Java section.
(you can also find a sun java .deb file in there that you can just install with dpkg -i).
alternatively, you can add the seveas repository to your sources.list, and you will be able to install sun java through synaptic. (to find the seveas repository, just search google for it. :) )

---

