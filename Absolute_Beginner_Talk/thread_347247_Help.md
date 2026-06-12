---
title: "Help"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tenkabuto on 2007-01-27
I'm new to Linux so please bear with me. Okay, I am really impressed by the LiveCD, but the partitioning would not work. I did something, I'm not sure what, but all of a sudden the partitioning did work, but the original Windows partition displayed only 4.98 used MiB.

What did I do? =/

---

### Post by Imsati on 2007-01-27
First off, welcome to the Community!  Have you tried starting fresh and taking your time while going through the install. It may seem like a lot of effort, but read everything step 2 or even 3 times before clicking next and moving forward. It could be a problem with the LiveCD, but probably not. Sometimes the initial install takes a few tries (at least in my case) but after that, the OS runs like a dream.

Are you trying to install onto a HDD with Windows already on it or a separate HDD? Basic rule of installation/partitioning/gparting is ALWAYS BACK UP your data first! That way if something does go awry (which it does) you'll have all your personal files and whatnot. I'm heading to bed in a few minutes, but I'm certain others will help you out inf you still need aid.

---

### Post by tenkabuto on 2007-01-27
> **Imsati said:**
> First off, welcome to the Community!  Have you tried starting fresh and taking your time while going through the install. It may seem like a lot of effort, but read everything step 2 or even 3 times before clicking next and moving forward. It could be a problem with the LiveCD, but probably not. Sometimes the initial install takes a few tries (at least in my case) but after that, the OS runs like a dream.

Are you trying to install onto a HDD with Windows already on it or a separate HDD? Basic rule of installation/partitioning/gparting is ALWAYS BACK UP your data first! That way if something does go awry (which it does) you'll have all your personal files and whatnot. I'm heading to bed in a few minutes, but I'm certain others will help you out inf you still need aid.

Thank you, but my main problem at hand is the reinstalling of Windows, which I lost to an accidental formatting of the hard drive while trying to partition. I planned to run Windows along with Ubuntu.

---

### Post by tonyr1988 on 2007-01-27
Uh oh - that's no fun. This is a common gameplan:

-Install Windows first.
-Repartition: Shrink Windows, add a Linux partition (usually ext3), and maybe add a shared folder (for sharing files between Windows and Linux)
-Install Linux - make sure you don't have the "Format" box next to Windows checked.

How many hard drives do you have, and how big are they? How much do you plan on using either operating system (tons of programs, tons of files / songs / videos / etc?)? If you need, we can try and help you with a partitioning scheme.

---

### Post by nyinge on 2007-01-27
> **tenkabuto said:**
> Thank you, but my main problem at hand is the reinstalling of Windows, which I lost to an accidental formatting of the hard drive while trying to partition. I planned to run Windows along with Ubuntu.

I'd suggest installing Windows first.  GRUB boot manager in Ubuntu CD should take care of the dual booting process, when you install Ubuntu.  Yeah, like the previous poster said, take your time to read the instructions.

p.s.  Hope you're not installing them on a RAID system.

---

### Post by tenkabuto on 2007-01-27
> **tonyr1988 said:**
> Uh oh - that's no fun. This is a common gameplan:

-Install Windows first.
-Repartition: Shrink Windows, add a Linux partition (usually ext3), and maybe add a shared folder (for sharing files between Windows and Linux)
-Install Linux - make sure you don't have the "Format" box next to Windows checked.

How many hard drives do you have, and how big are they? How much do you plan on using either operating system (tons of programs, tons of files / songs / videos / etc?)? If you need, we can try and help you with a partitioning scheme.

Well I mostly use the computer for a few things:
Dreamweaver
Photoshop
FTP
Internet Radio / Music

Any schemes you have in mind?

---

### Post by tenkabuto on 2007-01-27
Also, how do I reinstall Windows? It wont let me boot from the Windows disk. :mad:

---

### Post by irish_flu on 2007-01-27
> **tenkabuto said:**
> Also, how do I reinstall Windows? It wont let me boot from the Windows disk. :mad:

Just to make sure we know what's goin' on:  You could boot to the Ubuntu Live CD, but you can't boot to the Windows CD?

---

### Post by tenkabuto on 2007-01-27
Nevermind, I got the Windows setup CD to work. I just need it to recognize my monitor resolution, setup an internet connection, and get my old files all in place.

What do I do with VMware to allow me to go from Windows to Linux?

---

### Post by tenkabuto on 2007-01-27
Okay, this is a very frustrating problem. In Ubuntu the resolution is fine, but in my fresh install of Windows it says that the resolution is 680x540 when it should be 1240x????. :mad: 

Anyone to help me with this shall be greatfully appreciated.

I also have problems with accessing to internet on the computer, but I'll save that after I fix the resolution problem.

---

### Post by irish_flu on 2007-01-27
> **tenkabuto said:**
> Okay, this is a very frustrating problem. In Ubuntu the resolution is fine, but in my fresh install of Windows it says that the resolution is 680x540 when it should be 1240x????. :mad: 

Anyone to help me with this shall be greatfully appreciated.

I also have problems with accessing to internet on the computer, but I'll save that after I fix the resolution problem.

You probably need to install the drivers for both the network card and the video card (hopefully provided on a disk sent with your computer) in order for Windows to recognize them.

If it were me, I'd install the network card driver first and get your internet connection working.  Then, I'd go to the website for whoever made your video card and download the drivers for it there (because they'll be newer than what's on the CD).  That's just my preference though, do it how you want.  :)

If there's one single disk with all the drivers on it, install the lot of them in Windows.  Especially if this happens to be a laptop, there might be all kinds of little funky hardware things that Windows isn't quite clear on.

---

### Post by tenkabuto on 2007-01-27
How do I figure out what drivers to get? And my internet should just work when it detects the internet is connected.

Right now I'm on Ubuntu posting this, when it works here and not on Windows.

---

### Post by irish_flu on 2007-01-28
> **tenkabuto said:**
> How do I figure out what drivers to get? And my internet should just work when it detects the internet is connected.

Right now I'm on Ubuntu posting this, when it works here and not on Windows.

Did your computer come with a disk containing drivers?  If not, we'll have to find them another way.

I agree that your internet "should just work", but not if Windows can't see your network card (possibly because you lack motherboard drivers for a built-in network device).

---

