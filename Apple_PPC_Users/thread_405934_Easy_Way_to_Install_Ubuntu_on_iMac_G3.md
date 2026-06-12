---
title: "Easy Way to Install Ubuntu on iMac G3"
date: 2007-04-10
forum: Apple PPC Users
---

### Post by ZoiaGuyver on 2007-04-10
Ok ive seen so many people lately have these problem's i thought id make a post as a little walkthrough of the install for Ubuntu and Varients on the iMac G3's.

Ok to go into a little detail of the problems we face first. The first problem people will definatly notice is the lack of a DE/GUI on boot, this isnt a major issue, its nothing to be scared of its just the way X.org trys to communicate with you screen thats slightly off.

The second problem that can turn up is whats kindly reffered too as the "date bug", basically OF (Open Firmware, Apples version of a bios) stores all its data with the help of a pram battery, a lot of people would refer to it as a kind of bios battery. This bug can and will break the install of Ubuntu in many cases causing very weird things to happen. 

Ill try and take it step by step so hopefully we can have a successfull install of Ubuntu first time.

Lets start by making sure our Date and Time are correct.

As the iMac boot's hold down these keys

**cmd + option + p + r ** (Thanks for noticing my silly mistake fkdev :D)

If this is successfull you should hear another start up chime. This means the OF has been reset to defaults and should also make OF update the time and date from the network.

Next to the meat of the project getting us a working install of Ubuntu. Now here we have two choices depending on a persons prefference. One takes us through a GUI install of Ubuntu the other will leave us a basic Command Line.

**GUI Install**

This is probably the most simple of the installs, the Ubuntu devs seem to have worked long and hard on making the GUI install as nice as possible, for this install we would require the "Ubuntu Live CD" or one of its Varients (Kubuntu/Xubuntu).

Right first we need to set our iMac up, so once youve got the CD booted you will be greeted by a blankscreen rather than the desktop you had been waiting on. So first lets fix this by using a terminal and writing these command's to get us a working X.org and GUI.

Hit these keys to take you to a terminal.

**[color=red]ctrl-option-F1**[/color]

at prompt type

**[color=red]sudo nano /etc/X11/xorg.conf**[/color]

Look in the file for the "Modules" Section in there you should have one that says

Load "dri"

change that to 

#Load "dri"

Then look towards the bottom of the file for

HorizSync 

and

VertRefresh

change the values of these to

HorizSync 58-62 

VertRefresh 75-117

Then do ctrl + o then enter

Then do ctrl + x

Then type

**[color=red]sudo killall -HUP gdm[/color]**

If all has gone well you will now be greeted with the desktop you first expected. Now you can install using the installer link on the desktop and begin your wonderfull adventure into Ubuntu and Linux. Once the install is finished and you've rebooted into your new Ubuntu system i would recommend two more commands before you rush off to play :D

**[color=red]sudo apt-get update**[/color]

**[color=red]sudo apt-get upgrade**[/color]

This will make sure you have the latest security and package updates.

**CLI Install**

This install is a little more hands on as it were but still leaves us with a working system that is  command line only though so we are left to customise things, for this install we would require the "Ubuntu Alternate Install CD". 

At the "boot" prompt press the "tab" key to display a list of possible installs the one we are interested in for this install is the "cli-powerpc", so at the boot prompt we type:

**[color=red]cli-powerpc**[/color]

Now this install uses a debian type of graphic install and will walk you through the rest of the install with various choices given to you, my only suggestion here would be to read the options and select them from there.

After this has been completed the Mac should ask you to reboot and eject the CD. On reboot we will be left with a Command Line. Now the task is to log in using the name and password you used for the install, at this point you should be at the prompt.

Now we want to make sure we have all the latest packages.

**[color=red]sudo apt-get update**[/color]

**[color=red]sudo apt-get upgrade**[/color]

At this point you may notice the kernel has been upgraded and there are packages being held back. So our next step would be to restart the machine. Type "reboot" at the prompt and once restarted login again. Now we deal with the held back packages type

