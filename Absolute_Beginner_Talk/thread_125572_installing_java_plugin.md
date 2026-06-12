---
title: "installing java plugin"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Great_King_Rat on 2006-02-04
I am a new convert to Linux, and am stuggling to learn the coding techniques needed to get things to work. I am trying to install the the Java runtime enviroment so that my wife can play games off Yahoo. I have downloaded the jre-1_5_0_06-linux-i586.bin file to my desktop. I have been able to access the terminal screen and have made a java directory /home/simon/java I can get into the java dir, but cannot add any files or make the jre file to go in to it. What am I doing wrong? I tried installing thru the Synaptic program but can not figure out how to get that too  work...I am very much a newbie armed with a ..for dummies book so any help would be greatly received!!
Many thanks

---

### Post by Klaidas on 2006-02-04
You could install it using [automatix]("http://www.ubuntuforums.org/showthread.php?t=114251") :)

---

### Post by rayban on 2006-02-05
:cool:  a few days ago i had the same problem, try this:

in a terminal:
sudo bash  (enter)
(asks your password)
copy your  .bin file to /usr/share/
 # chmod 700 jre-1_5_0_06-linux-i586.bin
 # ./jre-1_5_0_06-linux-i586.bin
which will create once you accept the licence agreement

jre1.5.0_06/
 symlink: # ln -s jre1.5.0_01 java.current. 
in future releases you only have to update this symlink with a new version :)
 update-alternatives to use java and java_vm as commands:

  # update-alternatives --install /usr/bin/java java /usr/share/java.current/bin/java 120
  #update-alternatives --install/usr/bin/java_vmjava_vm/usr/share/java.current/bin/java_vm 120
  test your installation: # java -version
 
which will show you something like this
      java version "1.5.0_06"
      Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06)
      Java HotSpot(TM) Client VM (build 1.5.0_06, mixed mode....etc)


integration on the browser
Mozilla Firefox

 in the same consoleconsole #
   # cd /usr/lib/mozilla-firefox/plugins/
   # ln -s /usr/share/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
   
after restarting firefox it works (at least for me it did)

---

### Post by diebels on 2006-02-05
Go into System->Administration->Software-properties in the gnome panel

Add a custom repository(plf)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Search for sun-j2 in synaptic and install it.

---

