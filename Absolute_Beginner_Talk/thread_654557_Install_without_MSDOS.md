---
title: "Install without MSDOS"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by captaindc on 2007-12-31
Whilst I have read all the ways to install UBUNTU - it seema to me it's like many distros of Linux - it needs MSDOS ie a MIcrosoft Disk Operating System to be installed - and to be there to support if your linux screws up.

I'm using Linspire version 5 at this time - I would like to to use KUBUNTU 6 but that needs MSDOS to install. I have tried to install KUBUNTU 6 Alternative CD but this fails to install KDE - I have no idea why. 

I have a USB CD - no internal CD and no BIOS Support for a USB CD. Yet with grub installed I can copy my Linspire 5 CD to my Hard disk and install off that CD.

It's the only way I can recover after installing the kubuntu 6 alternative cd installation which leaves me at the command prompt - I may as well go back to MSDOS ver 3.

Anyway 20 years on there ought to be a way of installing KUBUNTU without MSDOS.  It's amazing that there is no iso to replace an existing Linux. The aim seems to be to convert from MSDOS very worthwhile.  

Think then of GRUB how can I get KUBUNTU 6 Desktop to install with KDE I don't mind using the alternative cd or the desktop cd - as long as I get KDE desktop installed.

Practical solutions welcome - excluding getting an internal cd or taking the hard disk out and sticking it in another laptop or installing msdos.

There is no option to stick the CD and boot up an MSDOS machine and then do a network install onto a linux box or laptop. Why just focus on replacing MSDOS?

Happy New Year 

Regards,

David

---

### Post by anthonie on 2007-12-31
You can easily make a GRUB floppy and use that. Search around a bit. AFAIK there is no such thing as MS Dos being used in conjunction with *NIX flavors.

---

### Post by Menthol on 2007-12-31
MS DOS isnt used at all, I've never seen anything to do with MS DOS on ubuntu.  Linux is based on Unix which was about long before MS DOS.  
MS Dos would require a MS file system and linux uses EXT.

---

### Post by Tux.Ice on 2007-12-31
i think he may be talking about the terminal???

---

### Post by captaindc on 2007-12-31
> **Menthol said:**
> MS DOS isnt used at all, I've never seen anything to do with MS DOS on ubuntu.  Linux is based on Unix which was about long before MS DOS.  
MS Dos would require a MS file system and linux uses EXT.

So when you installed UBUNTU are you saying that you did not replace an existing MSDOS? ie VISTA or XP or Pro 2000 or WIN98? Hmmm the  KUBUNTU ISO's need MSDOS OS to install  - or did you not notice what version of MSDOS you had? 

Or did you buy a machine with UBUNTU preloaded?

Regards,

David

---

### Post by anthonie on 2007-12-31
> **captaindc said:**
> So when you installed UBUNTU are you saying that you did not replace an existing MSDOS? ie VISTA or XP or Pro 2000 or WIN98? Hmmm the  KUBUNTU ISO's need MSDOS OS to install  - or did you not notice what version of MSDOS you had? 

Or did you buy a machine with UBUNTU preloaded?

Regards,

David
Ever since XP there has been no real version of MSDos connected to these Win installs.  What is this MSDos focus? Are you not simply talking about a command line surrounding or so?

I think most of us just install from a bootable CD.

---

### Post by forestpixie on 2007-12-31
when I installed the last time I installed to a completely empty hard drive -

---

### Post by Cypher on 2007-12-31
Linux doesn't require MSDOS or any Microsoft OS to perform the installation. In the past, Linux has come with installers that were launched from MSDOS or Windows, mainly because of the limitation of method of booting from CD's and USB devices.

If you were to grab the latest Ubuntu/Kubuntu/Xubuntu LiveCD and burn that to a CD, pop it in and tell the PC/Laptop to boot from the CD, you will find that it will boot into Linux without caring about what else might be installed on that PC.

Now, your issue is that you only have access to a UBS CD-ROM and no way of telling your laptop to boot to a CD on there, so you will need a bootfloppy that will allow you to begin the installation. To that end, please check out this helpful page om [SmartBootManager]("https://help.ubuntu.com/community/SmartBootManagerHowto").

---

### Post by Menthol on 2007-12-31
I use the bootable CD to install, the bootable CD doesnt have anything MS related on it.  It boots to the grub menu and you install ubuntu from there. 

Are you sure you're not getting Linux itself confused with MS DOS? The command line stuff is Linux, the "windows like GUI" is just an add on to Linux in a way

---

### Post by Tux.Ice on 2007-12-31
MSDOS - a command line environment used on a personal computer prior to a graphical environment, 

MICROSOFT DISK OPERATIONG SYSTEM - is only found on WINDOWS computers.

 In Windows Xp and up, msdos is not found anymore but, they do have a tool for powerusers: command prompt.

