---
title: "print from Gutsy laptop"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Unstuck on 2008-03-11
I'm trying to print from a Feisty laptop to a printer that is connected to a Gutsy desktop.  I've searched the forums, but I only find topics that discuss connecting a linux computer to a windows computer.  I installed cupsys, but I obviously haven't configured something correctly.

---

### Post by handydan918 on 2008-03-11
What exactly have you tried? 
System>Administration>Printing will give you an interface for configuring printers.Choose ipp and enter the ip address of the remote print server (the machine the printer is physically connected to) and click "Find Queue'.
This should pop up a box listing available printers on your network. Click "next", and it will locate the driver for the printer. it should all be pretty intuitive from there.

---

### Post by Unstuck on 2008-03-26
I added the IPP and selected a driver (CUPS + Gutenprint Simplified), but I still cannot print from the laptop.  For kicks, I tried to pause a job that was in queue and got this message >  CUPS SERVER ERROR 
There was an error during the CUPS operation: 'client-error-not-possible'. then tried to cancel the job and got the same message.

---

### Post by Unstuck on 2008-03-27
bump
sorry

---

### Post by Unstuck on 2008-03-30
final bump

---

### Post by xeth_delta on 2008-03-30
Have a look at [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Can you print locally? A couple of months ago I managed to get working more or less what you are describing.

Let us know if you need further help.

---

### Post by Unstuck on 2008-04-01
Thanks, Xeth.  I followed the directions in the link above--open Printer Config--and got this
> xxx@desktop:~$ sudo system-config-printer
sudo: system-config-printer: command not found
 so I went to **System > Admin > Printing** to change the Server Settings...but there weren't server options to check.  

I double-checked to make sure CUPS is installed, and it is...

BTW, I can print from the comp that is wired to the printer.

---

### Post by xeth_delta on 2008-04-02
Did you also make sure the cups server is started?
```
/etc/init.d/cupsys start
```

---

### Post by LowSky on 2008-04-02
first on the gutsy desktop openfirefox andgo here [http://localhost:631/](http://localhost:631/)

log in and do a test page from there


then go to the same address, and add printer, it should find your printer and add it to your list.Make sure both computers are on when you want to print, unless the printer is a network printer then it dont matter

---

### Post by Unstuck on 2008-04-03
I started CUPS then tried to open the Printer Config and got this
> xxx@desktop:~$ sudo /etc/init.d/cupsys start 
 * Starting Common Unix Printing System: cupsd
xxx@desktop:~$ sudo system-config-printer
sudo: system-config-printer: command not found

Just for kicks I went into the printer properties and saw this...don't really know what it means. 
>  Status: Paused: /usr/lib/cups/backend/ipp failed

The same status message was on the CUPS website LowSky recommended.  I tried to log in with my admin username and PW, but it was rejected so I'm not sure which credentials it is asking for.

---

