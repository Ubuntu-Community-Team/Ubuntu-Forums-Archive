---
title: "[SOLVED] i just can't....get...wireless!!!!"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by jeh0753 on 2008-08-01
Alright, I'm sure there have been like a million other people who had this problem but i can't find a place with a solution which works for me. If you can direct me somewhere that would be great, but please take into account my whole situation first. I am on a 3,1 model MBP, and I am running hardy 8.04 beta, the intel version.
I typed sudo lspci because i saw on another thread that this had important info, so here is the result:
jeh0753@jake:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)
jeh0753@jake:~$ 

In my attempts to solve the problem i have tried a tutorial on [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa), but I had no idea how to follow the directions it linked to about the bug. I also tried another site's directions, which had me use the driver included on mac osx's install cd. I have no idea what i've done already, and i worry that future attempts will not work because i have these other two wireless drivers already installed (theoretically, if i followed the directions correctly).

I do have access to internet via a cord.

Please let me know what to do, or where I might find a site that might tell me what to do. Thanks!

---

### Post by cyberdork33 on 2008-08-01
First, please, please, when posting terminal output or commands, use code tags... It goes like this but don't add the spaces:

[ code]Paste the output here[ /code]

Next, please post the output of:
```
sudo dmidecode| grep Product
```

---

### Post by jeh0753 on 2008-08-01
Alright, sorry about that. here is what I got after putting in that command:
```
Product name MacBookPro3,1
Product name Mac-4238B8 
```

---

### Post by cyberdork33 on 2008-08-01
Ok, you are following the MacBook Santa Rosa Guide, but you hav a MacBook _Pro_. They have different hardware.

Your page is here:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
and the Wireless section refers you to here:
[https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)

---

### Post by jeh0753 on 2008-08-03
Thanks so so much! Success!

---

