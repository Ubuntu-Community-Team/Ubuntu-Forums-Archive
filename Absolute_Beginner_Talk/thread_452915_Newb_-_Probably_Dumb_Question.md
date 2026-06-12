---
title: "Newb - Probably Dumb Question"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by rancid98 on 2007-05-23
Tonight, I am installing a second HDD in my PC and plan to install Ubuntu Studio 7.04 on it.  I am leaving Windoxs XP on the existing drive for the family to use.  I have searched the net and found instructions on how to have a dual boot up so the user can choose which OS to boot to at start up - not sure if it was at this forum as I can't find it again.  It all appears pretty straight forward.  The instructions say there is a program called Grub which will allow allow the set up for the choice of OS at startup.  Just a few questions:
[LIST=1]
[*]I have saved the various commands I have to cut and past in a Word document on the first hard drive in Windows.  I did this because I am fearful that I may not be able to access the internet whilst setting up.  I have now started to think I may not be able to access this Word document to cut and paste from when trying to set up the dual boot.  Will I be able to do that?
[*]This Grub program - does it come standard with the installation of Ubuntu Studio 7.04, or will I have to install it?  As I said, I fear that I may not be able to access the internet unless, of course, I boot to Windows.
[*]My fear with internet access is that I will install Ubuntu, and it may not have the necessary drivers for the cable modem or I may not be able to set up the settings for the modem etc. 
[/LIST]
I guess like most Windows users, the change is very scary and I am very afraid - I expect that something will go wrong at the most inopportune time when I do not have internet access to ask for help, and I will be putting it all back together in the current configuration so I can access the internet, then I will be sweating on an answer to get it all done.  I thought if I could predict problems, or at least satisfy myself that they won't happen, I might be a little more at ease.

Thanks, and my apologies if the questions are a little moronic.

---

### Post by nonewmsgs on 2007-05-23
ubuntu will take care of you, do not worry. grub is standard and automated.  it will see windows and automatically set everything up.  it is part of the installation process but while it installs you will already be using it!  it is a livecd so you can "try before you buy" (well not buy but you get the idea).  you can see how everything works and even go online without installing and then once you click install now. you can still use it.  you can play solitare while it whizzes along.

---

### Post by nonewmsgs on 2007-05-23
the only part that might be weird is if you have one sata and one pata drive.

---

### Post by Iokua on 2007-05-23
I don't have any experience with Ubuntu Studio, but I've installed Ubuntu about twenty times and it's always picked up on my internet settings immediately. I've never been without internet access (using cable modem with router). 

Maybe I'm just not familiar with Ubuntu Studio, but what commands do you need to cut and paste? I checked the Ubuntu Studio website and I only saw a few terminal commands about how to access their repositories. You won't need this to install Ubuntu, only to update Ubuntu Studio specific packages. If you're installing with a LiveCD, the whole process is graphical and it walks you through it. And yes, GRUB comes standard with most Linux distributions.

---

### Post by perce on 2007-05-23
> **rancid98 said:**
> 
I have saved the various commands I have to cut and past in a Word document on the first hard drive in Windows.  I did this because I am fearful that I may not be able to access the internet whilst setting up.  I have now started to think I may not be able to access this Word document to cut and paste from when trying to set up the dual boot.  Will I be able to do that?


If you install with the live CD, which is the preferred option, but doesn't work on all systems, you will be able to access your doc files by double clicking on them, just like in Windows. If you install using the alternate CD you won't. Saving in doc format was probably not a very good idea: if they were text files you could read them with the alternate CD too. The best option however is to print those instructions, or to copy them on paper.

> 
[*]This Grub program - does it come standard with the installation of Ubuntu Studio 7.04, or will I have to install it?  As I said, I fear that I may not be able to access the internet unless, of course, I boot to Windows.


Grub will be installed by default: it's not something you'll need for the dual boot; it's the standard Linux loader. The dual boot will be configured automatically by Grub.

> 
My fear with internet access is that I will install Ubuntu, and it may not have the necessary drivers for the cable modem or I may not be able to set up the settings for the modem etc. 


If you use the live CD and have a DSL ethernet modem you can set up the connection before starting the instalation (search the forum for instructions). If you have a DSL modem and use the alternate CD you'll probably have internet only at the very end. If you have a DSL USB modem, or a winmodem, there are high chances that you'll never have internet with Linux

> 
I expect that something will go wrong at the most inopportune time when I do not have internet access to ask for help


Of course it will happen. Isn't it the same with Windows? failures in critical moments are a hardware feature ;)

If you don't know the difference between the live CD and he alternate CD, the live CD is a complete Linux system that you can boot from cdrom instead of from the hard disk, and which comes with a graphical installer. It's a little slow, of course, but it is surprisingly usable. The alternate CD is a CD which loads only a minimal system with a text mode installer.

---

### Post by konungursvia on 2007-05-23
Just make sure in installing ubuntu 7.04 that you choose to put its root/ on the new external drive, not the one with xp. Actually, you can do it there too, but you have to be careful not to tell it "yes, delete the windows partition".

---

### Post by rancid98 on 2007-05-23
Thanks guys.  I found the thread - it was from this place - [http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

Cheers

---

