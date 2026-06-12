---
title: "At wit's end here with this thing."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by naughtywill on 2007-04-30
I am trying to get this damn thing to work. I CANNOT get any further than this  here.......
> root@will-desktop:/home/will# sudo apt-get install sun-java6-jdk
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@will-desktop:/home/will# sudo dpkg --configure -a
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


 I have  downloaded the file from sun.I do not know how to let the file be owned by root.  I tried following to the TEE the other post here...[http://ubuntuforums.org/showthread.php?t=423615]("http://ubuntuforums.org/showthread.php?t=423615") Still ZERO luck in doing anything. Can anyone here please help me?

---

### Post by Seisen on 2007-04-30
This should help you.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_Upgrade_to_Java_Development_Kit_.28JDK.29_v6.0]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_Upgrade_to_Java_Development_Kit_.28JDK.29_v6.0")

---

### Post by oilchangeguy on 2007-04-30
do what the message says. open a terminal and type sudo dpkg --configure -a
then press enter.
looks like you did something to stop the download or install process.

---

### Post by bobplano on 2007-04-30
why is there a "#" before your command lines? that is usually a comment character. try getting rid of them unless it is for some reason part of the folder

---