**[color=red]sudo apt-get dist-upgrade**[/color]

Now this will grab us a later kernel and install that for us. Reboot the machine again and login so we can start to get us a GUI.

Now my choice of DE/GUI whatever people want to call it is Enlightenment E17, this is a very much in development Desktop Shell (as they like to call it), but in my eyes its def one of the best for use on the iMac. I wont walk people through how to install that as its not a default UI and needs the sources.list file edited. Instead i will tell you how to install X.org and one of the Ubuntu desktops instead.

At the prompt we need to type in a few commands to make sure we get the packages we need. The first and main pakage would be X.org the Xserver we will be using.

**[color=red]sudo apt-get installl xorg xserver-xorg-dev**[/color] 

**[color=red]startx**[/color]

After this you should notice that X looks a little weird so we need to sort that before proceeding. This is the time to edit xorg.conf, first we need to kill X by using

**[color=red]ctrl + alt + backspace**[/color]

Then we type

**[color=red]sudo nano /etc/X11/xorg.conf**[/color]

The first thing we do in the file is to disable the DRI as explained above.Then on most of the iMacs you will notice that the driver for the graphics card is "fbdev" change this to "ati". Also be sure to adjust the refresh rates to those above.

Now some will ask why we need the X.org dev most wont need it but you may find when installing from source (which you probably will be doing on PPC) its needed sometimes.

Second we need to decide and get our DE. Typing these commands will get them for us.

**Choose One of these**

**[color=red]sudo apt-get install ubuntu-desktop**[/color] **Gnome** 

**[color=red]sudo apt-get install kubuntu-desktop**[/color]  **KDE**

**[color=red]sudo apt-get install xubuntu-desktop**[/color] **XFCE**

Once this is done you can reboot the Mac for one last time and should see a wonderfull login manager greet you on startup.

I hope this helps someone out.

Tbh its basically all the stuff ive found while trying out different bits. There is also a way to enable "dri" on the iMacs but maybe ill go into that if ppl want me too :D

---

### Post by solar george on 2007-04-10
> One takes us through a GUI install of Ubuntu the other will leave us a basic Command Line.

You can also use an alternate install CD, it uses a text menu to install but sets up the GUI for you.

---

### Post by anurse on 2007-04-10
Many thanks. For people like me who have been mainly Mac users, this type of step by step instructions is really needed. Again, thanks.

---

### Post by ZoiaGuyver on 2007-04-11
Yes i know we can do that from the alternate. 

The reason i gave cli instructions are for those like me that dont want it installed for first boot but rather have it after all the updates have been done. 

Sorry for not making that clearer maybe i should have said it was my preferred install method and explained it a little better sorry.

---

### Post by Orange.exe on 2007-04-11
I just got a lime imac dv w/ os 8.6, and plan to install edgy w/ the live cd.

First, would there be any problems letting it format the drive w/ os 8.6 on it?

Also, would it be possible to install beryl or compiz on this mac?

---

### Post by ZoiaGuyver on 2007-04-12
If you dont want 8.6 anymore then its fine to format the complete drive. Imo Ubuntu would make a very good replacement for you. 

The answer to the beryl/compiz question im afraid is no, the graphics cards in the imac (ATI Rage based) arnt supported, you can get AIGLX to go on them but tbh the performance is terrible.

XGL is a total no go as the Rage isnt even supported and there are issues with locking.

---

### Post by fkdev on 2007-04-15
Correction:
```
 ctrl-option-p-r 
```
should be:
```
 cmd-option-p-r 
```
However, one should note that, at least I think,
If people have changed the insides of their computers (like replacing drives)
then this may make Mac OS 9 require a re-install of drivers
for the partition via the recovery or install cd's disk utility

---

### Post by didg on 2007-04-20
About X resolution and iMac, does Feisty liveCD work ok now? (It should).

---

### Post by ZoiaGuyver on 2007-04-26
First off FKDev is correct it is cmd-option-p-r i do apologise i wrote this up quick and muddled the keys :S

