---
title: "Initial username/password after install??"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2007-06-25
Hello. I have a newbie question... I am installing Feisty from scratch (first time from a CD). After Ubuntu is loaded, I get a login screen. It asks me for a username and password. What is the initial username and password that it expects?? I tried admin and root, but I keep getting an incorrect password message. This is strange behavior for an initial installation.

Thanks!

---

### Post by cogadh on 2007-06-25
It's looking for the user you set up during the install.

---

### Post by Phixion on 2007-06-25
During installation you should have been asked to enter your full name, then it gives you a username to use which you can change, default is usually your first name in lowercase, your password is also one you enter during installation.

---

### Post by Cold-Gin on 2007-06-25
Thanks for replying... It did not ask me for a username and password. From the initial installation menu, I chose "Start or Install Ubuntu". The next screen that appeared (After about 2 or 3 minutes) was the login screen. Should I have chosen a different installation option?

Thanks.

---

### Post by cogadh on 2007-06-25
Did you already complete the install and reboot? If so, you should have removed the install disk before the reboot, the installation is already complete and it is no longer needed. The only way the install should prompt for a password is if it is starting an existing installation and not trying to run the Live CD.

---

### Post by Phixion on 2007-06-25
It definately takes longer than 2 minutes to install Ubuntu... I suggest you go through the install process again :P

---

### Post by Cold-Gin on 2007-06-25
No, I didn't even get so far as to be able to install it on a second hard drive that I put in specifically for a Linux installation. I have only gotten to the point where Ubuntu is loaded into memory. Like I was saying the exact steps that I took were:

1.) Insert CD
2.) At initial Ubuntu installation flash screen I chose "Start or Install Ubuntu"
3.) After 2 minutes the login screen appears

Nowhere did it ask me to enter a name or an initial user.

Thanks again.

---

### Post by cogadh on 2007-06-25
Ah, the subject of your post says "Initial username/password **after** install??" I think that is where the confusion lies.

There may be a problem with the CD you are using. Have you tried downloading/burning a new copy? Also, which install CD are you using (Standard, 64 bit, alternate,, etc.)?

---

### Post by Cold-Gin on 2007-06-25
Thank you very much for your suggestions. Actually, I know this CD is OK, because I was able to install Linux on my machine at work from it. My problem is that I did the install like 3 months ago, and I don't remember exactly what installation steps I took :) Now, I am trying to install it at home.

This would be the 32 bit version. At work, I had originally started out with the 64 bit version by mistake, and I tossed that CD in the garbage. So I know that I have the 32 bit version in my possession... Let me try it one more time.

I'll post back my results.

Thanks.

---

### Post by cogadh on 2007-06-25
Okay, I just fired up my Standard install disk. The username is "ubuntu" and the password is blank. If your new attempt doesn't work, try that and let us know how it works.

---

### Post by Cold-Gin on 2007-06-25
OK, sorry it took so long to get back, but I have been working at this for a couple of hours. Still having trouble... Here's what has happened so far. Sorry if this is long winded, but I didn't want to leave out any details...

1.) I tried the installation again after my last post, and this time I did NOT get the login screen for some reason, but was able to get as far as the Ubuntu desktop with the "install" icon. I kick off the installation, giving user name, password, and pointing it at my second hard drive. Good so far - installation starts and I let it go while I make some coffee. I come back 15-20 minutes later and I see that it's at 78%. I am looking at the status bar (it was on "Loading Locales"), and all of a sudden it disappears. I wait for a few minutes to see if it does anything else, but no dice. (No "installation complete" notification or anything). Now, I try to bring up a terminal, but I get a message box that says "Permission denied". I try to bring up FireFox also, but same deal. I figure that I may have to do a chmod somewhere, but at that point, I figured rebooting may not be a bad idea. It starts shutting down, but the shut down does not end gracefully (I get a black screen with some messages).

