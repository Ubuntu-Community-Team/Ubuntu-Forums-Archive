---
title: "Slow CDROM Drive, Speed Up Thoughts (quick question for the right person)"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by mlissner on 2007-01-09
Hello, quick question: the instructions that are on ubuntuguide.org about speeding up your CDROM, are those safe and reversible? I don't really know what they do, but I do know my CDROM is slow...I try not to mess with hardware these days unless I know what I'm doing...

The instructions are these:
> 
How to speed up CD/DVD-ROM
  * Read #General Notes 
  e.g. Assumed that /dev/cdrom is the location of CD/DVD-ROM 
```
sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
gksudo gedit /etc/hdparm.conf
```

  * Append the following lines at the end of file 
```
/dev/cdrom {
    dma = on
}
```

Here's the link in case you're curious:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM)

Thanks.

---

### Post by deadgobby on 2007-01-09
It is safe. The reason why the instructions is haven you make a back up file. If it fails to do what you want. You can go back and edit the from the old settings.
Gobby

---

### Post by mlissner on 2007-01-09
OK. I gave it a go, and I discovered that it wasn't meant to be:
```
sudo hdparm -d1 /dev/cdrom
HDIO_SET_DMA failed: Function not implemented
```

Any ideas? My CDROM is supposed to go to 52X, but it just took me 50 minutes to copy a DVD at 2.5X (according to gnome baker).

Thanks.

---

### Post by deadgobby on 2007-01-09
Depending how big the file is and other things. Like ram. It may take that long. I use K3B my self. It may take time to copy from the file.
Gobby

---

### Post by Johan! on 2007-01-09
Try
```
 ls -l /dev/cdrom 
```
This will return a line like this on my system:
lrwxrwxrwx 1 root root 3 2007-01-06 10:06 /dev/cdrom -> hdd

So this tells you that /dev/cdrom is linked to /dev/hdd (on my system, your system may be different)
Then try the sudo hdparm command again, and substitute /dev/cdrom by /dev/hdd

I don't know if it's important, but I have a /dev/cdrom entry, and a /dev/cdrw entry.
Try them both, if you have 2 entries.

---

### Post by mlissner on 2007-01-09
I also have a /dev/cdrom and a /dev/cdrw entry, though I get the same error as I mentioned above when I try the hdparm on them. 

Does this mean I need to figure out how to turn on this function? Is there another way to speed it up?

---

### Post by mlissner on 2007-01-09
I guess I should probably also mention that I'm having a bit of a kernel problem. I mentioned this elsewhere (and got ZERO responses), but it could have something to do with this, so here it is again. 

Since I installed edgy (through an upgrade), my kern.log has the following bad errors, and my system freezes for about 30 seconds at a time every ~2-50 minutes. It's driving me absolutely crazy, and I will HAVE to install something else if I can't get this freezing problem fixed, which would be a terrible waste. I'm not saying Windows or Mac, but I would have to leave Ubuntu for something else...Fedora? Noooo...Fedora didn't support my wireless card. Who knows. Recommendations at this point? 

Anyway, here're the errors:
```
[17189890.432000] ata2 is slow to respond, please be patient
[17189915.408000] ata2 failed to respond (30 secs)
[17189915.416000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17189915.416000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
```
Do these mean anything to anybody, or have anything to do with my CDROM? I need help, and nobody seems to know anything about these. Also, if you don't know anything about these, do you know how to go about finding out about them? The internet seems to be pretty deaf to them.

Thanks. Hope my depressing message hasn't been too off-putting, but I don't look forward to installing something else and I will have to if I can't figure out how to fix that problem.

Thanks

---

### Post by noenter1 on 2007-01-10
For troubleshooting purposes you may want to try another hard drive/optical drive to see if you get those errors. It sounds to me like its you hard drive tho it may be both or could be your drivers for your hard drive. Also if your bios has smart hard drive monitoring enable/disable it and see if either one works. Thats all i can think of hope it helps.

---

### Post by mlissner on 2007-01-15
OK, sorry for the delay, but I wanted to make sure that I had tested thoroughly before reporting back. 

I disabled SMART hard drive monitoring in the BIOS, which sounds like a good thing to have enabled, and the problems with the freeze-up seem to be greatly lessened. They still there from time to time, and I'd love to know why, but I'll start another thread about that if the problem persists.

Now, about the CDROM drive...it's still very slow. Help?

---

### Post by mlissner on 2007-01-21
I hate to do this, but bumity.

Also, the HD problems persist and my CDROM is NOT operating at 52X.

---

### Post by KAL9000 on 2007-02-18
well if you have a 52x CD rom drive that doesntmean you can reada DVD as that speed. check your documentation, the disk's spin slower for DVD's

The writers have 52x24x12 meaning 52x read 24x write and 12x rewrite, DVD combo drives have the same. 
also dont forget that a DVD is typicaly 6GB+ so you're not going to rip it in 90 seconds like most CD's can.

---

