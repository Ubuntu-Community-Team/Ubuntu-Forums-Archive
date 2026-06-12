---
title: "Tomcat is going to kill me soon, need help soon or may chop up computer"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-11
I installed 6.06 LAMP.  I also installed Tomcat 6 with this tutorial. 
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

 Tomcat isn't running though (according to my dead 8080 and 8180 ports and Webmin) and I don't even know if I have java installed.  I ran "java -version" but java isn't a known command.  I tried to install java , but I got this error:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-jdk"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-bin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I'm at my wit's end.  I'm too much of a noob to know how to find my problem.  I can't tell if Tomcat is even running!  Webmin doesn't have it listed in processes.  I can't tell if java is installed.  I can't do anything with Ubuntu at all until I get this going.  

I really want to like Linux, but this is really killing me on the inside.  I was going to convert all my stuff to ubuntu, but this is ridiculous.  Crap on this thread all you want - this ain't easy.


**edit**
and another thing: this stupid command gives me an error:
dpkg –get-selections | grep sun-java that "-g" isn't a command](*,)](*,)](*,)](*,)](*,)

---

### Post by insineratehymn on 2008-03-11
Yo.

I'm gonna point you to a thread already on this forum:
[http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006)

Titled: How to install Tomcat 5.5.

That is a slightly old post, but fundamentally it should still be sound.

Don't give up on linux just yet... Once you get past all of the idiosyncracies that kept you on Windows you will begin to love it for its power and efficiency.

---

### Post by thepiston on 2008-03-11
Thanks for the help, but that link shows you how to install java5, not 6.  The Tomcat tutorial has links for 6. I tried the first command on the link you sent me and it says "couldn't find package sun-j2rel.5".  i have all the universe and multiverse lines uncommented in sources.list...

---

### Post by insineratehymn on 2008-03-11
Damn.
Sorry, its late for me..

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

Try that one.

---

### Post by thepiston on 2008-03-11
yep, must be really late - that's the tutorial I posted above and have already followed...

I don't think I have java installed, when I do the dpkg -get... command it says that "-g is not an option"

---

### Post by thepiston on 2008-03-11
IS this tutorial for Ubuntu 7.04 and not 6.06 or 6.10???
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

All of the Java references use Java6, but on this tutorial it says that 6.06 only uses Java5
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Either way, I get errors trying to install java of any type.  **** it, I'm installing Windows, this blows.

---

### Post by LeoSolaris on 2008-03-11
There is a glitch still with the java in the repos. You have to download it from Sun as an .rpm and use alien to turn it into a .deb so it can be installed.

[http://monkeyblog.org/ubuntu/installing/#rpm](http://monkeyblog.org/ubuntu/installing/#rpm)

That's how to make use of rpm's and unfortunately, just like Windows, you will have to get java online rather than the nifty repo system.

After that, your tutorial of Tomcat should work just fine.

Leo

---

### Post by handydan918 on 2008-03-11
try ```
dpkg **--**get-selections (with 2 - instead of 1 -)
```

---

