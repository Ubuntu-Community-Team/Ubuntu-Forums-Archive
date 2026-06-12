---
title: "Two network problems with Ubuntu so far"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by JBull on 2006-04-11
I just installed Dapper on my home PC a couple days ago and everything worked great right away.  I had some trouble changing from DHCP to static IP.  First I logged into the router and turned off DHCP.  Then next time I booted Dapper my network card failed to get an IP (of course).  So I went to the GUI network administrator.  I selected the eth0 card but was unable to configure it.  The "Configure" button was grayed-out.  I had to go command line and manually edit the /etc/network/interfaces file to put in static IP and gateway.  Upon reboot everything worked.  Then the GUI tool was no longer grayed-out.  Strange.

 I had more trouble with the laptop (IBM Thinkpad T20) when I tried to install Breezy.  

I used  grub-for-dos to load the Breezy "network install" kernel and ramdisk.  It started up fine but could not connect to the repository to complete installation.  It said it could not detect my network card.  I'm not talking about wireless.  I have a wired 3com card in the notebook and Breezy could not figure it out.  I had to revert to Fedora Core 4 for the laptop.  Fedora detected the card right away and installed easily over the network.  I did it this way because my laptop won't read CD anymore.  And no floppy.

You would think Breezy would be able to figure out the network card if Fedora was able to do it.

---

