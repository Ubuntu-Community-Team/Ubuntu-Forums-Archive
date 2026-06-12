---
title: "using the Kubuntu 7.04 Alternate CD to upgrade - but how!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by HiJolly on 2007-04-21
Ok, now I've mounted my CD drive and want to upgrade my brand new 6.10 Edgy to the new hotness 7.04 Feisty.  But my laptop has no internet connection, so the plan is to do it using the ALT CD.  But the thing is a WINDOWS program!  WHAT?  

How do I upgrade from CD ?  


HiJolly

---

### Post by mikewhatever on 2007-04-21
Quoted from [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD
   2.

      Insert it into your CD-ROM drive
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD
   4.

      Follow the on-screen instructions

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade" 

Note that for Kubuntu the upgrade dialogue will not be displayed and you will need to install gksu before running the above command (it will not work with kdesu). 

You can download and burn the CD using Windows on another PC. Try this link [http://www.ubuntu.com/GetUbuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate](http://www.ubuntu.com/GetUbuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate)

---

### Post by bobplano on 2007-04-21
no the alternate cd image should not be a "windows" program. it should come as an .iso like all the rest of the ways to get (k)ubuntu. then all you need to do is burn it as an image and upgrade. i'm not sure how to upgrade form a cd because i've used dapper for the whole time i've used ubuntu (not very long), but it shouldn't be too hard

---

### Post by HiJolly on 2007-04-21
> **mikewhatever said:**
> Quoted from [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Yeah, I read that.  But I have no clue what "Note that for Kubuntu the upgrade dialogue will not be displayed and you will need to install gksu before running the above command (it will not work with kdesu). " means.  

I mean, what do I do to install gksu?  I don't have the internet on this laptop, I mean that's why I'm upgrading using the ALT CD in the FIRST place.  So, can install it from CD, so then I can upgrade from the ALT CD?  What an interesting and convoluted process - and I'm just starting!!  

So, how?  


HiJolly

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> no the alternate cd image should not be a "windows" program. it should come as an .iso like all the rest of the ways to get (k)ubuntu. then all you need to do is burn it as an image and upgrade. i'm not sure how to upgrade form a cd because i've used dapper for the whole time i've used ubuntu (not very long), but it shouldn't be too hard

The start.exe says (in Konqueror) that it's a Windows Executable.  And I can vouch that after I burned it from .iso to CD on my XP machine, it started to go.  So, it is.  


HiJolly

---

### Post by bobplano on 2007-04-21
you can get packages from [packages.ubuntu.com]("packages.ubuntu.com") and then put them on a usb sitck or something and install them on your ubuntu system. i haven't checked but you can get most anything there so that should include gksu(do). then you can run that command and upgrade

---

### Post by HiJolly on 2007-04-21
> **mikewhatever said:**
> 
You can download and burn the CD using Windows on another PC. Try this link [http://www.ubuntu.com/GetUbuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate](http://www.ubuntu.com/GetUbuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate)

What?  I already have the ALT CD.  I just don't have gksu or know how to get it.  I'll try Bob's idea, but I know exactly nothing about installing packages...  


HiJolly

---

### Post by bobplano on 2007-04-21
> **HiJolly said:**
>  but I know exactly nothing about installing packages...  


HiJolly

installing packages is acutally easier than using synaptic or add/remove. you just click on it to open it and then click on install package. to get gksu search [packages.ubuntu.com]("packages.ubuntu.com") for gksu and it is the first choice

---

### Post by halitech on 2007-04-21
there is a file (not sure on the name, could be start.exe for all I know) that will, when placed in a windows computer, will autorun to show windows people what Ubuntu is all about.

I have no idea on upgrading from 6.10 to 7.04 by the cd but if you've just installed 6.10, do you have anything you need to keep on the drive now? if not, simply boot from the drive and do a fresh install

---

### Post by st33med on 2007-04-21
Well your BIOS might not be loading off the CD. When you boot up with the CD inside, there should be two button references at the top. Note them, and one should say 'Boot options' or something like that. Not setup. Now reboot again, and press that button REALLY quickly. Press it several times during boot.

Now a menu should state which thing you want to boot off of. Select CD.

There you go!

EDIT: Wait, do you have a dual-boot system?

---

### Post by HiJolly on 2007-04-21
> **st33med said:**
> Well your BIOS might not be loading off the CD. When you boot up with the CD inside, there should be two button references at the top. Note them, and one should say 'Boot options' or something like that. Not setup. Now reboot again, and press that button REALLY quickly. Press it several times during boot.

Now a menu should state which thing you want to boot off of. Select CD.

There you go!

EDIT: Wait, do you have a dual-boot system?

No, this is Kubuntu only.  No win at all.  

Ok, I did have to hit that button super fast, sure enough!!  but it's booting up now.  I guess I'm going for a fresh install?  Or not?  

** I decided not to do a fresh install (yet!).  see below

HiJolly

---

### Post by HiJolly on 2007-04-21
> **bobplano said:**
> installing packages is acutally easier than using synaptic or add/remove. you just click on it to open it and then click on install package. to get gksu search [packages.ubuntu.com]("packages.ubuntu.com") for gksu and it is the first choice

OK, I copied it (via thumbdrive) to the desktop and clicked on it - but there is no "install package" to click on.  It lists "Control.tar.gz", "data.tar.gz" and "debian-binary".  The valid Actions seem to be "add file" or "extract".  What should I do?  extract?  

Ok, I 'extracted'.  Now, how do I apply the package to Kubuntu?  Click on 'control.tar.gz'?  


HiJolly

---

### Post by HiJolly on 2007-04-21
Need help on how to install a gksu.deb package in kubuntu.  Please?  


HiJolly

---

### Post by benson444 on 2007-04-21
Just install it over the top of 6.10. If Feisty can't do whatever you needed Edgy to do then ask about it here. I'm sure somebody will help you.

You really need to get a Linux system on-line. Linux is designed, from the ground up, as a networked OS. If you can't connect you'll be stuck in a dependency netherworld where nothing much can be done (without major hassle) to improve your PC beyond the base install. If you can you'll be off and learning.

Why can't you get on-line with Edgy? If your wireless doesn't work then ethernet will.

---

### Post by HiJolly on 2007-04-21
> **benson444 said:**
> Just install it over the top of 6.10. If Feisty can't do whatever you needed Edgy to do then ask about it here. I'm sure somebody will help you.
Yes, I see what you mean.  And, for the first time, I understand what "dependency hell" is.  Ouch.  I will indeed install fresh with 7.04.  

> **benson444 said:**
> You really need to get a Linux system on-line. Linux is designed, from the ground up, as a networked OS. If you can't connect you'll be stuck in a dependency netherworld where nothing much can be done (without major hassle) to improve your PC beyond the base install. If you can you'll be off and learning.

Why can't you get on-line with Edgy? If your wireless doesn't work then ethernet will.

I could, but I know very little about DHCP routing, networking stuff I really am lost.  So I wanted to avoid it because of the learning curve.  Why get into the mess if I don't need to.  Well, I guess I need to.  Ugh.  


HiJolly

---

### Post by benson444 on 2007-04-21
> **HiJolly said:**
>  I could, but I know very little about DHCP routing, networking stuff I really am lost.  So I wanted to avoid it because of the learning curve.  Why get into the mess if I don't need to.  Well, I guess I need to.  Ugh.  


HiJolly

Well, I know very little about DHCP routing as well. :-) When I come across a specific problem I simply search for it (as I would in Windows) and do the best I can to sort it out. Post a new thread as to why you can't get online and maybe someone will be able to help with it.

---

### Post by mikewhatever on 2007-04-22
> **HiJolly said:**
> Need help on how to install a gksu.deb package in kubuntu.  Please?  


HiJolly

In case you are still at it, a *.deb file in Ubuntu is the same as *.exe in Windows. You can simply double click it, and, in case all the dependencies are satisfied, it should get installed. 
The start.exe installer you mentioned earlier is another way of installing Ubuntu from Windows environment. [http://ubuntuforums.org/showthread.php?t=338279](http://ubuntuforums.org/showthread.php?t=338279)

---

