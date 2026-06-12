---
title: "Problems after installing ntfs-3g"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by NorvilleBarnes on 2007-04-02
When I installed Ubuntu several days ago, my external hard drive (actually an internal in a case) was read only and I couldn't change it to Read and Write. First, I tried using the ArsGeek manual here: [http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675). But even after following all the directions, my HD wasn't switching to Write. So I tried givre's tutorial "HOWTO: NTFS with read/write support using ntfs-3g (easy and safe method)". It installed correctly, I can open it under Applications and no error message appears. After, though, my HD stopped opening, giving me 

> $logfile indicates unclean shutdown (0, 0)

failed to mount '/dev/sda1': operation not supported

mount is denied because ntfs logfile is unclean. choose one action:

   boot windows and shutdown it cleanly, or if you have a removable

   device then click the 'safely remove hardware' icon in the windows

   taskbar notification area before disconnecting it.

or

   run 'ntfsfix' on linux unless you have vista, then mount ntfs with

   the 'force' option read-write, or with the 'ro' option read-only.

or

   mount the ntfs volume with the 'ro' option in read-only mode.

error: could not execute pmount


I run NTFSFIX on /dev/sda1 and I get this:

> 

Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr... 
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... FAILED
Error setting volume flags.


Any ideas?

---

### Post by NorvilleBarnes on 2007-04-02
Bump

---

### Post by szaka on 2007-04-03
Install ntfsprogs 1.13.1 and run ntfsfix. You have an old, broken version. Ntfs-3g will support uncleanly detached devices only from the next stable release, in about a 1-2 weeks.

---

### Post by NorvilleBarnes on 2007-04-03
Ok, I did all that, and now it looks like the hard drive is working fine:
> 
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.


But now I get this when I try to actually open the drive:
> volume is scheduled for check.

please boot into windows twice, or use the 'force' mount option.

error: could not execute pmount



Thanks for the tip on the ntfsprogs update, I never would've figured that out on my own.

---

### Post by NorvilleBarnes on 2007-04-03
Here is my fstab, maybe there's something wrong there.

> proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=0c011467-8ab5-4585-9ac6-17e1ac64d3de / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=8ba1b061-d224-4a83-8209-7f24d2083caf none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs-3g defaults,user,nls=utf8,umask=007,gid=46 0 1


I've looked all over the internet for a solution to this, and I can't find anything.

---

### Post by szaka on 2007-04-03
> **NorvilleBarnes said:**
> I've looked all over the internet for a solution to this, and I can't find anything.
That's very strange because when I typed into google search "ntfs-3g how to use the 'force' mount option" then the first hit explained how to do it: [http://forum.ntfs-3g.org/viewtopic.php?p=1398](http://forum.ntfs-3g.org/viewtopic.php?p=1398)

You also use an old version of ntfs-3g. Here is the output of the latest stable in the same situation:
```

Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sda1 /media/windows -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sda1 /media/windows  ntfs-3g defaults,force 0 0

```
I hope this helps.

---

### Post by NorvilleBarnes on 2007-04-04
Szaka, you're a star in my eyes. > 

That's very strange because when I typed into google search "ntfs-3g how to use the 'force' mount option" then the first hit explained how to do it:

Yeah, well.......I wish I had a good excuse for not finding this.

One last question, though: am I going to have to do this every time I want it mounted? I' m almost afraid to turn it off.

---

### Post by szaka on 2007-04-04
You must do it only when the external disk was detached incorrectly from Windows. Microsoft has instructions how to do it correctly (ntfs-3g explains only shortly how it's possible in the error message).

---

