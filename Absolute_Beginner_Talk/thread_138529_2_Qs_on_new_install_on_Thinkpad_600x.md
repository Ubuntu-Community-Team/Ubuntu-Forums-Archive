---
title: "2 Qs on new install on Thinkpad 600x"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by NorthIL on 2006-03-02
Hello, I'm new to Ubuntu but a somewhat old hand in linux. I install 5.10 Ubuntu from the official CD distros.

First, After installing onto 2nd partition ( I created 2 new partitons; 2 gig ext3 and 500meg swap; on an extended partition using partitionMagic in XP ) on a 600x w/256meg. The install went ok, but now when it boots, it seems that after the initial login screen it takes an unholy amount of time before the Gnome interface appears. Also, it is VERY VERY sluggish, compared to XP Pro which is installed on the primary partition. I tried the LiveCD version from the net, and it ran very quick. Why so sluggish?:cry: 

I searched the forums and found that the culprit may be the 'noapci' parameter, but after I added that to the Grub command line...no change. Also, I have never upgraded the BIOS firmware on this Thinkpad. Could that cause the problem? For reasons I can't get into here, I can't upgrade the BIOS firmware.

Second, I noticed the Gnome is the default GUI with Ubuntu. I'd much rather use KDE. After searching the forums for an answer, I saw people refering to a Kubuntu release. Is this a different distro? I could have sworn during the install that I saw the KDE librarys and packages being installed. Any easy way to switch from Gnome to Kde? 

Thanks.

---

### Post by NorthIL on 2006-03-02
Well, i see there is a Kubuntu distro, so that's answers one of my own questions. I tried the LIVE cd again, and it flys perfectly. Don't understand why the installed version is so slow...:cry:

---

### Post by terencelhl on 2006-05-01
Hi there,

I am having the same problem with you and am searching for solutions now. :(

---

### Post by waffen on 2006-05-12
Hello,

Edit de grub (/boot/grub/menu.lst) adding this line:

pci=noacpi acpi=off apm=on

Good luck!

---

### Post by waffen on 2006-06-02
[QUOTE=waffen]Hello,

Edit de grub (/boot/grub/menu.lst) adding this line:

pci=noacpi acpi=off apm=on

Good luck![/QUOTE]

Hello!

This problem is fixed in Ubuntu Dapper version!! :-D

---

### Post by lreyes6 on 2006-10-23
i have edgy installed on my 600X and works perfect

---

### Post by Stew2 on 2006-10-23
> **lreyes6 said:**
> i have edgy installed on my 600X and works perfect

Sorry for hijacking the thread :). Did you have to upgrade the bios to install edgy? I bought this 600X off of ebay a year ago and have been scared to upgrade the bios in case it has an admistrator password set in the bios that I don't know about.:confused: 

Regards,
Stew2

---

### Post by NetworkGuy on 2006-10-23
If you can access the BIOS without needing a password then you should be OK to upgrade the BIOS if needed.   

To access the BIOS on a thinkpad:  hold down the F1 key and turn the thinkpad on.  Release the F1 key when the unit beeps.

---

### Post by lreyes6 on 2006-10-23
nope i didn't upgrade the bios... btw don't know wich version i have right now and don't  know either wich version is the latest jeje... can u tell me?

---

### Post by Stew2 on 2006-10-23
Thanks for the replies! :D  I will have to give it another shot one of these days. I think the latest bios version for the 600X is version 1.11 (ITET55WW). And yes I can get into the bios without a password so that must mean that there is no bios password... excellent:D .
I will stop hijacking the thread now. Thanks again for the tips!

Regards,
Stew2

---

### Post by AFMComputing on 2007-05-29
Hello everyone,

I have a LOT of thinkpad 600s, 600es, and a working 600x.  I am trying to install 6.10 on the 600x but I am having trouble getting past Step 2, (localle, timezone)  It seems that ubuntu won't accept the FORWARD button.  I can go back, manipulate other programs, etc.  I assume that I'm just not doing something to satisfy the installer...

Is there a magic order to this, or do you need to have a working network connection to get through it (that rings a bell re the ALTERNATE CD)...  i'M on the 600x right now, so the network issue (wireless, in fact) has been set up.

Thanks for any input you might have...

Oh one thing I've learned with some of Live CD Distros is that to run an old thinkpad it sometimes takes   pnpbios=off at the beginning of the first run.  I don't know what that does to the resulting installation... whether it sets up ACPI or an APM installation.

Thanks, 

Mike
[email]AFMcomputing@verizon.net[/email]
EarthFriendlyPCs.Com

---

### Post by lreyes6 on 2007-05-29
try the alternate cd... that worked for me... and try Xubuntu... Gnome and KDE seems to be so heavy for this laptop 

regards

---

