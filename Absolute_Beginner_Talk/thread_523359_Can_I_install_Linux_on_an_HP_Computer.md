---
title: "Can I install Linux on an HP Computer?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2007-08-11
Good afternoon,

Some background information:

Computer - Hewlett Packard Pavilion a1610n
Operating System - Windows XP (hoping to dual boot with Ubuntu)

Recently, I spoke with an HP customer service representative inquiring about a Windows XP CD (I did not receive one with my computer). To make a long story short, I eventually asked about installing Ubuntu Linux on my computer, and the representative said that she didn't recommend installing Linux on my computer. She went on to say that HP does not support drivers for Linux. Thus I had a problem which still remains. I don't want to install Linux only for it not to work or become incompatible with my hardware down the road,  yet the customer service representative did not seem sure that it wouldn't work.

Has anyone had experience with installing Ubuntu on an HP computer? Did it run? Does anyone have advice for me?

Thanks,
- John

---

### Post by eapache on 2007-08-11
Ubuntu can be run from a CD, so you can see if it works without installing it or breaking your current install. Give it a try!

---

### Post by fickendichdu on 2007-08-11
With the growth of Linux the way it has you should not have many problems with your hardware.  Most devices are supported and work well.  You can now even connect digital cameras without having problems.  Go ahead and try it and see how it works for you.

---

### Post by anothrguitarist on 2007-08-11
Thanks for the quick replies... Will do!

---

### Post by jeremy1138 on 2007-08-11
> **anothrguitarist said:**
> Good afternoon,

Some background information:

Computer - Hewlett Packard Pavilion a1610n
Operating System - Windows XP (hoping to dual boot with Ubuntu)

Recently, I spoke with an HP customer service representative inquiring about a Windows XP CD (I did not receive one with my computer). To make a long story short, I eventually asked about installing Ubuntu Linux on my computer, and the representative said that she didn't recommend installing Linux on my computer. She went on to say that HP does not support drivers for Linux. Thus I had a problem which still remains. I don't want to install Linux only for it not to work or become incompatible with my hardware down the road,  yet the customer service representative did not seem sure that it wouldn't work.

Has anyone had experience with installing Ubuntu on an HP computer? Did it run? Does anyone have advice for me?

Thanks,
- John

I'm running a dual boot system with Ubuntu and Windows.  You will have to make a new partition for Ubuntu by resizing your Windows partition.  Everything works ok for the most part on my laptop but I'm having a lot of trouble getting anything 3d to work on this machine...  The problem is that I have an ATI video card and there are no good drivers for it out there.  You should be able to get everything working just fine especially if your computer is a desktop model with a video card other than ATI.  Oh and 64 bit machines can cause problems with plugins for Firefox(the internet browser).  Good luck!  Let us know how it turns out for you!

---

### Post by misfitpierce on 2007-08-11
Yup I use HP laptop works great. ACPI temp dosnt read but oh well.

---

### Post by crav on 2007-08-11
I'm pretty sure HP uses the Broadcom DevilChip(tm) [aka the 4318], at least i know my HP uses it. It can be a pain to set up in ndiswrapper, but it is possible

---

### Post by jeremy1138 on 2007-08-11
> **crav said:**
> I'm pretty sure HP uses the Broadcom DevilChip(tm) [aka the 4318], at least i know my HP uses it. It can be a pain to set up in ndiswrapper, but it is possible

Right I had some problems getting my wireless card to work but I got it.  I used my windows driver file and NDISWrapper and it's working great now!

---

### Post by gnuman on 2007-08-11
I have an hp pavilion laptop (dv6226us) and have never regretting going to Linux.  Although I was using Mepis for a long time, I have switched to Ubuntu for various reasons.

You will have to do some tweaking, but don't let that scare you [ever try installing Windows?].  You learn a LOT more about your computer when you tweak it.  Also, Ubuntu requires the least tweaking of any Linux distro I have tried.  About the only thing I had to really mess with was the screen resolution--which is pretty common.  I just did a search in this forum and found the solution (915resolution).  The rest were just minor fine tunings.

