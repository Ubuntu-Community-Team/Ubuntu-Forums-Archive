---
title: "Connecting to a printer"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by chillieman on 2007-06-06
Situation: I look after 3 p/c's in our office. 2 run widows xp and 1 now has ubuntu. the main p/c -which runs windows - has the printer connected to it (HP laserjet 1010) and is set for share. the other 2 p/c's were able to print from the main p/c via the network. I need to be able to use the office printer, which is on the windows p/c, from the ubuntu p/c. How do i do it???

---

### Post by lazyart on 2007-06-06
Go to System>Administration>Printers

Select Network Printer and change type from IPP to Windows printer (SMB)
Use the drop down to select the host machine
Then the next drop down to select the specific printer
Add your windows username and password if it's necessary but it's probably not.

Tada-- you can now print.

---

### Post by homergreg on 2007-06-06
start by typing    localhost:631      into your firefox address bar.  That should take you to your CUPS printing system, at least it does for me.  You should be able to add a shared windows printer through samba by following the wizards in CUPS.  

At least that will be a start.

(edit: or do what lazyart just said to do.  I'm a little slow on the draw ;)

---

### Post by esavato on 2007-06-06
I really like this guide on Linux Reality.  It breaks everything down and is succinct.

[http://linuxreality.com/docs/ep29notes.txt](http://linuxreality.com/docs/ep29notes.txt)

Basically, install cups, samba, configure cups, configure samba, add printer.  Just remember your windows password and user name.

---

### Post by MindFork on 2007-06-08
I followed the steps below, but in the "printer" drop down, there is nothing.  

What's interesting is that the username/password only accepts my ubuntu u/p, not the windows login.  If I enter the windows login, it keeps prompting me to log in after a few seconds.

The printer is being shared by two other windows computers just fine, although they do have to log into the network before they can print.  Do I need to change my windows box so that a login isn't required to access it?  Scary thought.

> **lazyart said:**
> Go to System>Administration>Printers

Select Network Printer and change type from IPP to Windows printer (SMB)
Use the drop down to select the host machine
Then the next drop down to select the specific printer
Add your windows username and password if it's necessary but it's probably not.

Tada-- you can now print.

---

### Post by PsychoKlown on 2007-06-18
> **homergreg said:**
> start by typing    localhost:631      into your firefox address bar.  That should take you to your CUPS printing system, at least it does for me.  You should be able to add a shared windows printer through samba by following the wizards in CUPS.  

At least that will be a start.

(edit: or do what lazyart just said to do.  I'm a little slow on the draw ;)

OMG Thank you! I've been trying to figure this out for days. The CUPS page is so easy to use. Easier than the Admin area!

<3 homergreg :KS lol

Thanks again!

---

