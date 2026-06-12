---
title: "[SOLVED] Internet Connection"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2007-11-19
I moved recently.  I had to get a new modem and that is hooked up and obviously the internet is working fine...  on windows.  

It doesn't work on Ubuntu.  

I don't know how to go about giving you guys information to help fix this but can any one think of what's going on here?  

Thanks.

---

### Post by Shazaam on 2007-11-19
Modem= broadband or dialup?

---

### Post by Partyboi2 on 2007-11-19
How is your pc or laptop connected to the modem, eg. ethernet, wireless. usb?
What sort of network card you using?

---

### Post by santiagoward2000 on 2007-11-19
> **AnLGP said:**
> I moved recently.  I had to get a new modem and that is hooked up and obviously the internet is working fine...  on windows.  

It doesn't work on Ubuntu.  

I don't know how to go about giving you guys information to help fix this but can any one think of what's going on here?  

Thanks.

Hi there and welcome!
Could you tell us what type of modem it is? Does it connect through an Ethernet port or usb?

---

### Post by AnLGP on 2007-11-19
Ethernet.  

How do I figure out what network card I'm running?

---

### Post by Shazaam on 2007-11-19
Panel (taskbar)>Applications>Accessories>Terminal
Type in...
```
lspci
```

This will list your pci devices. Post the output here.

---

### Post by AnLGP on 2007-11-19
How will I post the output from the ubuntu terminal if I can't connect to the internet from ubuntu?  :confused:

---

### Post by Partyboi2 on 2007-11-19
In windows go to hardware management an look at what network card is installed.

---

### Post by AnLGP on 2007-11-19
I am looking for Hardware Management but I can't find it.  I had to reformat my XP when I installed linux.  It died on me.

---

### Post by MegaJim on 2007-11-19
Click on the strart menu, right click my computer -> manage, in the new window click on device manager

---

### Post by Partyboi2 on 2007-11-19
For Xp:
go to Start
right click My computer
click on properties
select hardware tab
choose device manager
click on network adaptors and what is listed should be your NIC card
For vista I am not sure, I think it is pretty much the same.

---

### Post by houstonbofh on 2007-11-19
Grab this for Windows. [http://www.fs-driver.org/](http://www.fs-driver.org/)  Now you can get and post your logs, dmesg and stuff like that.  It is also damned handy in it's own right.  However, you may not want your virus scanner to autoscan your linux partition over night... :)

Now how are you connecting in Windows?  If XP, clicking on the start menu, and choosing Network Connections will list some stuff.  You are looking for 1394 (firewire), Lan, Wireless in one section.  There may also be another section with things like VPN, PPPoE, or other...  List what you find.

Last, what kind of "modem?"  Type Cable/DSL/Other, providor, and location please.

---

### Post by AnLGP on 2007-11-20
I still couldn't find it.  Here's what's listed under "Network Adapters" (The only thing close to anything regarding network I could find):

1394 Net Adapter
Intel(R) PRO/100 VE Network Connection

Just saw the previous post.  I tried to install the program but I don't know what drive letter my linux partition is (I think D:) so I aborted the install.  This is what I've found looking under "Network Connections":

1394 is status "connected" at 400 speed.  LAN is connected at 100 assigned by DHCP.

Modem = Cable, Comcast, Dover (DE).

---

### Post by Shazaam on 2007-11-20
> **AnLGP said:**
> How will I post the output from the ubuntu terminal if I can't connect to the internet from ubuntu?  :confused:

GAH! Sorry. Must have been a senior moment. :oops:

---

### Post by AnLGP on 2007-11-20
S'ok I was just wondering.

I saw there were a few threads posted I didn't see.  I've listed the outputs that I could find, I think.

---

### Post by AnLGP on 2007-11-20
I don't know what happened but it works on Linux now.  Thanks guys :)

---

### Post by Partyboi2 on 2007-11-20
A couple of days ago I was unable to connect to internet with ubuntu, yet i could with Windows. After reading alot and searching around alot. I found out that the problem that I was having that stopped me from having internet access with ubuntu, was that my network card feature of "wake on lan" was set to disabled which meant when windows shut down it was shutting off my network card.
So all I had to do was enable "wake on lan after shutdown" and then I had internet connection.

---

### Post by Niloc on 2007-11-20
Excuse me butting in but I searched for 'modem dialup' and ended up here. I have an IBM T21 laptop which I want to use as a dialup machine.
I did the'ispci' and got :
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)

What do I need now to dialup the ISP??

Thanks,
Colin

---

### Post by santiagoward2000 on 2007-11-20
> **AnLGP said:**
> I don't know what happened but it works on Linux now.  Thanks guys :)

Well, it's good to hear! Do you know if you did something to get it working?

---

### Post by houstonbofh on 2007-11-20
> **Niloc said:**
> Excuse me butting in but I searched for 'modem dialup' and ended up here. I have an IBM T21 laptop which I want to use as a dialup machine.
I did the'ispci' and got :
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)

What do I need now to dialup the ISP??

Thanks,
Colin

As this thread is marked solved, you will want to start your own.  And you have a Xircom Mini-PCI V.90 56k Modem.  Place that in the thread title.

---

