---
title: "2 problems"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by b-dizzle on 2006-07-03
OK, I have two problems I need help with here.
1. I get internet on my Ubuntu box using a USB Netgear dongle with my wireless network.  It was working fine up until a few days ago, when no matter what I tried, it couldn't connect, though my other computers can.  When I try to look at the network, it says to contact my network administrator about a "SIOCGIFFLAGS error: no such device".  If I go to the network config, it doesn't show a wlan connection of any type.  What went wrong here?

2. Next, once my Ubuntu box can connect to the network, I need help making it so that the printer hooked up to the Ubuntu box can be printed to over the network from my other Windows computers.  Can someone help me here?

---

### Post by b-dizzle on 2006-07-03
OK... strangely enough, after unplugging and replugging the dongle, everything works fine now, on problem #1, except that sometimes when the screen locks or the computer sleeps, it forgets its "location" setting and I have to go in and fix that.  Is there any way to remedy this?  And I still need help on problem #2...

---

### Post by b-dizzle on 2006-07-03
Hello?  Can someone please help?

I have my printer configured on the Ubuntu box.  In Administration>Services, CUPS is enabled. My computer even shows up on the Windows workgroup, but it doesn't show any connected printers.

---

### Post by Apple 101 on 2006-07-04
You need to setup Samba.  In a terminal: gksudo gedit /etc/samba/smb.conf.  There is a section on printers, shares, workgroup, etc.  You will also need to add the printer to the Printer section in Gnome/KDE/Xfce.

---

### Post by wylfing on 2006-07-04
You might try convincing Windows to use CUPS. Try this first:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

This might also be of use if the first link doesn't do the trick:

[http://www.cups.org/windows/index.php](http://www.cups.org/windows/index.php)

Another option, as Apple 101 points out, is to share the printer using Samba. This can be kind of tricky to set up right, so try making things work without resorting to hours of smb.conf hacking.

---