Secondly ive been testing fiesty and tbh it seems to be a problem within the Xorg not actually within Ubuntu. I dont really know if this is sorted within the finals (havnt had chance to update to that yet as im waiting for some memory for my G3), it wasnt corrected in the last of the beta's before going to release though

---

### Post by BigG123 on 2007-04-26
Ok.

---

### Post by sciawonrose on 2007-05-02
Hello Thanks for the help on installing on the imac g3.

I did install ubuntu but did not manage to have it shutdown properly because it keeps restarting all the time until I umplug it. I though it might be a problem of ubuntu, so I installed xubuntu with the same results. I have an imac g3 400mhz with 128ram the slot cd type. 

one more question I used to watch dvd with it on mac os9 but now with xubuntu even if I have installed (at least I believe to have) all the multimedia stuff, it plays but it is very slow with sounds unsincronized....

Any help will be welcome.

---

### Post by SectionThree on 2007-05-03
I wouldn't unplug the thing if I were you, it'll just cause a boatload of problems in the future. Use the reset button instead. It's located next to the ethernet port and it's marked with a little black triangle. Sometimes there's a button, sometimes a hole. If you have a hole, poke it with a paper-clip you bent out for that purpose.

As for playing DVDs, most of them are encoded with a proprietory codec that's unavailable in the "free" repository. Go into Synaptic and make sure ALL the repositories are switched on, then do your search.

This is about as far as I can help on this particular matter because I've never tried to play a DVD on Ubuntu, but I hope that I have at least pointed you in the right direction.

---

### Post by CrystalBaller09 on 2007-05-14
> **ZoiaGuyver said:**
> 

Tbh its basically all the stuff ive found while trying out different bits. There is also a way to enable "dri" on the iMacs but maybe ill go into that if ppl want me too :D

Could you please?

Edit: nevermind, I found a thread about it. Except it doesn't work.

---

### Post by VorDesigns on 2007-05-16
Thank you much for this.
I was looking for a cli editor and remembered my problems with iMac Black Screen at login and trying to figure out what to do.

---

### Post by marksman7328 on 2007-06-12
I am having a problem installing Ubuntu following your instructions.

I d/l Ubuntu Dapper Drake for PPC (Live CD)
I burned it to a CD
I reset the clock on my Apple G3.
I booted from the live cd.
Fancy ubuntu logo comes up. It says Loading essential drivers... etc., until it comes to Adding live CD user... and then it freezes and screen goes blank.
I did ctrl-option-F1 to get a terminal.
I still had a blank screen.
I typed sudo nano /etc/X11/xorg.conf anyway.
Nothing happened.



I am a complete Ubuntu/Linux noob seeking help.

---

### Post by GaiusJuliusCaesar on 2007-07-25
Hi.  Many thanks for the changes to the xorg.conf file to get *ubuntu on a number of old imacs I'm giving away.  You mentioned of a way to enable dri and that you would post it if there was interest.  Could you?  Thanks again, Julius

---

### Post by Lurcher on 2007-07-30
Thank you for the assist.  Recently I burned a copy of Feisty Fawn and attempted to install it on my G3.  It has gone very well, but when accessing Terminal (in an attempt to install Feisty on a partition on my G3; OS X 10.2 is on the other) it doesn't allow me to do any changes.  By this I mean that after 'command + option + F1' to access Terminal I can't do anything else because Terminal does not accept my commands.

And while I don't recall the exact wording, I pretty much run against a wall with 'sudo nano /etc/X11/xorg.conf.

I will give it another try tomorrow.

And I have to thank you again because, while I have run against a 'bump in the road', so to speak, I have come farther with your assist that I have prior dealling with the earlier version of ubuntu (6.06).

---

### Post by Midwest-Linux on 2007-07-31
> **marksman7328 said:**
> I am having a problem installing Ubuntu following your instructions.

I d/l Ubuntu Dapper Drake for PPC (Live CD)
I burned it to a CD
I reset the clock on my Apple G3.
I booted from the live cd.
Fancy ubuntu logo comes up. It says Loading essential drivers... etc., until it comes to Adding live CD user... and then it freezes and screen goes blank.
I did ctrl-option-F1 to get a terminal.
I still had a blank screen.
I typed sudo nano /etc/X11/xorg.conf anyway.
Nothing happened.