If you are a windows user/ linux noob you might think the linux terminal is "MSDOS". It is not. yes they do look alike, i know.

if you are going to use linux better get used to the terminal as it is where most of linux operations happen.

most of the people on this forum (i know i did) installed from a bootable live iso disk.

if you are just burning the iso to a cd, this will not work.

you must create a cd from the iso.  if you are using windows google - **iso recorder ** to get a good one.
in linux get **k3b** by going to add/remove

hope this helps :)

tux.ice

---

### Post by captaindc on 2007-12-31
> **anthonie said:**
> You can easily make a GRUB floppy and use that. Search around a bit. AFAIK there is no such thing as MS Dos being used in conjunction with *NIX flavors.

GRUB's good with hardware that slots in to the motherboard - when you have a problem like mine with a usb-cd there's no support in the bios on my laptop (an IBM A21E) it means you have to load an os that will then look for hardware - grub can't do that - I've tried.

The reason why I can install off the Linspire 5 CD is that there's a time lag and the fact that I have copied all the files to the hard disk - these load then look for hardware find the cd and then continue th install from there. I just edit the grub menu.lst file to point to the hard disk files. 

Let's say my Linspire screws up and all I can do is sit at a prompt. The good news is I don't care - I just create a recovery folder copy all the files from the CD and edit the menu.lst and use the command configfile (hd0,0)/recover/boot/grub/menu.lst and in 20 mins I have a full Linspire 5 up and running. 

Now I can do exactly the same with the Alternative cd KUBUNTU 6 but it does not install the KDE Environment. The idea of the alternative cd is if you have less memory and then you have a text based install menu rather than a heavy graphical user interface. I can install KUBUNTU 6 but it will not install KDE. Why I don't know as the CD checks out ok.

I cant use bootloader +1 because I need to have an o/s up and running that can find the usb-cd as grub can not.

Trust me I have been installing the alternative CD 6 and 7 with the same results and have had no success in getting the KUBUNTU 6 or 7 Desktop CD to run - it needs MSDOS installed ie it is to have a version of MSDOS running which can then replace. As  say you need MSDOS to install UBUNTU Desktop - unless of course you buy preloaded.

Regards,

David

---

### Post by anthonie on 2007-12-31
```
Sudo apt-get install life
```
I tried your advise. It told me I did not meet dependancies. Tried sudo apt-get install real-life and it told me to sod off... What a world, ubuntu...

---

### Post by Tux.Ice on 2007-12-31
nice.... (i hope you actually didnt try this :)

---

### Post by anthonie on 2007-12-31
> **captaindc said:**
> 
Now I can do exactly the same with the Alternative cd KUBUNTU 6 but it does not install the KDE Environment. The idea of the alternative cd is if you have less memory and then you have a text based install menu rather than a heavy graphical user interface. I can install KUBUNTU 6 but it will not install KDE. Why I don't know as the CD checks out ok.

I installed my Ubuntu from an alternate CD. Afterwards you can just sudo apt-get install kubuntu-desktop, or better sudo aptitude install kubuntu-desktop (as the last one is easy to remove with autoremove).

> I cant use bootloader +1 because I need to have an o/s up and running that can find the usb-cd as grub can not.
 
I dont know as I have never used the GRUB floppy myself. I know there's a site out there called bootdisk.com. You should be able to find something of your liking there, I suppose.

@TuxICe No I did not try it, I smiled at it, which turned out to be so much better!

---

### Post by Tux.Ice on 2007-12-31
david if u can get into terminal type this to install kde

```
sudo apt-get install kubuntu-desktop
```

this will install all the kubuntu gui stuff

---

### Post by forestpixie on 2007-12-31
> **Tux.Ice said:**
> nice.... (i hope you actually didnt try this :)

what - you mean it won't work :(

---

### Post by captaindc on 2007-12-31
> **Tux.Ice said:**
> david if u can get into terminal type this to install kde

```
sudo apt-get install kubuntu-desktop
```

this will install all the kubuntu gui stuff

Ah I knew that at some point a sane and simple answer would come. You thought a bit. I appreciate that.

So, I install via the alternative kubuntu 6 - easy - I can then pick the recovery mode option that drops me to root>. At that point how do I start a terminal session and also do I have to point to the location of the files?

Regards,

David

---

### Post by anthonie on 2007-12-31
> So, I install via the alternative kubuntu 6 - easy - I can then pick the recovery mode option that drops me to root>. At that point how do I start a terminal session and also do I have to point to the location of the files?

See my earlier post, three above here I think. Best is to use aptitude. You don't need to reboot in recovery mode as long as you use sudo you will have root rights. Terminal can be found in Applications/Accessories menu.

---

### Post by captaindc on 2007-12-31
> **anthonie said:**
> See my earlier post, three above here I think. Best is to use aptitude. You don't need to reboot in recovery mode as long as you use sudo you will have root rights. Terminal can be found in Applications/Accessories menu.

