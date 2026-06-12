---
title: "Ubuntu hangs when copying files"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by chloraldo on 2006-04-12
I'm trying to copy mp3 files from an external USB drive to an internal harddisk. I get the message "*Copying file: 168 of 4666 (10:33:22 Remaining)*" for hours. The time changes every few seconds, but it's always 168 of 4666.

If I click cancel nothing changes...

What should I do? How kill the copying? How copy the files?

-- 
Thanks
chloraldo

---

### Post by taurus on 2006-04-12
Instead of copying all 4666 (!!!) songs all at once, try copying them in a small batch!  Also, how did you copy them, with nautilus (or any other GUI) or did you do it from a command line (a terminal)?  Also, make sure you have enough space on your harddrive to copy them over!

---

### Post by chloraldo on 2006-04-12
> **taurus]Instead of copying all 4666 (!!!) songs all at once, try copying them in a small batch![/QUOTE] 
That's what I was doing!  said:**
> Also, how did you copy them, with nautilus (or any other GUI) or did you do it from a command line (a terminal)?
I used nautilus. Does that make a difference? Would it be better in a terminal?

I tried to add the files from the external disk to my amaroK collection and that stopped aswell...

BTW, it's an NTFS USB-disk

---

### Post by taurus on 2006-04-12
Yes, try copying them in a terminal as Applications -> Accessories -> Terminal.

---

### Post by chloraldo on 2006-04-12
[QUOTE=taurus]Yes, try copying them in a terminal as Applications -> Accessories -> Terminal.[/QUOTE]
I tried, but it still doesn't work. Stops after 174 files :(

---

### Post by Mustard on 2006-04-12
[QUOTE=chloraldo]I tried, but it still doesn't work. Stops after 174 files :([/QUOTE]

Interesting.  I'm quite curious what it going on with this situation.  I wonder whether it's too many files for the file argument, or some type of problem with space in the root filesystem.

What's the command you are using atm, from command line?

Is it possible for you to watch the disk space while the process is going on?

---

### Post by taurus on 2006-04-12
That was one of my questions in the original post!  What is the output of this from a terminal then...
```

df -h

```

---

### Post by chloraldo on 2006-04-12
[QUOTE=chloraldo]I tried, but it still doesn't work. Stops after 174 files :([/QUOTE]
Now I copied the files from windows (another PC) from that USB disk to another USB disk: No problem. Then I copied them from the "new" USB disk to the ubuntu machine... that seems to work!

Was probably a problem with the disk...

---

### Post by krusbjorn on 2006-04-12
I've had this problem a few times, and it has always been due to physical damage to the disks.

---

### Post by Hiew on 2006-04-12
I've had a problem similar to this however it was copying large amounts of music files from a DVD disc and onto a SATA drive (120 GB) it copies the files fast however it made both the gnome and KDE environments (whichever i tried to run) REALLY slow and lags the system. However i havn't tried to use a console to copy yet...

---

### Post by Tom Tiger on 2006-05-21
I'm having a similar problem,  which oddly enough didn't occur at first on my 5.10.  If I write to my USB harddisk it works perfectly,  however if I read from the drive. It is awfully slow.  At first I thought it was the drive but when I hooked it up to my laptop (like my desktop a 2.0 usb) there were no problems.

At the moment I'm a bit stumped.... flashdrives don't have this problem, just my usb harddisk.  I'll get another drive and see what it does.....

---

