---
title: "Triple Boot Fiasco"
date: 2009-02-24
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2009-02-24
So I've done the triple boot before (Mac OS X, Win XP and Ubuntu), on more than one occasion. Or rather, I tried to be overly thorough when I first did it, and wound up reformatting a billion times. Anyways, so I had to do it once again, and now suddenly, my disks aren't showing up in Mac OS X. I've got the two HFS+ disks showing up (one is a music partition), but my NTFS and ext3 partitions aren't mounting (and refuse to mount in Disk Utility....the old "Repair your disk" routine).

Any thoughts?

Oh, and in case it makes a difference, I'm running a first gen MBP 15". I'm pretty sure this happened to me the first time I triple booted (the FIRST first time), but I'll be a monkey's uncle if I can remember how I fixed the issue.

---

### Post by Tu1J4kXk8NUhMz on 2009-02-25
bump

---

### Post by Tu1J4kXk8NUhMz on 2009-02-26
Help please.

UPDATE: I somehow got my ntfs up and running (er, mounted) but now my ext3 drive won't mount in OS X!

UPDATED UPDATE: I've tried uninstalling, restarting, reinstalling and restarting (which I remembered worked last time) and that didn't work. I then checked the extFSmanager component in System Preferences. When I try to mount it in here, it gives me the following error:

```
Command: Mount
Device: disk0s3
Message: Unknown Error (The filesystem may need repair. Please use Disk Utility to check the filesystem.)
Error: 0xC047
```

And so, in spite of knowing it won't work, I go into Disk Utility and get this message when I try to Verify and Repair (respectively) my ext3 partition:

```
Verifying volume “UNTITLED”
/sbin/fsck_ext2: open '/dev/disk0s3' failed, Resource busy
Error: Filesystem verify or repair failed.
Verify and Repair volume “UNTITLED”
e2fsck 1.39 (29-May-2006)
/usr/local/sbin/e2fsck: Resource busy while trying to open /dev/disk0s3
Filesystem mounted or opened exclusively by another program?
Error: Filesystem verify or repair failed.
```

No clue how this could be the case, as nothing's using the disk and when I shut down Ibex, I shut it down fully (no errors or anything).

Although...is the final screen before shut down supposed to be red with white boxes on it? This struck me as odd, but I figured this was normal because even the Live CD did this...

---

### Post by cyberdork33 on 2009-02-27
why are you trying to repair a linux file system from within OSX... boot a Linux LiveCD and use fsck.

If you had an ext3 filesystem mounting in OSX previously, then you were lucky. That driver is old, no longer developed, and buggy.

---

### Post by Tu1J4kXk8NUhMz on 2009-02-28
> **cyberdork33 said:**
> why are you trying to repair a linux file system from within OSX... boot a Linux LiveCD and use fsck.

If you had an ext3 filesystem mounting in OSX previously, then you were lucky. That driver is old, no longer developed, and buggy.

To be honest, I didn't expect Disk Utility to do anything aside from say it couldn't do anything. The reason I ran Verify and Repair was to see what issues Mac OS was having with my partition. As I pointed out, my Ubuntu partition is quite new, so I didn't suspect any filesystem errors or anything like that. But I tried fsck, and got nothing :(
(I suppose no errors is actually a good thing, but I wanna fix the problem after all...)

It's been a while since I've been a regular on the forums, but I seem to remember several users having mild success with the ext2fs driver mounting ext3 (by mild success, I mean it was mounted read-only...which is all I need really). Is there a more viable option as far as the driver goes? I assume no, but haven't looked into it.

One thing I seem to remember was that the last time I got this to work, I started with an ext2 then added journaling later. Might this work?

---

### Post by cyberdork33 on 2009-02-28
> **teamjh14 said:**
> One thing I seem to remember was that the last time I got this to work, I started with an ext2 then added journaling later. Might this work?
an ext2 fs will probably work better, but I don't know why adding the journaling later would make a difference (but if it works, it works).