I shall cd around as I don't have a gui and find the command - or can I just at root> issue a command?

Regards,

David

---

### Post by markyb86 on 2007-12-31
you have pxe in your laptop. set up another computer with the iso of kubuntu and boot from your nic card


and for any commands in the terminal needing root priviledges, type sudo before the command

---

### Post by anthonie on 2007-12-31
No, you use sudo and than issue the command.
But were you not saying that you'd want to install the alternate cd first? I am not sure I 100% correctly understand what you want to do. It is not the case that without a proper Ubuntu install (be it from a Live or alternate CD) you can use apt-get install kubuntu-desktop. (At least, to my knowledge you can not do that.) So install the alternate CD first, and once you have a working desktop you can just start a terminal from there.

---

### Post by anthonie on 2007-12-31
BTW Linux floppies can be found here. You do actually have a floppy drive, right?

[http://www.bootdisk.com/linux.htm](http://www.bootdisk.com/linux.htm)

---

### Post by captaindc on 2007-12-31
> **anthonie said:**
> No, you use sudo and than issue the command.
But were you not saying that you'd want to install the alternate cd first? I am not sure I 100% correctly understand what you want to do. It is not the case that without a proper Ubuntu install (be it from a Live or alternate CD) you can use apt-get install kubuntu-desktop. (At least, to my knowledge you can not do that.) So install the alternate CD first, and once you have a working desktop you can just start a terminal from there.

Ok,

When I install from the alternative cd either version 6 or 7 of KUBUNTU I have no gui. If I do not press the escape key and let grub run as a user I am stuck at a user prompt. If I choose recovery mode I am at the root> user.

No gui gets installed and no kde desktop. I have done an install 5 times with KUBUNTU 6 alternative CD - the result is the same each time - no gui - no menu system just a prompt.

So all I have to do is at the root> prompt is to type sudo apt-get aptitude kubuntu-desktop - and low and behold it will be installed?

Regards,

David

---

### Post by markyb86 on 2007-12-31
your pc is very recent, dont install the alternate cd if you are able to boot up and actually start installing it. boot from the live cd

---

### Post by anthonie on 2007-12-31
But do you mean that as a normal user, you CAN get to the desktop? If so, do it from there. If not, it sounds like you did not install the alternate correctly. BTW, what ubuntu6 are you talking about? There are two distributions from 2006, as well as from 2007. I used the Feisty Alternate (7.06)

The alternate installs a normal gnome desktop and the only difference that I have seen is that it does not work as a live CD but instead has a txt based installer.

> **markyb86 said:**
> your pc is very recent, dont install the alternate cd if you are able to boot up and actually start installing it. boot from the live cd

He can't boot from his USB-CD rom drive.

---

### Post by forestpixie on 2007-12-31
are you sure you haven't got a server install disc - anyway that aside

once you've installed as you have already done and got to the prompt and assuming you have a working net connection

```
sudo aptitude install kubuntu-desktop
```

would install the desktop version

once that's done you can  reboot, with the command 
```
reboot
``` - at least I think you can

Edit - sorry didn't read properly, I see you've been given that option - so if you have tried running that command from the cli - does it not install or do you get an error

---

### Post by zetetic on 2007-12-31
> **captaindc said:**
> Whilst I have read all the ways to install UBUNTU - it seema to me it's like many distros of Linux - it needs MSDOS ie a MIcrosoft Disk Operating System to be installed - and to be there to support if your linux screws up.

I'm using Linspire version 5 at this time - I would like to to use KUBUNTU 6 but that needs MSDOS to install. I have tried to install KUBUNTU 6 Alternative CD but this fails to install KDE - I have no idea why. 

I have a USB CD - no internal CD and no BIOS Support for a USB CD. Yet with grub installed I can copy my Linspire 5 CD to my Hard disk and install off that CD.

It's the only way I can recover after installing the kubuntu 6 alternative cd installation which leaves me at the command prompt - I may as well go back to MSDOS ver 3.

Anyway 20 years on there ought to be a way of installing KUBUNTU without MSDOS.  It's amazing that there is no iso to replace an existing Linux. The aim seems to be to convert from MSDOS very worthwhile.  

Think then of GRUB how can I get KUBUNTU 6 Desktop to install with KDE I don't mind using the alternative cd or the desktop cd - as long as I get KDE desktop installed.

Practical solutions welcome - excluding getting an internal cd or taking the hard disk out and sticking it in another laptop or installing msdos.

There is no option to stick the CD and boot up an MSDOS machine and then do a network install onto a linux box or laptop. Why just focus on replacing MSDOS?

Happy New Year 

Regards,

David

Is this a stupid joke or what??
I've never read such a ridiculous post in all my life.

---

### Post by meindian523 on 2007-12-31
+1

---

