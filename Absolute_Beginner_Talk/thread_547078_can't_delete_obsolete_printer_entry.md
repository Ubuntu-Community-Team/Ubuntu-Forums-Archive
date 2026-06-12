---
title: "can't delete obsolete printer entry"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-09
I have an obsolete printer entry on my system, and I can't delete it from system->printing->rt click -> delete printer (no result) or from CUPS- delete printer, which gives me a 403 Forbidden error. How can I get rid of the damn thing?

---

### Post by tgalati4 on 2007-09-09
In a browser:

localhost:631

Pick "Printers"

Pick "Delete Printer"

root

(root password)

Good luck

---

### Post by p_quarles on 2007-09-09
You should be able to edit it out of the text config file:
```
gksudo gedit /etc/cups/printers.conf
```
And, of course it's always a good idea to make a backup before editing config files:
```
sudo cp /etc/cups/printers.conf /etc/cups/printers.conf_bak
```

---

### Post by ginestre on 2007-09-09
> **p_quarles said:**
> You should be able to edit it out of the text config file:
```
gksudo gedit /etc/cups/printers.conf
```

provoked this error

richard@Richard-upstairs:~$ gksudo gedit /etc/cups/printers.conf
(gedit:6004): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
richard@Richard-upstairs:~$ 

nevertheless the file opened, and the incriminated printer , which I wish to cancel, is just not listed  there.

???

---

### Post by p_quarles on 2007-09-09
Yeah, that error shows up when you run something using gksudo. It's a false alarm, though, and it's much better than using sudo to run a graphical application (see [this]("http://www.psychocats.net/ubuntu/graphicalsudo")).

Okay, try this:
```
lpstat -t
```
Does the unwanted printer show up there, too?

Also, my system has an apparent backup of printers.conf called printers.conf.O (capital o) -- does it show up there, by chance?

---

### Post by ginestre on 2007-09-09
> **p_quarles said:**
> Y
Okay, try this:
```
lpstat -t
```
Does the unwanted printer show up there, too?

Yes, it does. It's the Laser@192.168.0.4:in the output below

richard@Richard-upstairs:~$ lpstat -t
scheduler is running
system default destination: Laser_1230
device for BRFAX: usb://Brother/MFC-210C
device for Laser@192.168.0.4: ipp://192.168.0.4:631/printers/Laser
device for Laser_1230: socket://192.168.0.2
device for MFC210C: usb://Brother/MFC-210C
BRFAX accepting requests since Thu 24 May 2007 09:15:50 PM CEST
Laser@192.168.0.4 accepting requests since Sun 09 Sep 2007 10:28:59 PM CEST
Laser_1230 accepting requests since Sun 09 Sep 2007 09:12:35 PM CEST
MFC210C accepting requests since Mon 27 Aug 2007 09:51:41 AM CEST
printer BRFAX is idle.  enabled since Thu 24 May 2007 09:15:50 PM CEST
printer Laser@192.168.0.4 is idle.  enabled since Sun 09 Sep 2007 10:28:59 PM CEST
printer Laser_1230 is idle.  enabled since Sun 09 Sep 2007 09:12:35 PM CEST
printer MFC210C is idle.  enabled since Mon 27 Aug 2007 09:51:41 AM CEST
richard@Richard-upstairs:~$ 


> 
Also, my system has an apparent backup of printers.conf called printers.conf.O (capital o) -- does it show up there, by chance?

Yes, it does. Shall I kill it from here?

---

### Post by p_quarles on 2007-09-09
Yeah, give that a try. If that doesn't work, I'll try to hunt down the bash command to remove the entry.

---

### Post by ginestre on 2007-09-09
> **p_quarles said:**
> Yeah, give that a try. If that doesn't work, I'll try to hunt down the bash command to remove the entry.

Knocked it out from both files, and for good measure rebooted the system. The incriminated printer is nowhere to be seen in the new conf or conf.O files, but is still lurking in CUPS! Where is the CUPS thingie finding the damn printer???

---

### Post by p_quarles on 2007-09-09
That's a good question. Maybe this printer has an unfinished job assigned to it. Try:
```
lpq -a
```
to list pending print jobs.

---

### Post by ginestre on 2007-09-09
> **p_quarles said:**
> That's a good question. Maybe this printer has an unfinished job assigned to it. Try:
```
lpq -a
```
to list pending print jobs.

-no entries

so that's not it.

---

### Post by p_quarles on 2007-09-09
Well, I can think of a couple more things to try, but it looks like this is beyond my knowledge of CUPS.

1) Your lpstat output indicated that this printer is/was on a separate machine, or is shared with the network. If it's on a different computer, try running a browser to the CUPS interface on that computer. It might also be as simple as "unpublishing" the printer prior to deleting it.

2) It's possible that CUPS is finding the printer from its entry in /etc/cups/ppd/  -- you could try removing that entry (don't delete the whole directory, though, of course). 

Beyond that, I'd suggest you just look through all the files in /etc/cups and ~/.cups for any references to the stubborn printer.

---

### Post by ginestre on 2007-09-09
Thanks for your help. Unfortunately, the machine which was governing this printer is no longer on the network -it was trashed -  so I can't intervene there in any way.  But I'll try looking in the other cups directories tomorrow: it's past midnight here and I've already spent three hours on this! Time for bed.

Once again, thanks for the input.

---

### Post by p_quarles on 2007-09-09
Yeah, it would be difficult to delete files on a computer that doesn't work :)

One thing you could try, though, is temporarily setting one of your machines to the static IP *formerly* used by the trashed server. The CUPS web interface doesn't like it when you try to delete printers remotely, but this might fool it into letting you. This advice comes with *no *warranty, though :)

FWIW, CUPS itself has a pretty active help forum. I didn't see this problem during my quick search, but that might be something to check out if you can't resolve this otherwise.

---

### Post by tgalati4 on 2007-09-11
If this printer was defined on another computer on the same network, then it will keep popping up.  You need to delete it from all computers on the network, because CUPS automatically shares all printers on the same subnet.  It's possible that you deleted it from your local machine, but there is still a print queue floating around on another machine.

---

