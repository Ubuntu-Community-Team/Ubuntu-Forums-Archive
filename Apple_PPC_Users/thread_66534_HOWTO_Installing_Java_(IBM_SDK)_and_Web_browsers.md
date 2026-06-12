---
title: "HOWTO: Installing Java (IBM SDK) and Web browsers"
date: 2005-09-17
forum: Apple PPC Users
---

### Post by lol on 2005-09-17
I wasn't able to find this anywhere else, and therefore decided to make a small HOWTO so that others will avoid loosing as much time as I did.
By the way, this method to install Java is much better than the one described in the Ubuntu guide or Wiki (IMHO). If possible, I would like to update the guide, so if somebody knows how to do so, please tell me. Unless you want do it yourself, of course :)

________________________________
INSTALLING JAVA - IBM SDK 1.4.2

1 - Go to: [https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)
Download the JRE 1.4.2 for PPC. Registration Required. The one you want is the most recent version of "IBM SDK for 32-bit iSeries/pSeries" in tgz format. At the time of writing, you should get a file 'IBMJava2-SDK-142.ppc.tgz'. 

2 - Make sure 'fakeroot' and 'make-jpkg' are installed:
> apt-get install java-package fakeroot

3 - do the following:
> export DEB_BUILD_GNU_TYPE=powerpc-linux
> fakeroot make-jpkg IBMJava2-SDK-142.ppc.tgz
> sudo dpkg -i ibm-j2sdk1.4_1.4.2_powerpc.deb

4 - That's all folk :) 

No need to specify the PATH, everything is taken care of. You can also install packages depending on java, there is no need for the java-virtual-machine-dummy (this way to install Java is much better than creating a DEB package from a RPM one).

_______________________________
USING JAVA IN WEB BROWSERS

Well, as you probably already know, there is no way to use Java with Firefox or Mozilla (at least not with recent versions). But it can be done with Opera or Konqueror.

Here, I will simply explain how to set up Java for Opera, which can be downloaded from [www.opera.com](www.opera.com)

1 - Select Tools -> Preferences -> Advanced. Go in 'Content', check 'Enable Java' and click on 'Java options...'
2 - Here, select or enter the path to the JRE. It should be /usr/lib/j2sdk1.4-ibm/jre/bin if you followed this HOWTO. Validate.
3 - Just in case, close and restart Opera (should not be needed though) and try to load an applet. Just be aware that not 100% of the applets work in Opera...

**BE CAREFULL NOT TO ADD A TRAILING / AT THE END OF THE PATH!!!!!!**

This is probably the main point of this HOWTO, since I lost dozens of hours because of this simple mistake!
Opera will crash with the following error if you don't remove the trailing /:
```
Can't find class java.lang.NoClassDefFoundError. Invalid class path ?
JVMDG218: JVM is not fully initialized - will not do dump processing.
```

---

### Post by vibes on 2005-11-25
Cheers, works great for Breezy aswell :D

---

### Post by bcrowell on 2005-11-25
As lol requested, I've posted this info on the wiki at [https://wiki.ubuntu.com/forum/software/JavaApt#preview](https://wiki.ubuntu.com/forum/software/JavaApt#preview). Thanks, lol -- after a lot of frustration, I finally got applets to work based on your info!

---

### Post by Leif on 2005-11-25
Can you clarify in which way the wiki solution doesn't work ? I've used it in hoary and breezy successfully. If you're having problems with firefox 1.5, there's an easier solution : use the plf repos for the sun jre.

---

### Post by bcrowell on 2005-11-25
>Can you clarify in which way the wiki solution doesn't work ? I've used it in hoary and breezy successfully.
The library it tells you to make the symbolic link to doesn't exist -- the path is incorrect. Also...

>If you're having problems with firefox 1.5, there's an easier solution : use the plf repos for the sun jre.
Yes, I'm using firefox 1.5. What is a plf repos?

---

### Post by Leif on 2005-11-26
I've edited the wiki page and put in a method that works for firefox 1.5 for me. If it works for you too, please move the comments you put in from the wiki page to some other page, as they don't really belong there since they don't use repos to install.

---

### Post by robotgeek on 2005-11-26
[QUOTE=Leif]Can you clarify in which way the wiki solution doesn't work ? I've used it in hoary and breezy successfully. If you're having problems with firefox 1.5, there's an easier solution : use the plf repos for the sun jre.[/QUOTE]
The plf repositories don't have java for ppc. It must be downloaded from IBM's site and installed manually (for now). 

Anyways, the information in the wiki works perfectly for me (i am using the instructions for java 1.5).

---

### Post by bcrowell on 2005-11-26
The apt-get instructions still don't work for me. (I'm running firefox 1.5, and followed the directions recently added for firefox 1.5.)

What's plf?

---

### Post by Leif on 2005-11-26
[QUOTE=bcrowell]The apt-get instructions still don't work for me. (I'm running firefox 1.5, and followed the directions recently added for firefox 1.5.)

What's plf?[/QUOTE]

plf is a repo with proprietory stuff. which step doesn't work for you ?

---

### Post by bcrowell on 2005-11-26
OK, I figured out what was still going wrong. The command you gave for creating the symbolic link only works if you already have a plugins directory. I didn't, so instead of creating a link inside a plugins directory, it created a link called "plugins". I've added a note to the instructions concerning this possibility, and deleted the other instructions.

---

### Post by fourhead on 2005-11-27
Hi I'm trying to install a Java VM on Breezy on  PPC and an AMD64 machine. The only problem I have right now that apt-get won't find "java-package" which is needed for this make-jpkg command. I have all repos in the default sources.list enabled (main,universe,multiverse,backports). Where do I find this package? Is there a way to get some debs for java on ppc/amd64?

Tom

---

### Post by bcrowell on 2005-11-28
Have you tried the method given in the howto? --
[https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by Luxx on 2008-02-24
I'm very frustrated with this. I got the IBMJava2-SDK-1.4.2-9.0.ppc.tgz file from the IBM website, but I can't do anything with it, as below:

user@ubuntu:~$ fakeroot make-jpkg IBMJava2-SDK-1.4.2-9.0.ppc.tgz
Error: The file "IBMJava2-SDK-1.4.2-9.0.ppc.tgz" does not exist.

I have this problem every time I try to download something and then do anything with it from the terminal. Only apt-get and wget seem to work, but this isn't in a repository and IBM requires registration login to download. What am I supposed to do with it now? Why doesn't it exist as far
as my terminal is concerned and how do I get my terminal to find and recognize it?

Thanks.

---

### Post by stmiller on 2008-02-25
Luxx:

You are replying to a post that is soon to be 3 years old. :) 

Medibuntu has java for ppc. See the powerpcfaq at the top of the forum.

---

