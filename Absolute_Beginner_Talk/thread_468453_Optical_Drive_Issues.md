---
title: "Optical Drive Issues"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Volsfan91 on 2007-06-08
Hi guys, my third day using Ubuntu and I couldn't be happier.

The only thing that I'm having trouble with are my optical drives. The models of these drives are:

1) DVD Writer - Lite-On SOHW-1633s

**Under Windows:**
Rips DVD's, plays DVD's fine under VLC and others, can make ISO's of disc in drive. DVD burns usually result in coasters, CD burns always work fine. Doesn't work great and sometimes have to restart or reinsert the disc.

**Under Linux:**
I think I got most of the codecs, and still can't get it to do much of anything. Can't play DVD's in VLC, can't make ISO's of CD in drive (namely a PS1 game)

2) CD-ROM Drive - Asus CD-S480/AH

**Under Windows:**
Gets next to no use, but works fine for making ISO's of CD's.

**Under Linux:**
Works fine for playing audio CD's, can't make ISO's of CD in drives.

Methods I've tried for making ISO's of my PSX games:
*Graveman
*Nero Linux
*Alcohol120% under WINE
*Terminal [dd] (returns error)

At the advice of Google, I ran **"sudo dmesg"**. I was returned a great number of errors. If you want to see the entire log in order to help me fix it, let me know, but here's what I've picked out as perhaps telling:

[ 4314.228601] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 4314.228603] ide: failed opcode was: unknown
[ 4314.228901] hdc: error code: 0x70  sense_key: 0x05  asc: 0x21  ascq: 0x00
[ 4314.228904] end_request: I/O error, dev hdc, sector 4
[ 4314.230460] hdc: command error: status=0x51 { DriveReady SeekComplete Error }

[ 6522.275203] ACPI: Unable to turn cooling device [da772dec] 'on'

It prints that cooling device message a hundred or so times all the same.

Anyway, I'm still loving Linux, I just want to fix this one issue. Thanks a lot if you guys can help!

---

### Post by Volsfan91 on 2007-06-08
Bump. This place moves quick!

I never realized how much I could hate booting into Windows. :P Anyone got any clue? I'm willing to try whatever.

---

### Post by 67GTA on 2007-06-09
Not sure if this will help,but there is a section on using cdrdao to copy psx iso to hard drive. [http://www.linuxjournal.com/article/8851](http://www.linuxjournal.com/article/8851)

---

### Post by DBStevens on 2007-06-09
First install K3b.

Then insert a CD in your CD player and do a CD copy that is Tools Copy CD

Un select remove image and select image only then find out where K3b is goinf to put the iso image by clicking on the image tab. 

Write that location down.

Click on the options tab and press the start button.

The copy process should start.

After it finishes there should be an .iso in the location you wrote down.

Then you should be able to use that .iso to burn a cd.If that works try the same thing with a dvd only stop after you get the iso.

It is likely you won't be able to burn it unless your burner can handle a daul layer dvd.

Oh about those errors what are the /dev entries for both the CD  and the DVD devices.  In addition to that information are the jumpers on the optical drives set in the correct master/slave position for the ide chanel they are on?  

Good luck.

---

### Post by ramjet_1953 on 2007-06-09
Quite often, problems with CD and DVD ROM devices occur because of incorrect permission settings.

First, identify your drives. 

Quite often, if they are external, they will be identified as scsi devices. ie /dev/scd0.

Once that has been done, in a terminal give yourself read and write permission to these devices.

[COLOR="Red"]sudo chmod o+r+rw /dev/xxxx[/COLOR] (where xxxx is the ide or scsi device)

Regards,
Roger :cool:

---

### Post by diddler on 2007-06-10
Well, this is very confusing.  My optical drives are called hdc and hdd.  When I open the properties box, permissions tab, it tells me that both drives have read and write permissions for "Owner", "Group" and "Others".  So in theory, I should be able to write to them at any time, YET, when I try to drag and drop a file with a formatted DVD-RW in the drive, I still get the "You do not have permissions to write to this folder".  

Not only that, but it does not seem to really recognize a DVD-RW.  I have one folder on the disk but when I try to write another folder to it using CD/DVD creator. it asks me if I want to erase the existing folder (the only other option is to quit).  When I try to write to it using GnomeBaker (which I formatted the disk with), it immediately gives me a "write fail" message and throws the disk at me.

Any suggestions?

---

### Post by diddler on 2007-06-10
> **Volsfan91 said:**
> 
Anyway, I'm still loving Linux, I just want to fix this one issue. Thanks a lot if you guys can help!

Hate to rain on your parade, but this is only your CURRENT issue.  Believe me, more will arise.  But Linux is rather fun, isn't it (in a spend a lot of time and don't accomplish much kind of way)?

---