Am I the only one who get's irritated by service reps that brush off Linux just because they have no clue how to really answer your question?  Sheesh.

---

### Post by EXCiD3 on 2007-08-11
HP does not officially support Linux as they have gotten a deal with Microsoft to sell their products, not linux. Linux runs great on my HP laptop. The links in my signature will take you to some threads I have started about running Ubuntu on HP computers.

---

### Post by p_quarles on 2007-08-11
From googling, it looks like that model is a desktop, so you probably don't use wireless.

I have a slightly newer version of the Pavilion desktop, and I haven't had a single hardware problem with it. Go for it. The HP reps are going to tell you not to -- of course -- because they don't want to make any guarantees. The hardware they use, though, is very standard, and completely compatible with Linux.

You mentioned that you didn't get an XP CD with the computer. I've purchased two machines from HP recently, and both of them had a separate "Recovery" partition from which you could burn the installation disks. The application for burning these disks is located in the Start menu under something like "system tools." Be sure to look for this before you try to install Ubuntu.

And, of course, if you want to dual-boot, make sure you defrag the hard drive a couple times before you install.

---

### Post by fickendichdu on 2007-08-11
> **gnuman said:**
> I have an hp pavilion laptop (dv6226us) and have never regretting going to Linux.  Although I was using Mepis for a long time, I have switched to Ubuntu for various reasons.

You will have to do some tweaking, but don't let that scare you [ever try installing Windows?].  You learn a LOT more about your computer when you tweak it.  Also, Ubuntu requires the least tweaking of any Linux distro I have tried.  About the only thing I had to really mess with was the screen resolution--which is pretty common.  I just did a search in this forum and found the solution (915resolution).  The rest were just minor fine tunings.

Am I the only one who get's irritated by service reps that brush off Linux just because they have no clue how to really answer your question?  Sheesh.

If you need to fix your resolution to get greater like he said you cna search the forums like I have just solved it a half hour ago with help from here.  Here is the console command so you do not need to search again.

```
sudo apt-get install 915resolution
```

---

### Post by Frak on 2007-08-11
I use an HP, and it works great. By support, they probably in case something doesn't work, they won't support it, but I have yet to come across an HP that won't run Linux. (They are huge supporters BTW, every single printer they make works with Linux.)

---

### Post by p_quarles on 2007-08-11
> Am I the only one who get's irritated by service reps that brush off Linux just because they have no clue how to really answer your question? Sheesh.
Preaching to the choir, here. :) You're not the only one.

I called my ISP for some help with configuring my modem once, and after I made the mistake of telling them which OS I was using, I spent nearly half the call trying to explain to them that networking protocols are not OS-dependent (nevermind the fact that the modem itself is running on embedded Linux). 

Steam was literally shooting out of both ears by the end of that call.

---

### Post by anothrguitarist on 2007-08-11
Well I booted from a CD and things are going well. As mentioned by another poster, the resolution isn't quite right, but that shouldn't be a problem.

One of you mentioned that I should defrag my hard drive before installing. Are you implying that I do not have to reformat my hard drive before installing :) ?  In other words am I able to install Ubuntu without wiping away windows?

Thanks for the overwhelming assistance,
-- John

---

### Post by fickendichdu on 2007-08-11
Yes you are able to install without wiping out windows.  You will just want to repartition your drive so you have available space to install on.

---

### Post by p_quarles on 2007-08-11
> **anothrguitarist said:**
> Well I booted from a CD and things are going well. As mentioned by another poster, the resolution isn't quite right, but that shouldn't be a problem.

One of you mentioned that I should defrag my hard drive before installing. Are you implying that I do not have to reformat my hard drive before installing :) ?  In other words am I able to install Ubuntu without wiping away windows?

Thanks for the overwhelming assistance,
-- John

No, you absolutely don't need to wipe the drive to install Ubuntu or any other Linux distro. When you start the installation, it will ask you a few questions about your name, your keyboard, and your location. After that, it will take you to the partition editor, which allows you make a new partitition for Ubuntu. 

