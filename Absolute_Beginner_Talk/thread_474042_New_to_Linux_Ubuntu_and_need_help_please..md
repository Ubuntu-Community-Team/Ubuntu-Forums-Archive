---
title: "New to Linux Ubuntu and need help please."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by livewire94 on 2007-06-14
Im trying to make the switch over to Ubuntu from XP but am having problems installing or configuring my hardware.  I installed my ATI 9700pro video card with Envy and seems ok so far and yes Direct Rendering is enabled.  One question with that is, why does the screensavers seem so slow even though my video card is installed?

Next, I am trying to setup my TV Card.  Its got the saa1730 phillips chip on it but does not show who manufactured it.  In Windows XP the Lifeview drivers and software worked with it but I don't know how to set it up in Ubuntu.  I installed TVtime but it opens in a black screen.  The drivers are probably not setup right and I don't know how to fix them.

I also need to get my Logitech webcam and mouse to work correctly.  I have the Logitech Quickcam IM.   The mouse is a Logitech mx310, has the side buttons.

Thats it for hardware for now.  Im hoping to get everthing to work correctly so I don't have to revert back to Windows XP anymore.  Last question is:  Do I need to install a firewall and antivirus or is Linux Ubuntu almost imune to that stuff?

Thanks in advance for any help.

---

### Post by jasmuz on 2007-06-14
1-Did you check the framerate with glxgears?

2-Your Tv Card should be working, did you try using the Tvtime program with a different input (i had the same issue, and it was me the one with the error) if not, post your /var/log/messages to see what the system says about the card

3-Cant help you much with the webcam, check if its Linux compatible in the hardware list, plus try aMSN out to see if its recognized already

4-No need for antivirus (viruses are mainly for Windows platforms) or Firewall (unless you are very freaky with security)

Best of luck!

---

### Post by hyper_ch on 2007-06-15
You already have a firewall installed called iptables... ;)
If you want a graphical frontend (iptables is quite a beast but you can filter stuff any imaginable way... you can install firestarter... however firestarter is only a very limited frontend for what iptables can do...)

---

### Post by livewire94 on 2007-06-15
Thanks for the replies.  I have been messing around with the tv card and got it to work but the sound is verly low.  I turned up all sound levels but still is low.  

lspci shows this:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:0d.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)


Here is a link to my tv card.  Its the same one.  
[http://www.geeks.com/details.asp?invtid=7130-TV&cat=VID&cm_mmc=TechTips-_-JK-_-TVonComputer-_-s87-21Jul06]("http://www.geeks.com/details.asp?invtid=7130-TV&cat=VID&cm_mmc=TechTips-_-JK-_-TVonComputer-_-s87-21Jul06")

Im new to Linux and am lost when configuring stuff in the terminal.

Thanks for any help.

---

### Post by w4ett on 2007-06-15
For your webcam, do a check of the output of : lsusb  If it's there, go to Synaptic and install an app called Camstream, it's a down and dirty gui camera streamer......just call it up in the terminal: camstream

---

