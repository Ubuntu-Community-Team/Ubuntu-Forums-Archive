---
title: "persistent breaks java"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by hiker_jon on 2008-01-31
Hi,

I want to use a livecd version of ubuntu to check on how my ImageJ plugin will work on Linux. 
ImageJ is an image processing program written in Java.

So I got the ubuntu 7.10 iso.  I gave up on trying to install Java, couldn't get it to work plus this is a livecd and who would want to reinstall each time.  So I downloaded an ImageJ distribution that contains its own jre.  That works fine, but it was a pain to try to save my environment each time.

So someone suggested that I try LiveCDPersistence. I did and guess what?  now my ImageJ jre is broken! I get the messages:
Error: could not find libjava.so
Error: could not find Java 2 runtime environment

*Let me emphasize that this does NOT happen when I do not use persistent.*
NOT TRUE!  Sorry for the mistake.  The problem is NOT persistence (which is not working for me anyways even though I followed the LiveCDPersistence doc).  The problem occurs when I copy the ImageJ directory to the Desktop or home folders.  It does not occur when I run from the copy of ImageJ on my laptop filesystem.

I am disappointed by ubuntu's decision to not support Java.  ImageJ does not run on the replacement Java (gij).  Also as far as I can see Java applets don't run in Firefox on ubuntu.  It is not reasonable to require people to install Java (look at all the posts on these forums about being unable to get Java working) to get an applet working for internet browsing.  

Jon

---

### Post by emarkd on 2008-01-31
Ubuntu doesn't support the latest version of Java because its not in line with Ubuntu's philosphy on free (as in freedom) software.  You can easily install java6 if you choose by enabling the extra repositories in Synaptic and installing sun-java6

---

### Post by hiker_jon on 2008-01-31
For me,  I would just like ubuntu users to be able to use my plugin.  One reason I wrote it in Java is to make it available to users of different operating systems.

 ImageJ is a remarkable program.  It makes it easy for me to piggyback my plugin onto a great image processing program that works on PC's, Mac's, and MOST versions of Linux.

---

### Post by jordanmthomas on 2008-01-31
How is it not reasonable for a user to have to install Java to be able to run Java applets?  I don't know how to solve your problem with the persistent LiveCD, but was just wondering why you think it's unreasonable to have to install Java.  Nearly every OS needs Java to be installed before Java plugins will work.

---

### Post by emarkd on 2008-01-31
But while Sun makes all versions of Java available for Linux (and lots of other OS's), they're not really free.  They're just binary blobs and that goes against the idea of having complete control over the software that's on your computer.  Ubuntu's default configuration contains only free software, but it tries hard to make those binary bits just a few clicks away for those who want to use it.

You can always rewrite your software targeting the free version of Java.  I think it's in line with version 1.4, but check that before you start coding.

---

### Post by hiker_jon on 2008-01-31
> **jordanmthomas said:**
> How is it not reasonable for a user to have to install Java to be able to run Java applets?  I don't know how to solve your problem with the persistent LiveCD, but was just wondering why you think it's unreasonable to have to install Java.  Nearly every OS needs Java to be installed before Java plugins will work.

My experience was that I couldn't get Java installed so I assume that others new to ubuntu might have the same problem.  I have no quarrel with having to install Java if it is at least reasonably easy to do.

---

### Post by jordanmthomas on 2008-01-31
Ah, I figure it'd be easy on Ubuntu.  In Archlinux, I just have to install a package called jre (or jdk if I want it).  I'd say overall it's at least as easy to install as it is in Windows.  Is it not similar in Ubuntu?  I'm not really familiar with Java issues in Ubuntu.

---

### Post by Blutack on 2008-01-31
sudo apt-get install sun-java6-jre
should do the trick if your livecd computer has a net connection.

---

### Post by hiker_jon on 2008-01-31
ubuntu@ubuntu:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

