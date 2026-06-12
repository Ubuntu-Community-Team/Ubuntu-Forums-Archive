---
title: "wine diablo 2 dapper"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by leLune on 2007-02-21
Get an odd msg went I try to run diablo 2 (see attachments.) Diablo 2 seem to install fine but a can't get it to run. Any helpful points? Using ubuntu 6.06

---

### Post by Eddie Wilson on 2007-02-21
Check the config of your drives. What kind of hardware do you have?
Eddie

---

### Post by leLune on 2007-02-21
Hmm..not sure I know how to do that. But, I know about winecfg is that what you mean?

Hard Disk:
Maxtor 6YO80PO 76.34 GiB (what's GiB? Sorry, many questions!) /dev/hda
Lexar jumpdrive 247.50 MiB (Man in Black?) /dev/sda
SanDisk Sansa m230 483.89 MiB /dev/sbd
Compaq CRD-84028 /dev/hdc

screeny of winecfg for drives

---

### Post by ADT on 2007-02-21
I have the same problem with homeworld. I own a legal copy of the game and when I install the game using wine and then try to run the game using wine an error pops up saying something like "Please insert the homeworld CD".
The installed computer game doesn't seem to be able to see the CD in the CDROM drive. 

In your screenshot you have /media/cdrom0 for your D: drive. You should change the path to /dev/hdc and in "ShowAdvanced" you should choose the device Type CDROM.

/media/cdrom0 is a folder that you can mount the cdrom to but it's not actually the cdrom. I think the path /dev/hdc directly accesses the cdrom drive.

This didn't actually work for me, but I think it tells wine where the cdrom is, it might work for you.

What worked for me was using a NoCD crack on the installed game exe so I could play the game without the CD. I don't know the laws involved with using NoCD cracks but if you own the game it should be OK (I don't know for sure). 
Google for megagames, it has a large collection of NoCD cracks and it is a clean site, I haven't encountered any malware personnally.

---

### Post by leLune on 2007-02-21
Update:

Change /media/cdrom0 to CDROM in adv. settings run the game. Although, it's very choppy and there are sound/speed errors. 

Thank for all the help guys :KS

---