I am a complete Ubuntu/Linux noob seeking help.

Try the alternate CD installer for Dapper Drake PPC, some suggest using the lowest burn speed when burning the ISO  disc. If this works and the Live CD didn't, maybe you need more RAM or have to reburn the live CD at a lower speed. 

The alternate CD installed is basically a text based menu for installation, it will ask you some questions as the installation goes on. the longest part of the installation will be when it says "Select and Install Hardware" If it looks like it is hanging up...it isn't ....some parts ...especially at 6 % seem to hang when in fact its doing the install. Expect about a hour or longer. But stay with it , as it asks questions before you can go further. Also make sure the G3 is plugged into the internet.

 If you are having issues with the video output before or after this check to see if you have two video outputs instead of just one output. if you have two video outputs ( I did!), use the top one. Let us know the outcome.

---

### Post by cheezle on 2007-09-26
First of all, I'm new here so...  Hi everyone! :KS

I'm pretty much a linux noob, so sorry for all the questions.

I'm planning on putting Xubuntu on my iMac g3 ( 400 mhz 192 mb ram and a 9.51 gb hard drive).  ***I'm wondering if this whole proscess will work with the alternate install cd.***  I don't want to use the "live/install" cd because that requires the exact ammount of ram my iMac has, and I want the install to go as fast as possible.

Thanks in advance!

---

### Post by cheezle on 2007-09-27
> **cheezle said:**
> First of all, I'm new here so...  Hi everyone! :KS

I'm pretty much a linux noob, so sorry for all the questions.

I'm planning on putting Xubuntu on my iMac g3 ( 400 mhz 192 mb ram and a 9.51 gb hard drive).  ***I'm wondering if this whole proscess will work with the alternate install cd.***  I don't want to use the "live/install" cd because that requires the exact ammount of ram my iMac has, and I want the install to go as fast as possible.

Thanks in advance!

Sorry for the double post, but I think I solved my problem.

I just read wrong.  It said it required 128 MB or RAM rather than the 192 I thought it needed.

---

### Post by docinsano on 2007-10-01
I'm attempting to install ubuntu feisty on an imac g3 400 mhz w/ 512 ram. I downloaded the iso from the links in the sticky. the disk boots up fine and the desktop works but either there is no installer or i just dont know how to install it on my mac. Any ideas? Thanks in advance.

---

### Post by Midwest-Linux on 2007-10-02
> **docinsano said:**
> I'm attempting to install ubuntu feisty on an imac g3 400 mhz w/ 512 ram. I downloaded the iso from the links in the sticky. the disk boots up fine and the desktop works but either there is no installer or i just dont know how to install it on my mac. Any ideas? Thanks in advance.

Use the alternate text installer CD, it installs Ubuntu with no problem.

---

### Post by mangurt on 2007-10-18
Ok, I am completely lost here.  Hopefully someone will be kind enough to point me in the "right" direction.

I will explain my situation first.  I have a ibook g3/900.  Things were working fine on it last year,  I was trying to install something on the laptop and it locked up, and basically is stuck between OS's now (I get the blinking folder when I turn the computer on).  I can not for the life of me find the recovery disk and was hoping I could install ubuntu on this lap top.  I downloaded both versions of feisty fawn (i386 and the alternate i386), and burned both of them to separate cd's.  When I start the computer up though, I still get the blinking folder?  Is this a loss for me?  Is there something I need to do differently?
Thank you for the help in advance.

---

### Post by zjokke on 2007-10-21
You should not use i386 installs. These are meant for PCs and Intel Macs. You have a PowerPC Mac (or PPC). You'll have to download the PPC images. More info at [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ).

---

### Post by ungars on 2007-10-22
Hello from France.

If you download this two ISO cd images, you can control if the MD5 sum is ok using this script in Python (yes, Python is available under MAC OS 9.x...) :

[ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso](ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso)
[ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/xubuntu-6.10-desktop-powerpc.iso](ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/xubuntu-6.10-desktop-powerpc.iso)

[FONT="Courier New"]
#! /usr/bin/env python
# -*- coding: latin_1 -*-

import md5
print "Compute the MD5 sums of xubuntu610DesktopPowerpc.iso..."
m1 = md5.new()
m1.update("Macintosh HD:Download:xubuntu610DesktopPowerpc.iso")
d = m1.hexdigest()
print "MD5 sums of xubuntu610DesktopPowerpc.iso  : ", d
print "Compute the MD5 sums of xubuntu610AlternatePowerpc.iso..."
m2 = md5.new()
m2.update("Macintosh HD:Download:xubuntu610AlternatePowerpc.iso")
d = m2.hexdigest()
print "MD5 sums of xubuntu610AlternatePowerpc.iso  : ", d
[/FONT]

As you can see, this script is very simple. The names of the ISO cd images is less longer than the real names,
because under MAC OS 9.x we are limited to 31 characters for a file's name.
This cdroms don't boot at all, and the MD5 of this web site are not the same as computed by the python script, after I have downloaded the two ISO :

[ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/MD5SUMS](ftp://ftp.free.fr/mirrors/ftp.xubuntu.com/releases/6.10/release/MD5SUMS)

eefea0c37b7b9a59e8e34f3a87d80d5e  xubuntu-6.10-alternate-powerpc.iso
91eeb4820708f34bc4a738a9464d451a  xubuntu-6.10-desktop-powerpc.iso

I have downloaded them with Fetch 3.03 in binary mode under MAC OS 9.1, I have burned the "desktop" CD using another iMAC G5 under MAC OS X, by the Finder. My iMAC G3/350Mhz/320 Mo/ don't boot on the cdrom, with the "C" key of the keyboard pressed...It boot under MAC OS 9.1 only. The MD5 sums is not the same at the ftp site.
Any suggestions to resolve this strange problem ?

---

### Post by oswaldkelso on 2007-10-22
> **ungars said:**
> Hello from France.

I have downloaded them with Fetch 3.03 in binary mode under MAC OS 9.1, I have burned the "desktop" CD using another iMAC G5 under MAC OS X, by the Finder. My iMAC G3/350Mhz/320 Mo/ don't boot on the cdrom, with the "C" key of the keyboard pressed...It boot under MAC OS 9.1 only. The MD5 sums is not the same at the ftp site.
Any suggestions to resolve this strange problem ?

If I understand you correctly the iso has been renamed and is less than the 31 characters. As for the check sum I'm not sure.  I have had check sums fail and the cd work fine as there is a lot of data on the cd you may never use but it's always best to eliminate the burn first. 
It's a while since I ran os9 but in osx you can also select the boot options by holding down the alt key on boot if the “c” key fails. This will show you all boot options, for e.g. osx, osx2, os9, linux1, linux2, cd, etc. If available to you.

Imac crt cd drives are noted for being poor But check your firmware also if you have never run anything other than os9

Other options are use your osx disk for your G5 (if its ppc)  put osx on your G3 then install ubuntu

Try a  debian net install or business card install first then install ubuntu.  Here are links about the firmware  
[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)
A  business card install how to is on my site should you choose to do that. Hope it helps

---

### Post by ungars on 2007-10-22
In fact, I think that the CD has been made with the following error : when I read it under any systems, I see the big file, this with the ISO extent, not the various directories it should contains !...I will try to find the right way to burn correctly this CD.The MD5 script is not good : I think it compute the MD5 of the string in argument, not the MD5 of the ISO file ! I will try to correct this later.

---

### Post by TimHeckman on 2007-12-21
Alrighty...I'm kind of misinformed on the specs of the iMac I have.  It's an old one, most likely a G3.


I think I had a problem with my Alternate CD burn, so I'll have to retry that one.  But the Live CD of Gutsy Gibbon seems to have this problem.

I did the Command + Option + P + R...rebooted the computer.   I got the chime, held down the C-key to boot ubuntu.  

I get the screen with the ubuntu logo asking what I want to do.   I select to install, I get  the "Loading, Please Wait..." message.  And the Mac literally shuts down.  The power button in the front turns off, and the screen is black.

I cannot notice any sounds coming from the computer hinting that the HDD is spinning, or the CD-Rom Drive.  I'm going to retry again today...anyone have any ideas?  Could Gutsy Gibbon be the issue?

The alternate CD doesn't even try to book when I hold down the C key.

---

### Post by pi3832 on 2007-12-21
> **TimHeckman said:**
> I get the screen with the ubuntu logo asking what I want to do.   I select to install, I get  the "Loading, Please Wait..." message.  And the Mac literally shuts down.  The power button in the front turns off, and the screen is black.

I cannot notice any sounds coming from the computer hinting that the HDD is spinning, or the CD-Rom Drive.  I'm going to retry again today...anyone have any ideas?  Could Gutsy Gibbon be the issue?

The alternate CD doesn't even try to book when I hold down the C key.

You might try loading an older version from a Live CD, and follow the directions at the start of this thread for modifying the [FONT="Fixedsys"]xorg.conf[/FONT] file and such.

That would eliminate Gutsy as being the problem.

Also, be sure to check the MD5 on the [FONT="Fixedsys"].iso[/FONT] files before burning them to CDs, and when you burn them use a lower burn rate, such as 8x.  I've had trouble both with corrupted files and bad burns.  (Using cheap CDs probably didn't help any.)

