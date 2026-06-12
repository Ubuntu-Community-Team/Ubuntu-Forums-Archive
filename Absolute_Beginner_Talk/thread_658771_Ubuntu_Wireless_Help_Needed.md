---
title: "Ubuntu Wireless Help Needed"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by dconstruct on 2008-01-05
Hi,

I'm very new to Ubuntu and I love it.  I'm using an HP 530 laptop and I'm just trying to get my Wireless card to recognize and search for wireless networks.  For example, I'm at Denny's right now, and I want to be able to log on to their WiFi.  What steps do I take to allow this to happen, when I don't have IP addresses or passwords for each wifi address.

I tried the "sudo pccardctl ident" command and it gave me some sort of Socket: 0 No device found thing that I don't understand.  And, I tried the "lshw" command and it gave me a huge long list of things.  I just need to get this wireless working because I'm going to Italy soon and I won't have time to deal with it while I'm there.

So, any help would be greatly appreciated.

Thanks,

Adam

---

### Post by the_sorrow on 2008-01-05
What distribution are you using??

---

### Post by dconstruct on 2008-01-05
just regular Ubuntu, whatever the latest one is off of the main download page on ubuntu.com. :)  don't know what it's clever alliterated name is.

---

### Post by the_sorrow on 2008-01-05
There is no "regular" ubuntu, and I think you are using 7.10 Gutsy Gibbon, do you know if its recognizing your wireless card?

---

### Post by TheIceMan on 2008-01-05
im actually having the same problem

i just booted up Ubuntu a little while ago, and i cant find where i can search for wireless networks

i have a dell inspiron 1501, that has a wi-fi light up feature, which the light doesnt turn on when i was using Ubuntu

so i guess i just need to learn how to search for nearby wireless networks, if anyone can help me also, that would be great

thanks

edit: i also have the 7.10 version of Ubuntu, Gutsy Gibbon or whatever it is

---

### Post by the_sorrow on 2008-01-05
Both of you, do this:
Go to the Restricted Driver Manager
System>Administration
and put a printscreen to see the msg.

---

### Post by dconstruct on 2008-01-07
Okay, I did that.  And, basically it told me that my firmware wasn't being enabled.  The firmware appeared to be a Broadcom chipset which, given the title, suggests the wireless card recognition.  So, I went and clicked Enable and it asked me to download the firmware or something from either a website or a location on my computer.  I don't know which to do, but seeing as how I don't have a connection to the internet, I don't know where I could go to download the file and burn it to a CD or something, or even what I would put in that field.  Any suggestions or ideas?

Thanks,

Adam

---

### Post by doorknob60 on 2008-01-07
Ooh...broadcom can be a pain. Try this, I think I've succesfully used this before in Gusty, but you need to use the online installer. [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by anewguy on 2008-01-07
Broadcom can be made to work without much problem - it just takes a little time.  I've done it a lot of times. 

However, before we can assume you actually have a Broadcom chipset, I need BOTH of you to do the following in a terminal window (Applications/Accessories/Terminal):

lspci 

Copy the output and paste it back here so we can see which chipset your wireless is using.

Once you've done that we'll go from there!:)

---

### Post by dconstruct on 2008-01-13
this is the output from my lspci command.  what to do next?

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by dconstruct on 2008-01-13
i don't know if this fixed the problem or not, but i'm at work on a wired connection in Ubuntu and went to the restricted drivers manager, and enabled the firmware for the chipset.  the wireless card lit up on my laptop and now it's recognizing networks.  i can't verify that it will let me connect to any of them yet because they're all restricted networks, but i'll try it a little bit later at a denny's or something and let you guys know.

---

### Post by anewguy on 2008-01-14
I just got back so I could check this thread again.  Was going to do some searching and then reply, but saw your latest post saying it appears to be working.  If indeed it is working, please post back exactly what you did and then marked the thread as "solved".

If it's not working, let us know and we'll do some more searching, otherwise congrats on getting it working!:)

---