2.) Now I try bringing up Ubuntu again after having to pull out the plug (it was frozen) :( and then rebooting, but I can't even boot from the drive that I installed it on, so that installation must not have completed normally. So now I start trying to reinstall from the CD again (multiple times), but I now I am back to my original problem. I can get to the login screen but no further. I try to use the user id and password that I created with the installation described in step 1, but that doesn't work. I try to use username "ubuntu" with blank password, but that doesn't work. I try to use ubuntu with password ubuntu, but that doesn't work either.

So my question is: Is there anyway to start with a clean install? Do I have to format the second drive somehow? I am also confused about this installation process. If I put the CD in the drive, and it loads everything into memory, I have two drives. Where is it looking for the credentials for a brand new installation? It really shouldn't be, right? Shouldn't it take the ubuntu username and blank password for a brand new installation and let me install again onto a different drive?

Sorry for the book, and thanks again for any suggestions or light that you can shed.

---

### Post by Phixion on 2007-06-25
I really can't see why you're having so many issues installing, just boot from the Feisty CD, click on install, follow the instructions.

During installation you have to enter a username/pass. Installation will also format and partition the drive you want to use. If you're still having issues I think theres an alternative CD you can use to install which is a text based version.

---

### Post by cogadh on 2007-06-25
Your new issues are bringing me back to one of my earlier questions; are you sure your install disk is OK? Considering the problems you are having, none of which should be happening at all, it's either a bad install disk or perhaps some type of severe hardware problem with the machine you are installing it on (which seems unlikely ATM). I *strongly* recommend you download a fresh copy of Ubuntu and burn a new disk.

To answer your questions, you do not need to do anything to the drive before an install, even if you have already installed (or tried to install) previously. The disk will be partitioned and formatted by the install wizard. The credentials it uses for the install are coded into the boot scripts on the install disk and the fact that you have already tried to install doesn't change that. However, it should *never* ask you to log in before the install, the login is completely automated.

---

### Post by abn91c on 2007-06-25
try user ubuntu password ubuntu

---

### Post by cogadh on 2007-06-25
He did, that didn't work. Besides, the install user "ubuntu" does not have a password (at least it didn't on my Feisty CD).

---

### Post by zero244 on 2007-06-25
Keep in mind after you set up the initial user and password dont take away Root Privelegs from the initial user or you will be screwed. You can create a new user with different privileges but make sure at least one user has root access or you will be locked out of your own machine.

---

### Post by chrisfromja on 2007-06-25
I am now experiencing a similar problem in that I was not prompted to enter a username and or password. I would like to try to re-install Ubuntu on the same partition but I am unable to delete the existing Ubuntu partition as I keep getting a prompt asking me to specify a root file system. The install was done on a Dell Inspiron with a working Windows XP partition that I am using to write this post. Any suggestions for a newbie?

---

### Post by chrisfromja on 2007-06-25
> **zero244 said:**
> Keep in mind after you set up the initial user and password dont take away Root Privelegs from the initial user or you will be screwed. You can create a new user with different privileges but make sure at least one user has root access or you will be locked out of your own machine.

If that does happen, how can you recover? Is it possible to boot using the recovery option and create a new user with root access?

---

### Post by chrisfromja on 2007-06-26
I got around this problem  by deleting the Ubuntu partition using a Windows XP CD to boot the machine. I then reinstalled Ubuntu using the CD and started the installation process again. I saw where I made the misatek in the first installation. I installed Ubuntu on a machine running XP and I told the install process to import my user profile from XP. In the next screen where it asked me for my information, I told the install process to use my XP user ID as the login ID. I suspect this is where I made the mistake. I know have it up and running fine with the exception of getting the wireless to work.

---

### Post by cogadh on 2007-06-26
That wasn't your mistake. I did the same thing and I have had absolutely no issues with Ubuntu at all. The only problem I had was the profile import only grabbed my wallpaper and user icon, it didn't get any of my files or favorites. Fortunately, both are very easy to grab after the fact.