---

### Post by Tu1J4kXk8NUhMz on 2009-02-28
> **cyberdork33 said:**
> an ext2 fs will probably work better, but I don't know why adding the journaling later would make a difference (but if it works, it works).

I remember having quite a few issues with ext2, in that the OS would have to constantly run fsck (usually for the typical reasons, it was scheduled, what have you...but also sometimes for no particular reason at all). Is Ibex better about this?

Or perhaps do you suggest just not mounting that partition in Mac OS X to avoid all the bugginess/potential problems? It seems perfectly reasonable to have Ubuntu be the conduit to move files to/from Mac OS X, and not the other way around, due to the issues with using the ext2fs driver.

While having my Ubuntu partition mounted in OSX would be handy, it doesn't seem worth all the trouble and potential hazard.

---

### Post by cyberdork33 on 2009-02-28
I'd say that you are  likely to have the same thing in Intrepid with ext2. Of course, Jaunty will be coming out next month. You might be mreo worried about that :)

I use a FAT32 partition on an external hard drive to move files, or a network share. Mounting OS X's HFS+ in Ubuntu is no laughing matter either. (Well, mounting it read/write anyway).

---

### Post by Tu1J4kXk8NUhMz on 2009-02-28
> **cyberdork33 said:**
> I'd say that you are  likely to have the same thing in Intrepid with ext2. Of course, Jaunty will be coming out next month. You might be mreo worried about that :)

I use a FAT32 partition on an external hard drive to move files, or a network share. Mounting OS X's HFS+ in Ubuntu is no laughing matter either. (Well, mounting it read/write anyway).

Aw man! I just installed Intrepid!

Thanks for the suggestion on the external hard drive. I think I'll just do something to that effect.

As always, you have been a great help, Cyber!

---

### Post by Michel66 on 2009-03-06
Hi,

I've spent a lot of time on this forum, googleing but still no answer to my problem.

Okay. I have a Mac Pro with 4 drives.  First one with Leopard, second and third with photos and the last, well I used to have Windows XP and Ubuntu through Wubi but got tired with connection speed, so I decided to install Ubuntu and XP on separate partitions.

The XP partition was backed-up.  So I can always go back to my old setup but this is not my plan.  I want this to work.

So with Disk Util on OS X I formatted the 4th drive and created two partitions using FAT32 - first called Ubuntu, second XP.

I installed XP using my backed-up install through Winclone first on the third partition i.e. the last (EFI being the first).  Booted from it without problem.

Then I've installed Ubuntu 8.10 on the second partition.  Oh yeah, I've been using rEFIt for awhile to pick boot when starting my machine.

I had to do some tweak to get Ubuntu to run on its own but finally got it to work.  BUT now I can't access XP anymore!

For my Ubuntu install I followed the steps:
 
* Use manual partition and installed on the second (disk2s2) at “/” .
* The installer then indicated “GRUB will be installed to (hd0)”, but picked at step 6 (if I remember well) to install GRUB on sdd2 (/dev/sdd2) instead of the entire hard drive.
* Rebooted

Unbuntu was up and running.

I've checked the menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd3
title		Microsoft Windows XP Professionnel
root		(hd3,1)
savedefault
map             (hd3) (hd0)
map		(hd0) (hd3)
chainloader	+1

When I boot to XP from GRUB I get this error message:

Error 13: Invalid or unsupported executable format

But I've noticed that when I boot to Ubuntu it says Boot from (hd0,1)

What am I missing here?

Thanks

---

### Post by cyberdork33 on 2009-03-06
> **Michel66 said:**
> But I've noticed that when I boot to Ubuntu it says Boot from (hd0,1)

What am I missing here?

Thanks
when you have multiple hard drives on a Mac, whichever drive you run the bootloader from is seen as the primary hard drive. It is just how the Mac works. For this reason, you need to make any needed changes to make grub point to (hd0,x) rather than what you'd expect.

---

