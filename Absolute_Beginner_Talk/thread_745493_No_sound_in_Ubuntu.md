---
title: "No sound in Ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by JCM45 on 2008-04-04
hey guys!  been using Ubuntu for a few weeks now and i like it a lot.  however i have one problem i have yet to solve.  no sound comes from my speakers.  let me elaborate.  i am currently dual booting windows vista and ubuntu on my HP Pavilion dv6780se Special Edition Laptop.  the blue touch controls right above the keyboard all work in ubuntu.  i can play and pause and the quick play button even works.  now my volume controls work too because in ubuntu i can see the volume bar moving.  the mute button also mutes and unmutes in the OS on the volume control display.  however when the sound is muted the blue mute button will be red.  whenever im in ubuntu my mute button is red and will not change when i touch it.  the display on the screen will say its unmuted but no sound ever comes out.  i figure i need some new sound drivers however i do not know where to get them because im still fairly new with linux.  so if anyone could help me that would be greatly appreciated.  also i am relatively new on linux still so as basic as possible would be great.  thanks,

---

### Post by JCM45 on 2008-04-04
anyone?

---

### Post by stchman on 2008-04-04
> **JCM45 said:**
> hey guys!  been using Ubuntu for a few weeks now and i like it a lot.  however i have one problem i have yet to solve.  no sound comes from my speakers.  let me elaborate.  i am currently dual booting windows vista and ubuntu on my HP Pavilion dv6780se Special Edition Laptop.  the blue touch controls right above the keyboard all work in ubuntu.  i can play and pause and the quick play button even works.  now my volume controls work too because in ubuntu i can see the volume bar moving.  the mute button also mutes and unmutes in the OS on the volume control display.  however when the sound is muted the blue mute button will be red.  whenever im in ubuntu my mute button is red and will not change when i touch it.  the display on the screen will say its unmuted but no sound ever comes out.  i figure i need some new sound drivers however i do not know where to get them because im still fairly new with linux.  so if anyone could help me that would be greatly appreciated.  also i am relatively new on linux still so as basic as possible would be great.  thanks,

What kind of sound card do you have?  Give us an lspci output here.

---

### Post by JCM45 on 2008-04-04
ok once again im new how do i do that?  i forgot the command.

---

### Post by nnamdi on 2008-04-04
hello open your terminal and type this command post the output back ok am waiting

---

### Post by SlappyPappy on 2008-04-04
I think he wants you to go to Applications/Accessories/Terminal

Then type in lspci

lspci is the command. It will spit out a bunch of gibberish, copy it and post it back here for interpretation.

BTW I don't really know what I'm doing. I only installed yesterday, and just got my audio working but I have no idea how! This is crazy.

Still need to get my modem going, DVDs, MP3s, and better looking picture, still looks all wonky.

At least I can listen to CDs now.

Good luck friend.

---

### Post by JCM45 on 2008-04-04
it says all this stuff:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by nnamdi on 2008-04-04
sorry on your destop click on Application on the left top corner of your Desktopa drop down menu comes out then click on Accessories brings out another menu list where you will find Terminal click on it then it open

1.type: lspci
copy the out and paste it back to the forum there will know how to go about it

---

### Post by JCM45 on 2008-04-04
i did.  uts right above your post.

---

### Post by JCM45 on 2008-04-04
also in my sound mixer the second two catergories were muted and when they were unmuted nothing happend.

---

### Post by SlappyPappy on 2008-04-04
I don't think he sees so good. His monitor must be more jacked up looking than mine!  :confused:

---

### Post by erginemr on 2008-04-04
I believe by following the steps in this howto:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

you will be able to have the sound work.

---

### Post by JCM45 on 2008-04-04
i got it working guys thanks.

---

### Post by erginemr on 2008-04-04
Great! :D

But for the sake of documentation for future solution seekers, how did you do it?

And on a final note:
**To close a thread **-> You may select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by nnamdi on 2008-04-04
first download these [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and it. but i download the 1.5 version

---

### Post by stchman on 2008-04-04
> **nnamdi said:**
> first download these [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and it. but i download the 1.5 version

I used the 1.0.16 ALSA to get my headphone jack sense to work.  The sound otherwise worked with 1.0.13 ALSA.

---

