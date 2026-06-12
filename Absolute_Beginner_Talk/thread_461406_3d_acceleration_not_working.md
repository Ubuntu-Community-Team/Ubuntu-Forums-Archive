---
title: "3d acceleration not working"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-01
I recently bought Cedega, installed the latest version for use with a few of my favorite MMORPGs. However, when it ran the system testing, all but one thing passed. the "3d Acceleration" failed, and I have no idea how to solve that problem.

System specs:
Intel p4 2.0ghz processor
Onboard video (no graphics card)
256mb of ram
Xubuntu 7.04

I'm not very linux proficient, so can somebody help me out?

---

### Post by dodgePT on 2007-06-01
You gotta have a graphic card, otherwise you wouldn't see nothing in your display :D

Type 'lspci' in a terminal, and paste the result here.

---

### Post by Exershio on 2007-06-01
here's the result:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:04.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
05:09.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
```

---

### Post by dodgePT on 2007-06-01
Now, here's your graphics adapter:>  00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I don't know which driver you should use since i own an ATI... but this way, others might be able to help you better :)

Otherwise, make a search in this forum for intel driver or something.

---

### Post by dodgePT on 2007-06-01
Try this thread: [http://ubuntuforums.org/showthread.php?t=460603&highlight=GE+Chipset+Integrated+Graphics+Device]("http://ubuntuforums.org/showthread.php?t=460603&highlight=GE+Chipset+Integrated+Graphics+Device")

or this one: [http://ubuntuforums.org/showthread.php?t=460685&highlight=GE+Chipset+Integrated+Graphics+Device]("http://ubuntuforums.org/showthread.php?t=460685&highlight=GE+Chipset+Integrated+Graphics+Device")

---

### Post by Exershio on 2007-06-01
I'll try those out, thanks

---

### Post by Exershio on 2007-06-01
I did what was said in that thread and it still isn't working. What else could fix it?

---

### Post by dodgePT on 2007-06-01
Did you do this > you have to reboot, reconfigure your xorg.conf file to use the "intel" device

sudo dpkg-reconfigure xserver-xorg?

And do you confirm that the "Device" section in your xorg.conf has this:

> Driver                "intel"?

Type 'sudo gedit /etc/X11/xorg.conf' in a terminal to check it out.

---

### Post by Exershio on 2007-06-01
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection


that's what's in my xorg.conf

---

### Post by cantormath on 2007-06-02
> **dodgePT said:**
> Did you do this ?

And do you confirm that the "Device" section in your xorg.conf has this:

?

Type 'sudo gedit /etc/X11/xorg.conf' in a terminal to check it out.

I have the same card and I am setting it up using dpkg-reconfigure xserver-xorg,  How much ram would anyone recommend be shared ?  the dpkg-reconfigure xserver-xorg states that my card, which is the card of this thread, need to have it shared memory entered in most occasions. 

Where do I get the xorg intel drivers for dapper? they are not in the repos?
xorg-xserver-video-intel

---