---

### Post by Lupin the 3rd on 2008-01-07
I bring up the terminal and type sudo nano /ect/x11/xorg.conf and nothing comes up. There is no Moduals to look in. If it helps at all the cd says its okay and the desktop is all messup as in not in the right area.

---

### Post by bengki on 2008-01-08
Hi..Anybody know where to download bussiness card cd image for ppc?

---

### Post by solar george on 2008-01-08
> /ect/x11/xorg.conf 

/etc not /ect, easy mistake to make though.

> Hi..Anybody know where to download bussiness card cd image for ppc?

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

---

### Post by Lupin the 3rd on 2008-01-09
I got the file to open, (Thanks) but there is no HorizSync or VertRefresh. I've combed over it and didn't find anything. I performed a search and still nothing. Help?

---

### Post by ocean223 on 2008-01-27
I have an ibook 8oo mhz, 640 mb ram.  I can't get ctrl-option-f1 to bring me to the command prompt.
Any ideas?  
Thanks in advance.

---

### Post by stream303 on 2008-01-27
> **ocean223 said:**
> I have an ibook 8oo mhz, 640 mb ram.  I can't get ctrl-option-f1 to bring me to the command prompt.

With Gutsy on my G4 iBook, I also lost virtual terminals.  I had to edit /etc/yaboot.conf and remove

append="quiet nosplash video=ofonly"

With that line removed (make a backup of the original!), I ran
```
sudo ybin -v
```
and rebooted.

No splash screen, but now my virtual terminals are back.

---

### Post by Cows on 2008-03-20
You can leave quiet but you have to remove "splash video=ofonly", The video will definitely mess with the Virtual Terminals and the Splash is mest up so no point of having that there. Leave quiet though so it can be more organized. It get's really annoying watching all those lines going down. If anything just use "dmesg" after boot.

---

### Post by luke.is.very.handsome on 2008-04-06
So i did the livecd install, ran through the little part of the walkthrough just fine, the kubuntu logo pops back up with a blue bar across the bottom, and the output eventually states in white in the middle of the screen that says "Restarting system log...                      failed".  The failed is in blue.  It does this over and over if I let it sit and try to figure itself out.

This is a blue imac g3 with a 400mhz processor and 1gb of ram.  The disc I burned for this passes the checks and verifications.  It has the latest firmware and was running OS X tiger just fine, but I don't really like the apple os anyway.  I'm a fan of using broken stuff instead of fischer price.

---

### Post by stream303 on 2008-04-06
It sounds like the live-cd worked for install, but I'd try it with the "alternate" install image instead just to be sure.

