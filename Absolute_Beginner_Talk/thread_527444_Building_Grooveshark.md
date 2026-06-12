---
title: "Building Grooveshark"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-08-16
Hey. I just got a Grooveshark user name and password and they have a install. But here is teh deal. If it is not in package manager or in a .deb file then I really really am clueless on how to install it. Can someone give me a hand please?

---

### Post by diatribe on 2007-08-16
what kind of file is it

---

### Post by osc1882 on 2007-08-16
sharkbyte.sh
starter.jar
terms.rtf
updater.jar

And in this folder there is a folder called lib and
with in the lib folder there are these files:
fast-md5.jar
MD5.so

---

### Post by djrobthaman on 2007-09-10
I just got an account with them as well and have been unable to build it.  I get a message with the following:

```

Failed to load Main-Class manifest attribute from starter.jar

```

osc1882, did you get it to work?  Or does anyone else know how I can build it?

Thanks

---

### Post by anemptygun on 2007-09-26
This might help :)

[http://beta.grooveshark.com/register.php?os=linux&distro=debian](http://beta.grooveshark.com/register.php?os=linux&distro=debian)

---

### Post by anemptygun on 2007-10-01
Did that help?

---

### Post by osc1882 on 2007-10-04
I'm sorry. I really really really don't know how to build something. If it's not in a .deb file.. i'm useless.

---

### Post by anemptygun on 2007-10-04
Well it shouldn't be hard at all. Let's see if we can get it done. The easy way to do this would be to extract the sharkbyte folder out of sharkbyte.zip (this is the file you downloaded from grooveshark). It does not matter where you put the sharkbyte file, on your desktop, in your home file, it really dosen't matter. Now open up that sharkbyte folder. There will be several files in there but the one you need to pay attention to is the one labeled sharkbyte.sh . Now double click on sharkbyte.sh and choose to run as application. That should be all you have to do.

---

### Post by oxalá on 2007-10-09
> **anemptygun said:**
> Well it shouldn't be hard at all. Let's see if we can get it done. The easy way to do this would be to extract the sharkbyte folder out of sharkbyte.zip (this is the file you downloaded from grooveshark). It does not matter where you put the sharkbyte file, on your desktop, in your home file, it really dosen't matter. Now open up that sharkbyte folder. There will be several files in there but the one you need to pay attention to is the one labeled sharkbyte.sh . Now double click on sharkbyte.sh and choose to run as application. That should be all you have to do.

...which i know how to do, normally, except in Gutsy it appears that sharkbyte.sh is already associated with the Text Editor. I'm not sure how to get it to just run as an application.

this is one of those times that being comfortable with the command line would pay off, no?

---

### Post by philinux on 2007-10-09
> **anemptygun said:**
> Well it shouldn't be hard at all. Let's see if we can get it done. The easy way to do this would be to extract the sharkbyte folder out of sharkbyte.zip (this is the file you downloaded from grooveshark). It does not matter where you put the sharkbyte file, on your desktop, in your home file, it really dosen't matter. Now open up that sharkbyte folder. There will be several files in there but the one you need to pay attention to is the one labeled sharkbyte.sh . Now double click on sharkbyte.sh and **choose to run as application**. That should be all you have to do.

Within the launcher choose run as an app. Maybe create a launcher for it

---

### Post by Chitownguy885 on 2007-10-09
> **oxalá said:**
> ...which i know how to do, normally, except in Gutsy it appears that sharkbyte.sh is already associated with the Text Editor. I'm not sure how to get it to just run as an application.

this is one of those times that being comfortable with the command line would pay off, no?

Makeing it run as an application is very simple. All you have to do is: 

1. right click "sharkbyte.sh" & go to properties

2. look towards the bottom and click on "run this as application".

3. Click apply and OK.

Now you should be able to double click "Sharkbyte.sh" and a dialog should pop up to ask you to run it. 

NOTE: You may have to open the file in a terminal with "Sudo" in front of it to give it root privliages.

---

### Post by Chitownguy885 on 2007-10-09
Now for my problem. Hopefully I am not the only one who has exspericned this problem. 

When I try to run the "sharkbyte.sh"  with root privlages i this this error.

"Failed to load Main-Class manifest attribute from starter.jar"

Any ideas???  ](*,)

---

### Post by oxalá on 2007-10-09
> **Chitownguy885 said:**
> Makeing it run as an application is very simple. All you have to do is: 

1. right click "sharkbyte.sh" & go to properties

2. look towards the bottom and click on "run this as application".

3. Click apply and OK.

Now you should be able to double click "Sharkbyte.sh" and a dialog should pop up to ask you to run it. 

NOTE: You may have to open the file in a terminal with "Sudo" in front of it to give it root privliages.

i am an idiot.
that seems to have worked.
thank you! :-D

EDIT: well, no.  I now get the option box now when i try to run sharkbyte.sh, but now nothing happens at all.  Weird.

---

### Post by Chitownguy885 on 2007-10-10
Try adding the sudo command in the text file, Or just run the sharkbyte.sh with sudo.

---

### Post by oxalá on 2007-10-12
update:

this is my output:

oxala@zanzibar:~/Sharkbyte$ sudo java -jar starter.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: com/grooveshark/updater/Starter (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

---

### Post by tikal26 on 2007-10-12
I get the exeact same message. I am in kubuntu so I don;t know how to make it run as an application

---

### Post by paulothesilva on 2007-10-20
First of all I would like to apologize for the all the trouble and frustration caused by the old version of Sharkbyte. As an Ubuntu user myself, I know how much of a pain the old version was, but fortunately we finally have a DEB and RPM package for Sharkbyte and you can download them from [www.grooveshark.com/downloads](www.grooveshark.com/downloads) 

IMPORTANT NOTES:
*There is a problem with the current version and some of libraries will not work with Java amd64, for now as a "quick fix" you can install the 32 bit version of Java 6 (you can install it from the applications->"add/remove..." and search for "Sun Java 6 Web Start (32 bit)", also make sure that the java link points to the 32 bit version of Java . 

If it doesn't point to the correct version  you can change the link by doing the following :

cd /usr/bin
sudo rm java
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/bin/java java

The next version of Sharkbyte will be compatible with amd64.

*By default Ubuntu has GCJ instead of Sun's JRE , and Sharkbyte will not work with GCJ , it requires Sun's JRE 6 , 

If you have any other problems I would recommend using the forum at [www.grooveshark.com](www.grooveshark.com) ,or the feedback section below the player (it has this weird guy's picture next to it, you can't miss it) , or even messaging me in Grooveshark(my username is paulo) for a faster response.

Once again, sorry for old the version and thanks for your interest in Grooveshark.

---

### Post by anemptygun on 2007-10-20
YES!!!!!  w00t!

---

### Post by anemptygun on 2007-10-29
anyone gotten a chance to try it yet? I haven't I've been to busy lately.. :S

---

