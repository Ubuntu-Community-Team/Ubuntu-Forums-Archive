---
title: "Mounting and reading a floppy."
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by catgate on 2006-04-22
I have down loaded (using W98SE for obvious reasons) a couple of linux files (DSL modem stuff). But when I try to get at them, on Breezy Badger, I get no co-operation at all. Despite "floppy0" having a presence in "media", it will not mount. Could the fact that it has been contaminated by Bill Gates rubbish have any bearing on the matter. What should I do to mount and read these files, please? The files are *.rpm and *.tar.gz.

---

### Post by ruzle0 on 2006-04-22
if you type 'mount /media/floppy0' at a prompt it should be accessible and later umount /media/floppy0' when you're finished with the disk.
you can also do this through gnome in  PLACES->COMPUTER then right click oon floppy and select mount / unmount

if that doesn't work post file /etc/fstab

---

### Post by catgate on 2006-04-22
Thanks for that ruzel0,

[QUOTE=ruzle0]if you type 'mount /media/floppy0' at a prompt it should be accessible and later umount /media/floppy0' when you're finished with the disk.[/QUOTE]

I had already tried that, without much/any success.
I will try the following :-
> you can also do this through gnome in  PLACES->COMPUTER then right click oon floppy and select mount / unmount
and then :-

> if that doesn't work post file /etc/fstab

---

### Post by catgate on 2006-04-22
Well I tried the PLACES>COMPUTER route and all I got was the same message that it was "unable to mount", so I went into /etc/fstab. I am unable to cut and paste because I am working on two different machines. This one is on W98SE and the other is obviously on Ubuntu. But what it says is as follows:-

#/etc/sftab: static file system information
<file system>< mount point> <type> <options> <dumps> <pass>
proc            /proc              proc      defaults    0          0
/dev/hda1    /                   ext3       defaults,errors=remount ro  0   1
/dev/hda5     non               swap      sw            0         0
/devhdc      /media/cdrom0  udf,iso9660,user,no auto  0   0
/dev/fd0     / media/floppy0  auto     rw,user,noauto   0    0

 It looks to me, from my base of infinite ignorance, as though it might be what one would expect...but then ...what do I know about the price of fish????

---

### Post by ruzle0 on 2006-04-22
the options for the floppy look ok, i'm assuming there is a space and not a comma between iso9660 and user on the /dev/hdc line. also check that the last line of the fstab is an empty line as that can cause problems if its not.

does the cdrom drive work ok under linux too? when you try to mount the floppy do you get any error messages with 'dmesg' command

---

### Post by ruzle0 on 2006-04-22
if none of that sorts you, are you sure the floppy disk drive works ok, are you using the same computer as a dual boot or used it recently when another os was on it?
you can try mounting from the command line with
sudo mount -orw,user,noauto /dev/fd0 /media/floppy0
to see if the problem is with fstab, the files will all belong to root but you get them onto the computer
if it is a dual boot you can solve the immediate problem of transfering the files by mounting the windows partition, and play with the floppy drive after.
another thing to try is on a live cd if you have one handy, other floppy disks(freshly formatted if pos) etc. and see if anything changes to make sure if its a hardware or software fault.

---

### Post by Lord_Drakkus on 2006-04-22
> 
/dev/fd0     / media/floppy0  auto     rw,user,noauto   0    0


Well, I do notice one thing that's obviously incorrect and will cause a problem.  There shouldn't be a space between the "/" and "media"...  If that's really in the file, remove the space and that may fix it.

---

### Post by catgate on 2006-04-23
The contents of /etc/fstab as shown above were not "exactly" as shown in the file due to the fact that despite typing them on this message board panel with spaces the message board compacted everything when I pushed the "send" button.

---

