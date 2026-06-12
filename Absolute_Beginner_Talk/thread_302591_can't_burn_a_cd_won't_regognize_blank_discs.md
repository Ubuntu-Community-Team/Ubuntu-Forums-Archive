---
title: "can't burn a cd: won't regognize blank discs"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2006-11-18
I have tried multiple burning techniques trying to burn anything onto a cd, but I am constantly given the following message (or a similar one)

Waiting for Disk
Found media: **No media**
Please insert an empty CD-R(W) medium into drive

with options to load, eject, force, or cancel.  The drive is working properly with the exception of this issue (reads cds, specs detected fine).

Please help.

---

### Post by sgstarling on 2006-11-18
Please forgive the presumption, but you did insert a blank cd, correct?

---

### Post by ridgeback on 2006-11-18
Haha no problem, yes I have tried many different CD-Rs that I know to be blank, even different brands.

---

### Post by ridgeback on 2006-11-18
I just tried a new burning program and I get the same problem.

---

### Post by CatKiller on 2006-11-19
Out of interest, have you got more than one **optical** drive? Have you selected the appropriate drive in your burning software?

---

### Post by Sef on 2006-11-19
> I have tried multiple burning techniques trying to burn anything onto a cd, but I am constantly given the following message (or a similar one)

Waiting for Disk
Found media: No media
Please insert an empty CD-R(W) medium into drive

with options to load, eject, force, or cancel. The drive is working properly with the exception of this issue (reads cds, specs detected fine).

What cd burning software have you used?

> Out of interest, have you got more than one drive? Have you selected the appropriate drive in your burning software?

I have that problem too now with nautilus, and I have only one hard drive and only Ubuntu installed.

---

### Post by CatKiller on 2006-11-19
> **Sef said:**
> I have that problem too now with nautilus, and I have only one hard drive and only Ubuntu installed.

I've edited my post to clarify what I meant.

---

### Post by ridgeback on 2006-11-19
I have tried the software built into ubuntu (right click --> write to cd), k3b, and gnomebaker.  I have two drives and the correct drive is selected.

---

### Post by ridgeback on 2006-11-19
Update: not sure what this means, but I just tried throwing a blank cd in my other drive, which only reads, and no disk is recognized.  This could be normal for a CD-ROM/DVD-ROM drive to not recognize a blank cd, but given that neither my CD-ROM drive nor my CD-RW drive detect anything when a blank cd is inserted, the problem may run deeper than the drives themselves.  Again, I'm new and stupid so this may mean nothing, but hopefully it sparks some ideas from some of you veterans.

Jerod

---

### Post by ramjet_1953 on 2006-11-19
Have you tried running the burning app in a terminal?
type in sudo <appname>
It will ask for your password and then should run.
The problem with burning to CD ROM's is that you often need to have root priveleges to do so

Regards,
Roger 8)

---

### Post by ridgeback on 2006-11-20
I just tried running k3b from console with sudo and it gave the same error.

---

### Post by mbertini on 2006-11-29
Try: *tail -f /var/log/syslo*g (or use the GUI application in Applications>System Tools>System Log) when you insert the blank CD.

Usually it should be mounted automatically, but check if you get something like:

[I]hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
ide: failed opcode was: unknown
end_request: I/O error, dev hdb, sector 0[/I]

At least that's what I get with empty DVDs.

And no, I havn't a solution yet.

---

### Post by pixelterra on 2006-12-17
I have this same problem with ubuntu/gnome not recognizing my blank CDs. What could be the problem? CD's with data on them have no trouble. 

Is this a hardware problem? My laptop is about 4 years old. I don't even know where to begin fixing this. Maybe a certain brand of blank CD is required?

---

