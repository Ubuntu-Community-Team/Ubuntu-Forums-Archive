---
title: "Burning/ reading DVD again"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by topic58 on 2006-05-25
After problems burning DVD-R I tried burning it in K3b (after a tip). I set speed to Ignore. Burning was succesful. But I was not able to read the DVD in my cdrom. Then I tried it in my laptop with no problems, I was able to both open the DVD and read the files.
Then I tried this:
clabbe@desktop:~$ sudo mount /dev/cdrom /media/cdrom
Password:
mount: block /dev/cdrom is writeprotectected, mount as readable
clabbe@desktop:~$ cd /media/cdrom
clabbe@desktop:/media/cdrom$ ls
Death_of_the_Self.avi  Ice_station_zebra.avi  Independence_dayJ?vi
Hotet.avi              Identity.avi           Invasion_of_th?_Body_Snatchers.avi
(had to translate to english here while I'm using swedish language)
Now I was able to see what's on my DVD. But no chance of open a file or copy it to another partition.
Using Breezy now. Someone who got a clue here what I can do? The cdrom froze so I had to reboot to get the DVD out.
Maybe Dapper will be better in this than Breezy?
Perhaps an update of my firmware will help?

---

### Post by nalmeth on 2006-05-25
Just an offhand point, have you enabled DMA for your CD-ROM drive?
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)
Might help, might not.

---

### Post by topic58 on 2006-05-25
Tried that yesterday with no result.
clabbe@desktop:~$ sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
clabbe@desktop:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

---

### Post by nalmeth on 2006-05-25
Maybe the firmware will help, could be the drive.
Also Dapper may show improvement too.

I can't technically explain the behavior you're seeing.

---

### Post by topic58 on 2006-05-25
DMA is off in my laptop, despite that no problems in reading the DVD.

---

### Post by topic58 on 2006-05-25
Well, now i have updated my firmware on my cdrom burner to newest version. And I was also able to read the DVD I had problems in reading before. BUT - I also burnt a new DVD in K3b using speed Ignore. But I was not able to read it at all. Neither in my desktop, laptop or a friends windows XP. Despite that K3b says the burning was succesful. This says me my burner is okay, so I guess the problem is in Breezy. Will now try to install Dapper on a separate disc and try a new burning on that disc. Anyone who has a clue sofar??

---

### Post by topic58 on 2006-05-27
Hey, i got a big clue reading this thread:
[http://www.ubuntuforums.org/showthread.php?t=182300](http://www.ubuntuforums.org/showthread.php?t=182300)

in gconf-editor
/apps/nautilus-cd-burner
enable burnproof if you haven't... 
Thanks psylence :) 

Now Nautilus is working for me. I was burning in 6x. And I was able to open and read the DVD twice. :p  Great!

Read that this is a big problem in Dapper. And for me also in Breezy apparently.
I hope this can help out some of you out there.

---

### Post by topic58 on 2006-05-28
And I thought I was home free here, but no..
Got this message when trying to open a burnt DVD (automount didn't work)

clabbe@desktop:/home$ sudo mount /media/cdrom
Password:
mount: blockenhet /dev/hdc är skrivskyddad, monterar som endast läsbar
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and:

clabbe@desktop:/home$ dmesg | tail
[4472546.432000] Buffer I/O error on device hdc, logical block 8
[4472754.693000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4472754.693000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4472754.782000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4472754.782000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4472863.244000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4472863.244000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4472863.244000] ide: failed opcode was: unknown
[4472863.244000] end_request: I/O error, dev hdc, sector 64
[4472863.245000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

Someone who knows what's going on in my Ubuntu?? :confused:

---

### Post by topic58 on 2006-05-28
Does it matter what kind of files I burn? In this case I fail with xvid. And yesterdau no problems with jpeg. Both in Nautilus with burnproof, 6x.

---

### Post by topic58 on 2006-05-29
Getting so desperate here...
Can my DVD-burner be broken or what? Will try to check it out in XP. Just because I have to. 
No genius out there who can interpret my terminal?

---

