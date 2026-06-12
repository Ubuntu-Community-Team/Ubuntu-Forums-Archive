---
title: "Can Ubuntu help me get data off this HD from year 1994 ? ( attn: Old Timers !! )"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-26
[COLOR="Red"][B]Note:  THIS ISSUE HAS BEEN RESOLVED.

[/B][/COLOR]
Hello --

I have a Western Digital Caviar 31000 hard drive ... **[COLOR="RoyalBlue"]a mighty 1083.8 MB[/COLOR]** !!

It is from year 1994 and a relative has asked if I can get genealogical data off the drive.  It is of course IDE, and I've tried very hard to get Windoze to recognize this drive.  As a legacy device, I thought it would be as simple as plugging it in and Windows would recognize it.  Not so.  In googling around the web, I can see several others having this same issue.

I hope that linux will give me more control over accessing this drive.

Just to get some mechanics out of the way: This drive powers up fine, it sounds fine, it sounds and seemingly operates like every hard drive I have ever seen and heard operating normally.  So I know that power, and also I feel even mechanical functionality, are not the issue here.

[Here]("http://tinyurl.com/35gyxh") is a photo of the jumper situation for this drive:   ( [http://tinyurl.com/35gyxh](http://tinyurl.com/35gyxh) )  I believe that I should put the jumper in the 'middle column of pins' in order to make it slave in the system described in the next paragraph.  (I tired various jumper configurations with Windows, and although BIOS found the drive, Windows could not - no matter what jumper config I tried.)

The system into which it will be placed operating on Xubuntu beautifully.  It is a Compaq Presario 7470 ... AMD-K6 533 MHz ... 512MB PC100 SDRAM ... 1 master 20GB HD ... dual-booting Win 2000 Pro and Xubuntu with ntfs-3g, every partition is mounted in linux and writeable and OK.

So I am wondering -- I don't know *why* myself and others have trouble getting this hard drive to show up in Windows, but do you think linux can help?

Any thoughts, tips, clarification of my (mis)(understanding) greatly appreciated !!

---

### Post by Detonate on 2007-06-26
Does your BIOS recognize it?  If so, you could try a Windows ME boot floppy disk.  See if you can get to it that way.  Then if you have a FAT32 partition you could copy the files there.  Maybe. Big maybe.

---

### Post by dfreer on 2007-06-26
So it uses Master, Slave, and Cable Select? why not try putting the jumper on cable select? on an IDE cable , there are three plugs. one end goes to mobo, one end goes to the Master drive, and the plug in the middle is always slave. If you have another drive on this same cable, it needs to be in cable select position as well.
Or you could just set the jumper on the master drive to master and the slave drive to slave. it just needs to be either Master/Slave or Both Cable Select.

Beyond that, does linux have problems recognizing it? if so, what is the output of dmesg?

EDIT: really though, 1994 isn't THAT old lol. it should be recognized exactly like any modern day 320 GB IDE drive. problem is whether the data is still intact... ;)

---

### Post by Chilli Bob on 2007-06-26
IF you can download and burn a Knoppix Live CD, that will probably be able to read it.

---

### Post by confused57 on 2007-06-26
If you get your jumper settings correct and Xubuntu recognizes the drive, maybe you can mount the drive, then recover the files:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

---

### Post by totheresq001 on 2007-06-26
Hi

I have a computer repair business and frequently recover data from customers drives with Knoppix.  If you set up the drive you want the files from as a slave, boot from a knoppix cd.   Try this link
[http://www.shockfamily.net/cedric/knoppix/](http://www.shockfamily.net/cedric/knoppix/)
it should help

---

### Post by Detonate on 2007-06-26
The hard drive he is trying to recover files from is probably formatted using FAT16.  Will Knoppix be able to read that?

---

### Post by Ozitraveller on 2007-06-26
This might help too

DOS Formatted Disks
[http://www.linux.com/base/ldp/howto/Jaz-Drive-HOWTO-4.htmlt](http://www.linux.com/base/ldp/howto/Jaz-Drive-HOWTO-4.htmlt)

---

### Post by Average_Joe on 2007-06-27
Thanks to all for the help.

I was able to use the Cable Select + Cable Select and the IDE cable appropriately hooked,
and using the Knoppix LiveCD was able to go in to the 1083.8 MB hard drive and remove
the data.

I really appreciate the help!

---

