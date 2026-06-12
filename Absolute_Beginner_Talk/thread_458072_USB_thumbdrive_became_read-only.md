---
title: "USB thumbdrive became read-only"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by seetho on 2007-05-29
I have a 1GB Jetflash USB thumbdrive that I normally use to transfer files back and forth different computers.  It has been working all the time, but just this evening when I plugged it into my Dapper notebook and tried to remove some unwanted files it told me that the thumbdrive is read-only.  I could not even delete files which i copied in earlier.  I checked the drive properties and found that I am indeed still the owner and that I have read and write permissions.  Umounting - removing - reinserting it several times did not change anything.

At last I had to resort to:

```
sudo mkdosfs -F 32 -n myusb /dev/sda1
```

to clear out everything and restore it to a useable state.  No problems here.

My questions are:

USB thumbdrives are usually FAT32 formatted devices, could it possibly have owner information on it?

What could possibly cause it to behave this way?  The only thing I could think of is inserting it into a WinXP machine and copying some files into it.

Could this be a bug?

I'm just curious, so if ou happen to know anything about this please let me know.  Thanks.

---

### Post by BHelts on 2007-05-29
flash drives have limited write lives, meaning they have a finite amount of writes before they go bad.  perhaps you've run out?

---

### Post by seetho on 2007-05-29
That of course possible, but the tumbdrive is rather new.  Is it possible that Ubuntu detects a bad file system and mounts it as read-only?

---

### Post by smoker on 2007-05-29
have you been removing it properly in windows by clicking usb icon in taskbar, and 'remove device safely' (i think it's worded), i know an improper removal can fubar the file system, i also always unmount usb before removal in linux.

just a thought!

---

### Post by seetho on 2007-05-29
> **smoker said:**
> i also always unmount usb before removal in linux.

Yes I always do that, and on Windows too.  Have you noticed on Linux after you umounted the led on the thumbdrive is still on whereas on windows the led is off as soon as it is safe to remove.

I alway wonder whether it was really safe to remove in Linux, but so far I had no problems (until now).

---

### Post by smoker on 2007-05-29
> I alway wonder whether it was really safe to remove in Linux, but so far I had no problems (until now).

as far as i am aware, as long as the usb is unmounted it should be safe to remove, i believe you will get a warning it cannot unmount if the drive is still being written or read from. yes, the light remains on, but isn't flashing as in being accessed. the only time i ever 'broke' a usb flash drive was using windows!

---

### Post by smoker on 2007-05-29
hi, have a look at this post and see if it has any relevance to your current problem:
[http://ubuntuforums.org/showthread.php?t=445328&highlight=usb+write+access](http://ubuntuforums.org/showthread.php?t=445328&highlight=usb+write+access)

---

### Post by seetho on 2007-05-29
So I guess it was that time that I needed to use it on a windows PC that killed it.  I rarely use Windows nowadays but at work everyone else is not so....(shall we say) enlightened yet.

Thanks for the replies everyone.

---

### Post by seetho on 2007-05-29
For anyone interested in the information, I found out what was actually causing the thumbdrive to corrupt.  It was my new Samsung CLX-3160 MFP.  It has scan to usb feature which I have to use since scanning over tcp/ip does not work under linux yet (I can only print).

So every time I put in the thumdrive into the mfp's usb slot and do some scanning it stops playing nice with Ubuntu.  The scanned files on the device copies out fine but Ubuntu sometimes is unable to delete files or even to eject the device.

It doesn't help that there is no 'eject' or 'umount' feature on the printer/scanner to make sure that the usb device is safely removed.

:redface: p.s. I was too quick to blame Windows for it.  My mistake.

---

