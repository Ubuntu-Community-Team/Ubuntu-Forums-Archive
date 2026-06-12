---
title: "Windows shared Printer"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by FinePix on 2006-05-07
I have 4 pc connect to a internet router. 3 pc with WinXP and 1 Ubuntu. Theres a HP 3600 printer installed on one of the XP system. 

Tho other 2 computers can print through network. But  I cant.

Can some one help

---

### Post by monomaniacpat on 2006-05-07
This is quite a tough one, as there are so many different perameters involved. In the end, I got mine to work by installing samba (sudo apt-get install samba) then adding a network printer and editing the Device URI under /etc/cups/printers.conf to the following:

DeviceURI smb://WindowsUsername:WindowsPassword@WindowsComputerNameORIPaddress/PrinterShareName

To find out your Computer name, go to system properties (right click on my computer) and look under the computer name tab.

In order toget this to work, however, I first had to disable Norton Internet Security and did the following as described [here]("http://www.annoyances.org/exec/forum/winxp/t1056577268"):

[quote="Joanna"]THIS ACTUALLY WORKS!!!! To install NWLink IPX/SPX/NetBIOS Compatible Transport Protocol Open Network Connections. Right-click a local area connection, and then click Properties. On the General tab, click Install. In the Select Network Component Type dialog box, click Protocol, and then click Add. In the Select Network Protocol dialog box, click NWLink IPX/SPX/NetBIOS Compatible Transport Protocol, and then click OK. I fought this problem for three days before I found this answer. It's a lifesaver, and you don't have to mess with your firewall! Joanna [/quote]

I also did the following, but I'm not sure if this helped:

[http://www.ifelix.co.uk/tech/3002.html](http://www.ifelix.co.uk/tech/3002.html)

There may be other factors involved as well - it's difficult to tell. I found these answers after some persistency through google. Good Luck.

---

### Post by garner_nc on 2006-05-07
Here's what I did.  I have a DeskJet5740,

I went to System > Administration > Printing
Then selected New Printer > Network Printer > Windows SMB (from drop down menu). I had to enter the URL of the PC with the printer (in my case 192.168.0.101).

My PC with the printer had to have the printer selected as shared in properties.I did set-up my XP box to require a password to use the shared printer. I had some issues because I did not configure the printer as shared on the XP box. After setting as shared I re-booted the XP machine.

It was pretty much plug and play (for the Linux world).

All the Best,
Doug White

---