---

### Post by chrisfromja on 2007-06-26
> **cogadh said:**
> That wasn't your mistake. I did the same thing and I have had absolutely no issues with Ubuntu at all. The only problem I had was the profile import only grabbed my wallpaper and user icon, it didn't get any of my files or favorites. Fortunately, both are very easy to grab after the fact.

Ok so my question is, when it prompts for your information after you answer the XP user profile import question, is that similar to configuring the local admin user on an XP machine?

---

### Post by Cold-Gin on 2007-06-26
I burned a new CD and tried the installation again. I still get the login screen after I choose the "Start or install Ubuntu" option from the flash screen, and none of the credentials discussed in the thread work on the login screen. I know that I shouldn't even get the login screen, but that is what's happening. It will never bypass the login screen so that I would get the install icon on the desktop...

Not sure what to do at this point. I tried multiple times to install with the new CD. On subsequent attempts (not on the first attempt with the new CD), I have been getting these errors before I get the login screen:

SQUASHFS error: Unable to read cache block.
SQUASHFS error: Unable to read page.

That can't be a good sign. Eventually I get multiple messages showing that different drivers are being loaded and such, and then eventually the login screen appears. That's as far as I can get.

Thanks.

---

### Post by cogadh on 2007-06-26
> **chrisfromja said:**
> Ok so my question is, when it prompts for your information after you answer the XP user profile import question, is that similar to configuring the local admin user on an XP machine?
No, it's similar to creating a 'limited' user on XP. Ubuntu doesn't really have admin users like you do on XP. 

If you create an administrator account on XP it is similar to creating a root account in Linux. The account has completely unrestricted access to the entire system and can make any changes it wants to, even if it is bad for the system. 
A limited user in XP can run programs, but generally can't install applications or make system-wide changes, unless you use XP's "run with different credentials" option. That is similar to an Ubuntu user using the "sudo" command to install applicartions, make system changes, etc.

> **Cold-Gin said:**
> I burned a new CD and tried the installation again. I still get the login screen after I choose the "Start or install Ubuntu" option from the flash screen, and none of the credentials discussed in the thread work on the login screen. I know that I shouldn't even get the login screen, but that is what's happening. It will never bypass the login screen so that I would get the install icon on the desktop...

Not sure what to do at this point. I tried multiple times to install with the new CD. On subsequent attempts (not on the first attempt with the new CD), I have been getting these errors before I get the login screen:

SQUASHFS error: Unable to read cache block.
SQUASHFS error: Unable to read page.

That can't be a good sign. Eventually I get multiple messages showing that different drivers are being loaded and such, and then eventually the login screen appears. That's as far as I can get.

Thanks.
I did a little Googling on those SQUASHFS errors, and they seem to point to problems with your CD-ROM drive. Is it possibly malfunctioning (i.e. have you had problems reading other CDs with it)?

---

### Post by Cold-Gin on 2007-06-27
cogadh - Thank you very much for being so helpful. I do not have an explanation, but today, after about the fifth attempt, I was finally able to install Ubuntu 7.04. In fact, I am posting this from the Ubuntu :).

I did not do anything differently then the past few days, although I did not receive the SQUASHFS errors today. The reason it took me 5 attempts was that, although I was now able to get to the install icon (without encountering the login screen), it took a couple of times before the partitioning seemed to kick in correctly with my secondary drive.

My only other concern at this point is that I watched the installation from start to finish. At 87%, the installation window said: "Configuring time zone", and once again the installation window simply disappeared and never came back. I don't like the fact that I never got a completion message, and I have yet to reboot (so I may be posting from Windows the next time ;)

Thanks again. Under that ignited skull of yours is a kind and patient person. :)

---

### Post by cogadh on 2007-06-27
Glad to hear it, though I don't know how much help I really was. Happy Ubuntu-ing!

---

