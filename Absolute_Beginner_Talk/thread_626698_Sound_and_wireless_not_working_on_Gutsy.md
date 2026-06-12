---
title: "Sound and wireless not working on Gutsy"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by witkows6 on 2007-11-29
I recently purchased an Acer 5920 and installed Gutsy 7.10.  I also have Vista on it.  My sound and wireless works fine on Vista, but I can't keep a wireless connection in Ubuntu and I have no sound.  I'm new to Linux and do not know much about programming.  Is there anything I can do to resolve these issues?

---

### Post by Sandlst on 2007-11-29
Sorry to hear you are having problems.  By your description of wireless troubles, I am guessing you mean you can connect to router(s) with your wireless card, but the connection keeps dropping?  If this is the case, could you tell us the make/model of the wireless card you are using? 

As for sound, can you change volume in the top bar, or does it not even let you do that?  If you can, try double clicking on the volume applet, going to File/Prefrences and enabling the different elements you see there.  Sometimes you have to increase the volume in another channel besides "Master" for sound to work, if I install ubuntu on another computer and have sound issues, this is what I do first.

If you get an error when you try to do this, could you please tell us the make/model of your soundcard?

Hope this helps, post back if you have any problems.

---

### Post by quandary on 2007-11-29
They maybe have included the new linux kernel 2.6.23.1
If so, you need to compile the latest ALSA sound driver
and download an updated wireless driver and firmware...

I had an intel bg2200 wirless card wich dropped connections.  That was because the power saving firmware on my accesspoint was errorous.
As there was no firmware update I simply had to switch off power-saving...

---

### Post by witkows6 on 2007-11-29
That fix worked for the sound.  With the wireless, I don't have the wireless icon in the upper right hand corner.  It was there before, but it seems to only show up  when it wants to.  If I click to do things manually, there is no option for wireless settings.  It was there before, and now it just isn't.  I'm not sure the make and model of the wireless card.  It is a built in 802.11a/b/g/n.  Thanks for your help.

---

### Post by Sandlst on 2007-11-29
Hmm, I can't think of the exact place right now (Im not at my ubuntu computer) but under SYstem/Prefrences or System/Administration you should be able to view hardware profiles, which might have an entry describing your card.  Try looking there.  Also, do you have a windows driver cd for the card?  There is a program called ndiswrapper that can use windows drivers on linux, depending on your card that may be the only way to get it working.

---

### Post by quandary on 2007-11-29
In the terminal, type: lspci

You should get something like:
------------------------------------------------------
root@googlebot:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
root@googlebot:~# 
----------------------------------------------



you can type:  lspci | grep "Network controller"
which should give you your network card directly:
------------------ Looks like this-------------------------------
root@googlebot:~# lspci | grep "Network controller"
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
root@googlebot:~# 
-------------------------------------------------

---

### Post by witkows6 on 2007-11-29
ok,  I have an Intel PRO/wireless 4965 AG or AGN network connection (rev 61) and no disc came with the computer

---

### Post by quandary on 2007-11-29
> **witkows6 said:**
> ok,  I have an Intel PRO/wireless 4965 AG or AGN network connection (rev 61) and no disc came with the computer

Revision 61 ? WTF !!!

I don't know whether it helps for your problem (probably driver issue), but I got my wireless to work by installing the latest ipw2200 driver from Intel for Linux.

So doing the same for you might help. I googled for your driver model, just as i did for mine, and got this site: 
[http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

The site recommends you using this driver, known to work:
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Your try now, I don't have your card so I can't help you any further. 
Follow the instructions. 
Good luck !

PS: Before playing around with the drivers, make sure you didn't misconfigure any encryption you possibly use...

---

### Post by witkows6 on 2007-11-29
I'll give it a shot, thanks for your help.

---

