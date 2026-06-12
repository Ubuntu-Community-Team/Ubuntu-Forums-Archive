---
title: "Installing Java..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by sim085 on 2006-07-13
Hello,

I am trying to install Java (J2SE) on my pc.  I have downloaded the required package from Sun website (jsk-1_5_0_07-linux-i586.bin).

Now I have read several posts on this forum on how I can install this bin package.  I have also tried checking some websites as well.  However I am still failing to install the Java Development Kit.

I am trying to install the jdk on the Xubuntu live cd using the following commands.

sudo aptitude update
sudo aptitude install jsk-1_5_0_07-linux-i586.bin

When I run these commands I am in the desktop folder, since this is the place where I have the *.bin file.

ubuntu@ubuntu:~/Desktop$

I do not know what to do else.  I have also tried to use the Synaptic Package Manager, however it seems that it does not handle the *.bin file.

I would apreciate any comments about this :)

Regards,
Sim085

---

### Post by T700 on 2006-07-13
> **sim085 said:**
> 
I am trying to install the jdk on the Xubuntu live cd using the following commands.


This is the Live CD?  I'm not sure you can install Java if you're using the Live CD; I've never heard of anyone trying.  I just assumed you would have to do an install to your hard drive before you could add Java.  I could be wrong, so perhaps someone will correct me.

Paul

---

### Post by sim085 on 2006-07-13
I am using the live CD because I am at work.  When i go home I will make a full installation.

Do you know what i would need to do to install Java on my Xubuntu if I have a full installtion?

regards,
Sim085

---

### Post by T700 on 2006-07-13
The commands you're trying should work just fine.  You can also use Automatix (see my sig) to install Java and quite a few other things such as codecs.  

Paul

---

### Post by sim085 on 2006-07-13
I do not know if it is because of using the live CD.  However do I have to change something in order to be allowed to change the file:///etc/apt/sources.list??

At the moment I do not have permisions to change this file.  If this is because I am using the live CD, then I will stop trying to install Java now, and I will try again from home :)

Regards,
Sim085

---

### Post by garylai on 2006-08-13
Try this link:
[http://www.ubuntuforums.org/showthread.php?t=202537&highlight=bin+install](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=bin+install)

---

