---
title: "2 problems in xubuntu"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by shplog on 2007-11-08
Hey ppl.  Quite new to this.  Enjoying it so far, but massive speedbumps are in my way.

1) I'm trying to get Azureus to work.  I need to install Java first.  
-I know I downloaded and installed JAVA because "jre-6u3-linux i586.bin" is on my desktop.  And, I can listen to music on [www.myspace.com](www.myspace.com), watch youtube videos etc.  It was a small ordeal to get it working.
But, when I go to java.com and check my system to test if I have a Java runtime environment, it comes up negative.

I looked through sympatic (sp) and saw some java stuff, so I went ahead and installed it.

I read through some other threads about this, and the solution was 
> sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
however, when I enter it, I get
> E: Couldn't find package sun-java6-jre

HAALP!!

---

### Post by forestpixie on 2007-11-08
have you got multiverse repos enabled - system > admin >software sources

check against main, universe, restricted, multiverse and reload

---

### Post by mali2297 on 2007-11-08
What is your second problem?

---

### Post by shplog on 2007-11-08
> **forestpixie said:**
> have you got multiverse repos enabled - system > admin >software sources

check against main, universe, restricted, multiverse and reload
I don't know.  sytem > admin  (stop here)

I don't have "admin", I checked around for software resources and don't see that.
When you say "check against main, etc.  What exactly do you mean?  Try each one individually and remove java then reinstall?  Then try again??

My second problem was that I can't install Azureus.

---

### Post by plucky on 2007-11-08
Hi,

In Xubuntu it is Applications > System > Software Sources

You could try Applications >System > Add/Remove
Then at the top right of screen "show"   All available Applications

Search for "Ubuntu restricted extras"

Click on the box to install and Apply, this will install Sun Java.
Some of these applications are restricted depending on which country you are from and with Sun Java when it is installing will ask you to accept their license agreement.

Hope this helps
Peter

p.s I had problems with "Azureus" on Xubuntu ,I installed "Deluge" and that worked a treat

---

### Post by shplog on 2007-11-09
Thank you Plucky.
That did help, but Java still doesn't work.
I went through add/remove.  Found Java Webstart 1.4, which I assume is what I am looking for, and installed it.  The program downloaded some things, but now it's "applying changes" and it's never-ending.  It says "This can take some time" but really, it's not going to install.  

I tried rebooting a couple of times already.  It just won't install.

---

### Post by overdrank on 2007-11-09
> **shplog said:**
> Thank you Plucky.
That did help, but Java still doesn't work.
I went through add/remove.  Found Java Webstart 1.4, which I assume is what I am looking for, and installed it.  The program downloaded some things, but now it's "applying changes" and it's never-ending.  It says "This can take some time" but really, it's not going to install.  

I tried rebooting a couple of times already.  It just won't install.

Hi and can you use these commands in the terminal and post the out put here
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by shplog on 2007-11-09
> **overdrank said:**
> Hi and can you use these commands in the terminal and post the out put here
```
sudo apt-get update
sudo apt-get upgrade
```
Thanks mang.  Here:
> Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What does this mean?

---

### Post by overdrank on 2007-11-09
I was just checking to see if you had any errors trying to install the java. If you followed plucky post and installed the ubuntu restricted then you should need no other java. You may need to refresh your page if trying to few flash after installation.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Steveway on 2007-11-09
1. Why are you using Dapper? Do you really need the Long-term-support, is this a very critical machine?
2. Why Azureus? Deluge would be much better.

---

### Post by shplog on 2007-11-10
> **overdrank said:**
> I was just checking to see if you had any errors trying to install the java. If you followed plucky post and installed the ubuntu restricted then you should need no other java. You may need to refresh your page if trying to few flash after installation.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thank you.  Here is another output.

I got some restricted formats from that website.  
I installed sun java 5.0 successfully but it still won't work on java.com, but it's a start.

---

### Post by shplog on 2007-11-10
> **Steveway said:**
> 1. Why are you using Dapper? Do you really need the Long-term-support, is this a very critical machine?
2. Why Azureus? Deluge would be much better.

128mb ram, pentium 3 processor.  18 gb.

I will look into deluge my friend.  Much thanks.



Java...still not working.
My add/remove apps is not working too well.
It gets stuck on "Preparing Packages".  This is just not meant to be.

---

### Post by shplog on 2007-11-10
> **Steveway said:**
> 1. Why are you using Dapper? Do you really need the Long-term-support, is this a very critical machine?
2. Why Azureus? Deluge would be much better.
Deluge won't work because the dependancies are not satisfiable.  Libc6.
I tried to download it again...same problem.  It seems the package is for 7.04

---

