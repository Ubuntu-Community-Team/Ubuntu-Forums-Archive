---
title: "[SOLVED] Wireless USB adapter installation question"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by IanB2 on 2007-05-05
I am a brand new Linux user and have a test machine set up with Ubuntu.
I was having problems with wireless network connections so I bought an edimax wireless high gain USB adapter from the linuxemporium which claims to run on major distros.
I've tried just running up the system and plugging in the USB adaptor. That doesn't work.
The question is HOW do I install the driver on the CD to my system? 
(I'm used to Windows and was looking for an exe or a 'run' type command). The files on the CD are totally unfamiliar to me. (I have the USB adaptor successfully working on the Windows partition of the drive)

---

### Post by mikeyphi on 2007-05-05
Look for linux packages either .tar.gz  or .deb for a start

Or you could go the ndiswrapper route, look here for the guide - it's not your USB plug but the general instructions will be OK: [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

---

### Post by IanB2 on 2007-05-05
I have a bunch of linux type files on the CD that was provided for the USB adapter. I just cannot find any explanation anywhere of how to 'install' these files. The instruction that came with the USB adapter might as well be written in Chinese, and assume a good understanding of Linux. I bought this device because I thought it would be easy to install. :confused: 

 Is there a simple explanation somewhere of how to install a USB driver onto a Linux system (in Windows you just launch the exe file from the CD provided .... now that is easy!)

---

### Post by candtalan on 2007-05-05
Sorry to hear you are having problems. It sounds as if it is easily possible to use your usb wireless but - as you note- this may not be easy for a beginner.

For future note - a good approach could be to ask in a forum before purchase for the easiest choice to purchase, some are instant. For example I have a wireless card (pcmcia) containing a prism 54 chip and it connects to nearby networks automatically. (kubuntu 7.04).No driver installation whatsoever.

When I was a beginner I returned two different wireless cards to retail outlest because they were not working (easily) with linux, but now I could manage these if I chose I think.

If you stay with your usb stick, post here some more details, for more detailed comments?

Wireless has been made easy for many units in version 7.04, you seem to have got one which is not the easiest for a beginner.

hth

---

### Post by IanB2 on 2007-05-05
Thanks!

The USB deice is an Edimax hi-gain USB 2.0 adapter bought from linuxemporium.
I've had a terminal open and followed the examples given and think I've installed the device. (I don't really know what I'm doing .... but guessing)
I'm asked for the SSID as the installation completes, so something is happening, however, after a reboot on plugging in the USB device and using the 'sudo ifup rausb0' command, everything goes very slowwwwwly and there are not more messages on the terminal.

Any suggestions? (I'm running 600MHz on 192MB ram. )

---

### Post by IanB2 on 2007-05-06
I have had a very painful 12 hrs teaching myself how to run a terminal and some basic commands. The concept of Linux is superb, however the practicalities can be just too great to overcome!  ???

I bought the edimax USB device from a 'Linux friendly' site deliberately to try and avoid the situation that I now find myself in.

I have followed the script provided with the USB device e.g.
[b]mkdir /root/ralink
cd /root/ralink
tar xvf /media/cdrom0/le_ralink_install.tar
./install_rt61_rt73.sh[/b]

A whole series of actions then take place finishing with 'please enter your network id' ...... so I believe that I've successfully installed the driver.
After a reboot where everything works normally, I then run the command
**sudo ifup rausb0**
I get the following : **rausb0: ERROR while getting interface flags: No such device**
So I then plug in the the USB device and repeat the above command.
The big difference this time is that while all is still working, Linux is very slooowwwww to respond to keyboard strokes. At this point the cursor just flashes in the teminal and nothing more happens.

The USB adaptor works fine in the windows partition on the PC, so I don't believe that this is a PC hardware issue. Is this Linux or the USB adaptor (faulty).

Any help/advice would be much appreciated. It would be a pity if my journey into Linux stopped at this point, however without internet, Linux is not much use to me.

P.S. To add insult to injury, I tried to install the windows driver using the ndiswrapper to be told by the system (after successfully installing ndiswrapper using the Ubuntu installation CD) that **ERROR : no versions of ndiswrapper found**. The advice is to download and compile from the source code (even this is probably one stage too hard for me) and HOW do I do this without an internet connection? This presumably means that I will not be able to try any other USB wireless adaptors using the windows drivers.

---

### Post by candtalan on 2007-05-07
Thank you for the information, it looks as if you are nearly there but not quite.
I know only a very little about wireless and the experts on the wireless forum cannot find you easily here. I am very sorry for the problems, but if you could copy your information into the forum such as
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)
then they should be able to help you better than I can in the beginners forum. So sorry for the difficulty - I am on internet access which is unpredictable - I am travelling just now, so I cannot do much at any one session.
good luck with the networking and wireless forum I think they can help you more.

---

### Post by IanB2 on 2007-05-12
I'm writing this reply from my Ubuntu box using the USB wireless adapter ...... great!

Many thanks for everyone's help with this.

In the end, Quentin from Linuxemporium adapted the USB driver to run on the latest release of Ubuntu. Thanks Quentin.

The problems seem to be minor changes required for the new release.

---

