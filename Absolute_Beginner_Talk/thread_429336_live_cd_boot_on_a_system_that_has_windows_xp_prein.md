---
title: "live cd boot on a system that has windows xp preinstalled"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by larry wales on 2007-05-01
hi all,

I'm very new to Ubuntu, and am so far very impressed with its presentation.  I've been following Geertjan's blog:  [http://blogs.sun.com/geertjan/](http://blogs.sun.com/geertjan/)  where he's just installed Ubuntu and has been raving about it.

Unfortunately for me though, installation has not been as easy as advertised:

I've got the downloaded installation onto a CD, but cannot seem to boot from the CD when restarting my computer.  I'm currently running Windows XP, and the OS immediately runs when booting the computer.  I've tried pressing all keys to enter BIOS before XP starts, but so far no response.  This must be a common issue for newbies, but I haven't seen any other posts on this forum.

Please help!

thanks in advance,
larry

---

### Post by laidback on 2007-05-01
There will be a key to press at POST (Power On System Check, first screen) that will take you into BIOS. On my system it's Delete (AMI bios), I have read that some systems use an F key, perhaps F1or F2 could be tried. Alternatively look in the manual of the motherboard. If you don't have this but know the make and id goto the manufacturers web site and have a search around for the manual. I've downloaded a manual for an ECS mobo that is around 6 years old so the chances are that you'll find it.
Once in the BIOS you'll need to change the order of bootup, making the CD first. 
Sometimes there is a another key available at POST that says something like Boot Choice, this is a useful option that allows you to change the device used to boot the machine this time only, it preserves the BIOS boot sequence. Very handy, on my machine it's F8 for this option.
The solution is there, keep looking.

---

### Post by breezyfox on 2007-05-01
hi
you need to find out how to enter in to bios setup. Normally it is DEL key or sometimes F2. Look at the manual for your motherboard.
Once you setup the bios to first boot device to  cdrom, evry thing goes smothly. After installing (booting) the live cd, you can choose to install to hard disk from desktop icon. After a few steps, which are very easy to understand, you can partition your disk and assign a space for system marked as / and a swap space.

all the best.

bz

---

### Post by Sef on 2007-05-01
The most common keys to go into the BIOS are Del, F2, F12, and Esc.   Just push the right key once your system first boots up, and then it will take you to the BIOS menu.  You might need to push the right key until I get into the BIOS.

---

### Post by Malta paul on 2007-05-01
Just a thought, Did you burn your disk as an image file? or just copy your downloaded ISO to your CD. It needs to be an image file to boot.
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) :)

---

### Post by larry wales on 2007-05-01
Yes, I burned the iso file to a cd, and am 99.9% certain the cd's good.

When I restart the computer, the XP splash screen displays almost *immediately*.  And I have tried all keys, especially Del, Space, and all the F's.  I cannot seem to get into BIOS, though.

I really appreciate all the responses I've got within the hour.  If anyone might have any more suggestions, I'd certainly be grateful.

-larry

---

### Post by darren1270 on 2007-05-01
What is the brand of computer?  Also model number??..... My laptop actually lets me choose the boot device without going into the bios.

Darren

---

### Post by larry wales on 2007-05-01
it's a Toshiba Satellite Pro M 30.  The model was actually discontinued a few years back.  I just found the following site:

[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

which, at the bottom, suggests holding down the pwr button with the Esc key.  I'm going to try that now...

---

### Post by darren1270 on 2007-05-01
I have a toshiba laptop and I can use I believe its either F10 or F12........ not sure cause laptop is at home but... if you restart it.... press one of them repetedly you may be able to choose the boot device there... hope this helps.

---

### Post by airtonix on 2007-05-01
nope to get into the bios on toshiba satellites/dynabooks the keys are the ESC, F1, F2 or the DEL key.

if you hold down f12 while booting it might let you choose the boot device, at least thats what happned on my dynabook

---

### Post by larry wales on 2007-05-01
yep.  It was F12 - a menu displayed allowing me to boot from the CD/DVD drive.

Wow, again thanks everyone for any input!  I'm going to get on with the installation process now.  This could be the beginning of a beautiful relationship... \\:D/

---