I don't know which version of Ubuntu you are installing, but definitely see this tip for video frequencies and such that you might have to edit in a rescue-mode:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

1gb ram is great for a G3!

---

### Post by nitrous9200 on 2008-05-27
If you have a VGA port on your G3, plugging in an external LCD will allow you to complete the setup normally.

---

### Post by versemelk on 2008-06-12
i have the oldest G3 imac there is (tray loader, blue-ish green-ish)with boosted memory and i'm trying to install ubuntu 6.0.6 (dapper drake)


the live-cd boots a black screen with white letters, i press tab to see the structure but the file mentioned by OP is nowhere to be found, and every other thing i try ends with me having a white screen telling me the following:

"Can't allocate initial device-tree chunk

and info on apple's OF.

at this point, nothing works, what am i to do to solve this?

---

### Post by linear on 2008-06-13
> **versemelk said:**
> i press tab to see the structure but the file mentioned by OP is nowhere to be found

Do you mean "**[COLOR=red]cli-powerpc[/COLOR]**[COLOR=red][COLOR=Black]"? That's the alternate install CD, not the live CD. You may have better success using the alternate install CD. How much total memory do you have?[/COLOR][/COLOR]

---

### Post by versemelk on 2008-06-13
> **linear said:**
> Do you mean "**[COLOR=red]cli-powerpc[/COLOR]**[COLOR=red][COLOR=Black]"? That's the alternate install CD, not the live CD. You may have better success using the alternate install CD. How much total memory do you have?[/COLOR][/COLOR]

yes! that's the file i meant! i've tried both install types, the alternate didn't show that option either...


i have a total of 256MB of memory installed. i tried both the live and alternate cd so far but the problem occurs with either one of them. so far i've done everything by the book, burned the disks at low speed using diskutility but still i get that same white screen with everything i try.

has anyone else encountered this?

help is very much welcome!:confused:

---

### Post by stream303 on 2008-06-14
Hi versemelk, welcome aboard!

You might be interested in seeing this thread in the *current* Apple forum:

[http://ubuntuforums.org/showthread.php?t=820397](http://ubuntuforums.org/showthread.php?t=820397)

While the archived threads here are outstanding, they are setup as "reply-only" after a recent forum reorganization.  Just wanted to mention that, so you won't miss anything. :)

---

### Post by versemelk on 2008-06-14
thanks!

i'll ask around those forums a bit :)

---

### Post by Nimlot on 2008-06-17
I tried a CLI install with Hardy on a slot-loading G3. The installation went smoothly, and I managed to get X working. Unfortunately, as soon as I installed xubuntu-desktop I started having a problem similar to the one TimHeckman was having:
> **TimHeckman said:**
> 
I get  the "Loading, Please Wait..." message.  And the Mac literally shuts down.  The power button in the front turns off, and the screen is black.

I've verified the install disk and got the same result when I tried a complete reinstall. I can get into the system using the install disk as a rescue disk, and have tried removing xubuntu-desktop:
```

apt-get remove xubuntu-desktop
apt-get autoremove

```
However, that hasn't fixed anything. Any help is appreciated.

---

### Post by stream303 on 2008-06-17
If you want to get back to a "pure" environment, I have found this to be invaluable (no matter which DE you wish to remove).  I had to use the copy-n-paste method in a terminal. :)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Be sure to select the right desktop, and also the right version, (Hardy, Gutsy, Feisty, etc)

Worked well for me.

---

### Post by Nimlot on 2008-06-17
No luck with that. Followed the removal for Xubuntu Hardy, but the system still shuts down abruptly after displaying "Loading, please wait..."

---

### Post by clayton911 on 2008-06-25
iMac G3 333Mhz OS 9

When I hit "cmd + option + p + r" the chime sounds and then it boots into OS 9.  Holding the c key down boots from the disk and I hit enter to boot into Ubuntu and hit the ctrl-option-F1 and it gives me a flashing cursor but when I enter the "sudo.." nothing happens the cursor just goes to the next line.  Please help.  Thanks.

---

