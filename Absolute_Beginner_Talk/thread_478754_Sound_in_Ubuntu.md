---
title: "Sound in Ubuntu?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by pagzforpres on 2007-06-19
Hello, 

I am new to the Ubuntu community and have a quick question. I am unable to set up my sound (no driver!) and don't know how to find the driver I need. How can I identify my Sound Card? Please let me know. 


Thanks.

---

### Post by nutz on 2007-06-19
> **pagzforpres said:**
> Hello, 

I am new to the Ubuntu community and have a quick question. I am unable to set up my sound (no driver!) and don't know how to find the driver I need. How can I identify my Sound Card? Please let me know. 


Thanks.


What is the make and model of your computer?

---

### Post by old_geekster on 2007-06-19
Welcome!

The website for the computer manufacturer should have that information available for you.  It most likely is integrated sound, if you didn't add a sound card.

If you do have a separate sound card, simply open the case and look at the card.

---

### Post by pagzforpres on 2007-06-19
When I run lspci in the terminal here is my outcome: 

andrew@andrew-desktopubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 LE (rev a1)
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
03:03.0 Multimedia audio controller: Creative Labs SB X-Fi

---

### Post by iPirates on 2007-06-19
check this guide out.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=Sound+Problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=Sound+Problem)

further down the page, it has a link to a website that lists all the cards, and whether drivers for them are available.  most cards are supported, but the first one i had wasn't, so i was out of luck!  
guess that's what i get for buying a cheap card  ;)

---

### Post by iPirates on 2007-06-19
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)
is the link to the card support site.
I'm not sure how update to date it is, but some newer cards are on there, so it must be updated from time to time...

---

### Post by pagzforpres on 2007-06-19
Never Mind...

---