Once it's done installing, you'll get a new boot manager which asks you which OS you want to load. It's pretty great.

When you get to the partitioning stage, though, be sure to select "Resize existing volume and use newly freed space" (or something like that). Don't select "use entire volume" unless you want to get rid of Windows entirely. I mention this just because some new users have stumbled over this step.

---

### Post by anothrguitarist on 2007-08-11
Another question:

Do I/ should I create multiple partitions for Ubuntu in order for it to run correctly?

---

### Post by p_quarles on 2007-08-11
> **anothrguitarist said:**
> Another question:

Do I/ should I create multiple partitions for Ubuntu in order for it to run correctly?

Some people like to create a separate partition for their /home directory, which allows them to reinstall without losing their settings/files. Since this is your first installation, though, I would recommend you just go with the default settings. It's much easier, and Ubuntu will automatically create the partitions it needs to function properly.

---

### Post by anothrguitarist on 2007-08-11
> **p_quarles said:**
> Some people like to create a separate partition for their /home directory, which allows them to reinstall without losing their settings/files. Since this is your first installation, though, I would recommend you just go with the default settings. It's much easier, and Ubuntu will automatically create the partitions it needs to function properly.

Awesome, Thank you.

---

### Post by anothrguitarist on 2007-08-11
In regards to setting a better resolution:

When I run sudo apt-get install 915resolution, it cannot find the package. any help would be appreciated :)

---

### Post by bwtranch on 2007-08-11
Hey look folks. (and by the way hi,fx) For those of you that don't know Fx  and I have been on some projects lately and you can trust him. 

For the matter of "support" what do they really mean? You are getting support right here? I didn't see you signing an agreement to pay us:(

Look, the machine was made by only a handful of companies. Mostly Intel or AMD. It's either a ix86 or a x86_64 processor. There isn't anything else! Linux is the user form of Unix that was developed by the government by Bell Labs to run something for the military that would later be called the internet. OK are you with me so far? Bill Gates and some other 2nd rate programmers got together in a garage and knowing that they couldn't just outright steal the Unix system and just wrote some bad hacks. That became DOS. A really brilliant programmer got involved by the name of Steve Jobs and told them how to write something called a graphical user interface. They used what he told them and sent him packing and he tried to sue and lost. Steve started a company called Apple and was later booted. Bill had a company called Microsoft and even though it was cited for infringment of copyright and being a monopoly.

Steve Jobs came out ok and started a company called Pixar and finally made his money. Now, if you don't see where I'm coming from, look at the avatar.

Any questions? :)

---

### Post by p_quarles on 2007-08-11
915resolution will only work if you have an Intel graphics card. For NVidia, ATI or Matrox, there are other solutions.

If you do have an Intel card, you can do the following to enable the correct repositories:
1) Hit alt-F1 to open the command line
2) type```
gksudo gedit /etc/apt/sources.list
```
3) Remove the "#" symbol in front of any lines starting with "deb"
4) Back to the command line: ```
sudo apt-get update
sudo apt-get install 915resolution
```

---

### Post by anothrguitarist on 2007-08-11
I should have mentioned, I do have an NVidia graphics card: GeForce 6150LE. I should also mention that I haven't installed linux yet because I cannot see the forward button (on the install window) because it is off screen. I cannot resize the window either.

EDIT:  Found a work-around. Used control tab a couple of times to navigate to the forward button.

---

### Post by p_quarles on 2007-08-12
>  EDIT:  Found a work-around. Used control tab a couple of times to navigate to the forward button.
Good work. NVidia has Linux drivers for their hardware, so once you get Linux installed you'll be able to get the graphics working.

---

### Post by Frak on 2007-08-12
```
sudo dpkg-reconfigure xserver-xorg
```
It'll give you a screen where you can change everything to your liking :)
Most you can leave default, but when it gets to your resolution, choose the correct one.

Hope that helps:)

---

