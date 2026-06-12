---
title: "Printing on a WinXP network"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by cb03BoilerUp on 2006-03-15
Until now, I have been purely a Windows user.  My home network consists of a desktop running XP, a laptop running XP, and my Ubuntu box.  I have an HP 5600 all-in-one that is shared by the XP desktop.  File sharing using SAMBA has been working well so far, but when I tried to setup the printer on the Linux machine, I get the error in the status area of the properties window: 
' Ready: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_ACCESS_DENIED' 

The frustrating thing is that when I try to print, I watch the print queue on the XP desktop; and it shows the print job, but only ~64K loads, and then it stops.:confused: 

Any suggestions?

---

### Post by Jedeye on 2006-03-15
I dont have a lot of experience with printers but its worth a shot. go to System>Administration>Printing then click the Global Settings menu and choose Detect LAN Printers and see if it shows up.

---

### Post by bluerags on 2006-03-16
yop, that works like a peach! a couple clicks an my hp1200 on my winME machine spits my linux-made papers like crazy.

---

### Post by noswal on 2006-03-16
I have a similar problem but have a Toshiba copier/scanner/printer (laser) e-studio 120 from an extensive search on google there is nothing for linux, I've tried a few random postscipt drivers but nothing.

With Global Settings menu connecting to my xp laptop the add printer option still requests a driver

Any ideas, anyone?

---

### Post by chazaq on 2006-03-16
I just installed Ubuntu on a company desktop after WinXp crashed for the last time.
The end-user really likes Ubuntu (so do my boss and I).  
However, I am growing wearing of trying to get it to print on a network printer.

I have a Lanier 5635 connected on a network as it's own IP address and i share it out through a Windows 2000 Server computer.

Like everyone else I see on Google, I get one of the following errors:
NT_STATUS_FAILURE or 
Unable to Connect to Samba Host

I think I am very close because I have the user able to logon and access the Win2K Server files but not able to print... **Please help !** 
The sooner I can get this mastered the sooner I get more Ubuntu desktops in the office!!!\\:D/

---

### Post by linkman on 2006-04-16
[QUOTE=cb03BoilerUp]Until now, I have been purely a Windows user.  My home network consists of a desktop running XP, a laptop running XP, and my Ubuntu box.  I have an HP 5600 all-in-one that is shared by the XP desktop.  File sharing using SAMBA has been working well so far, but when I tried to setup the printer on the Linux machine, I get the error in the status area of the properties window: 
' Ready: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_ACCESS_DENIED' 

The frustrating thing is that when I try to print, I watch the print queue on the XP desktop; and it shows the print job, but only ~64K loads, and then it stops.:confused: 

Any suggestions?[/QUOTE]

You know sometimes we are not real smart - are we.

I have spent a few weeks trying to get my HP5600 to print from ubnutu via my Windoze box. I have experienced the same pain that is mentioned here - 64 k loads and then the queue hangs.

After much investigation I decide to try the WIKI and look what I find -

[https://wiki.ubuntu.com/WindowsXPPrinter?highlight=%28printer%29](https://wiki.ubuntu.com/WindowsXPPrinter?highlight=%28printer%29)

In short - go to the windoze box and uncheck bi-directional communication and you will print.

The authentication issue - make sure that you a user set up on your linux box which has the same use name and password as your windows user. That should fix it.

Have fun.

---

### Post by alastair mccracken on 2006-04-16
I have a home network running two windows xp destops and a seperate epson printer with a printsir print server. To get the windows xp desktops to print you set up the printer and then run a printsir installation disk. Can't run it in Linux as its for windows. Anyone any ideas how to get my ubuntu laptop to print over my home network?

---

### Post by uteck on 2006-04-16
[QUOTE=alastair mccracken]I have a home network running two windows xp destops and a seperate epson printer with a printsir print server. To get the windows xp desktops to print you set up the printer and then run a printsir installation disk. Can't run it in Linux as its for windows. Anyone any ideas how to get my ubuntu laptop to print over my home network?[/QUOTE]
Linux uses Cups to handle printer, so it there is a good chance it has the driver allready. Failing that, the 'raw' or 'generic' options work fine.  Go to System - Administration - Printing and add the printer.  The interface is similar to windows.

---

### Post by uteck on 2006-04-16
[QUOTE=chazaq]I just installed Ubuntu on a company desktop after WinXp crashed for the last time.
The end-user really likes Ubuntu (so do my boss and I).  
However, I am growing wearing of trying to get it to print on a network printer.

I have a Lanier 5635 connected on a network as it's own IP address and i share it out through a Windows 2000 Server computer.

Like everyone else I see on Google, I get one of the following errors:
NT_STATUS_FAILURE or 
Unable to Connect to Samba Host

I think I am very close because I have the user able to logon and access the Win2K Server files but not able to print... **Please help !** 
The sooner I can get this mastered the sooner I get more Ubuntu desktops in the office!!!\\:D/[/QUOTE]
Have you checked for the bi-directional problem like in another post?

Have you consider having the user print directly to the printer?  Or would it be possable to put in a Linux print server?  When Cups is set up to auto share, the printers just show up in client Linux and Mac boxes.  You just have to weed out the ones you done to be displayed.

---

