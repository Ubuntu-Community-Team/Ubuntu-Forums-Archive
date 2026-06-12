---
title: "[SOLVED] Trouble with Ethernet"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by HappyGuy938 on 2007-08-24
Hi guys,

I just installed Xubuntu 6.06 on my 5 year old computer, and I'm having some trouble getting the DSL to work.  When I go into the network dialog box, it detects that the ethernet is active (and enabled), but the ethernet light on my modem is off when I boot into Linux (it's on when I'm in Windows) and I can't use the Internet.  Any help would be apperciated.  =)

---

### Post by HappyGuy938 on 2007-08-24
After some investigation, I can further add that my ethernet card is a Realtek RTL8100.  My DSL requires special filters on the phone and TV (I do not know what this kind of DSL is called, but I hope that helps in diagnosing my problem).

---

### Post by nitro_n2o on 2007-08-24
knowing what is your modem might also help

---

### Post by HappyGuy938 on 2007-08-24
The modem was provided by my ISP; all I can say is that it is a Westtel.

---

### Post by ramjet_1953 on 2007-08-24
Does your ADSL router plug into an Ethernet port, or a USB port on your computer?

Regards,
Roger :cool:

---

### Post by HappyGuy938 on 2007-08-24
It plugs into an ethernet port.  Again, I'm using Ubuntu 6.06 (I'm not sure if that makes a difference).

---

### Post by HappyGuy938 on 2007-08-24
Thanks to all those who have taken the time to stop and post so far.  =)

---

### Post by ramjet_1953 on 2007-08-24
No, using 6.06 will not be an issue.

It is strange that your Internet didn't just work straight-up.

When you installed, was the router plugged into your PC and turned on?

Also did it automatically download updates during install?

Regards,
Roger :cool:

---

### Post by wormser on 2007-08-24
Are you getting an ip address?  Applications> Accessories> Terminal> ifconfig.  Also trying pinging the modem/router and other sites.  Post results.

Did you completely shut down your PC before booting or did you just restart from Windows?  I had and saw another post where once you reboot from Windows your ethernet does not work.  For that bug you just need to shut the PC down and start it manually.  That is a shot in the dark but it is worth checking.

---

### Post by HappyGuy938 on 2007-08-24
Everything was plugged in, but it did not seem to download any updates duriung install.

---

### Post by HappyGuy938 on 2007-08-24
Thanks, I'll try those things shortly.

---

### Post by anewguy on 2007-08-24
I'll also try asking for a little more information:

What brand and model is your motherboard?

type  lspci   in a terminal window and post the results back here for us to see.


Thanks!:)

---

### Post by HappyGuy938 on 2007-08-24
My motherboard is an ASUS P4G533, according to HP.

---

### Post by HappyGuy938 on 2007-08-25
Thanks for all the help so far guys; I'll do my best to get the information you requested quickly.  =)

---

### Post by HappyGuy938 on 2007-08-25
Here is what I found:

**1. Turning the computer off then on again:** no effect.

**2. pppoeconf:**  fails.

**3. ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:40:2B:3F:9F:E8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1356 (1.3 KiB)  TX bytes:1356 (1.3 KiB)


**4. lspci:**
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)


Thanks guys!

---

### Post by wormser on 2007-08-25
This [post]("http://ubuntuforums.org/showthread.php?t=517324&highlight=8139") looks like it can help you.  

This looks like what solved it:

Boot and at the Grub screen hit ESC, then e.  Next, find the kernel command line and again hit e. Append the option **noapic** at the end.

If that works then you can add the line to your /boot/grub/menu.lst file by adding the option to the kernel line.

---

### Post by HappyGuy938 on 2007-08-25
> **wormser said:**
> This [post]("http://ubuntuforums.org/showthread.php?t=517324&highlight=8139") looks like it can help you.  

This looks like what solved it:

Boot and at the Grub screen hit ESC, then e.  Next, find the kernel command line and again hit e. Append the option **noapic** at the end.

If that works then you can add the line to your /boot/grub/menu.lst file by adding the option to the kernel line.

As a matter of fact, sir, that did not work.  I tried noapic, acpi=off (which caused the computer to freeze), and both of the commands at once.  None of it succeeded in allowing me to access the Internet.  :(

---

### Post by HappyGuy938 on 2007-08-25
I feel I should also add that I am positive it isn't the modem's compatability with Linux.  I've had a different Linux box connected to the same modem in the same place, and it works just fine.

---

### Post by HappyGuy938 on 2007-08-25
I have still more information:
1. I can ping my own IP address.
2. I can neither ping the IP nor web addresses of anything else.
3. My ethernet also did not work on the LiveCD (I would have said so sooner, but I needed to go back and check).

---

### Post by HappyGuy938 on 2007-08-25
I just tried Puppy Linux.  It booted the same driver that Ubuntu used (which is what should work OK for the ethernet card in the motherboard), but was unable to connect to the Internet.  Like Ubuntu, it confirmed that the connection was active, but timed out when it tried activating it.

I tried other drivers, but only that one would load--and the Internet still would not work.

---

### Post by uclalinux on 2007-08-25
if you get internet using windows. then the internet is fine.

try and run

"sudo dhclient" 

also you might need to find the driver for your Ethernet card and install it.

---

### Post by HappyGuy938 on 2007-08-26
The *only* drivers for my particular card are the ones in the kernel--the ones that aren't working out for me.  The command **dhclient** did nothing at all to solve this.

Since I know for a fact that it is my card and not the modem that Linux doesn't like (I've connected a different computer running Linux to it and it worked fine), it must be the card.

Is there any software method to solve this incompatability, or is the best choice just to buy a  $20 Linux compatable card and use that instead?

---

### Post by uclalinux on 2007-08-26
what ethernet card won't work, I have a Realrek rtl8111/8186B and i have to added modules to the kernel to get it work.

---

### Post by HappyGuy938 on 2007-09-10
In then end, I just bought a new 3Com ethernet card and everything works very, very well now.  Thanks for all of your help!

---

