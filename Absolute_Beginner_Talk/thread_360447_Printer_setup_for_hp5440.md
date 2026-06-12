---
title: "Printer setup for hp5440"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-02-13
Trying to set up a hp5440 printer that is using Windows smb printer. I get this message:

Printing: Unable to connect to CIFS host, will retry in 60 seconds...

Is Samba set up already or do I have to set that up. I just installed Edgy two days ago.

What am I forgetting?

I just tried to add cups and I got this:

davek@davek-desktop:~$ cupsd

Message from syslogd@davek-desktop at Tue Feb 13 04:48:18 2007 ...
davek-desktop cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!
cupsd: Child exited with status 1!
davek@davek-desktop:~$ 


Any clues?

---

### Post by scrooge_74 on 2007-02-13
The printer is on a XP machine you are trying to connect from your Linbox? Or the printer is on the Linbox and is going to be share with an XP.

If non of the above and you only want to use it in Linux for this PC you should use [CUPSYS]("http://www.cups.org") to print.

---

### Post by geovino on 2007-02-13
printer is on a XP machine and I'm trying to connect from my Linbox.


Installed driver  hplip-1.7.1
Seems like it installed, can find it to set up. Is this the right one. I thought that Ubuntu already had the driver for this printer. I have printed with Dapper in the past. 

Is this the right thing to do?

---

### Post by scrooge_74 on 2007-02-13
you are on the right track as long as the XP is sharing the printer you should be able to see it from ubuntu, that driver looks ok.

it should work, as long as you can see the XP PC

---

### Post by geovino on 2007-02-13
I deleted the printer and started over... I had selected the 540 not the 5440, which isn't on the list so I selected the hp5550 and it worked! Go figure!

Thanks:)

---

