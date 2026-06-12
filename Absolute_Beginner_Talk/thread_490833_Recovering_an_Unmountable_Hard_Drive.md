---
title: "Recovering an Unmountable Hard Drive"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Goldsun1715 on 2007-07-02
I was recently running Windows XP when it started to become unable to boot. I believe my hard drive is corrupted, and I have a back up external drive connected via USB. I'm able to boot Ubuntu via disk, and when I try to mount my primary 300GB drive it gives me an error:
[Picture Here]("http://img154.imageshack.us/img154/8731/screenshotav8.png")

I have minimal Linux experience. I'm only slightly familiar with Window's Command Prompt.

I only need to back up my 300GB corrupted unmountable drive to my 500GB USB external hard drive.

Thanks,
Gold

---

### Post by Tsen on 2007-07-02
Well, first off, you might want to give Knoppix a try.  You said you're inexperienced with Linux, though, so chances are you won't get any further with it, but it has superior rescue tools (because, well, that's what it was designed for).

Anyway, first thing I'd do is try to run in a command prompt: 
```
fixntfs sda1
```
See if that gets you anywhere.  If it does, great!  Most likely, though, it'll give you an error of some sort.
Now, i'm assuming you have a Windows CD somewhere.  Find it, put it in the drive and boot from the CD.  Go to Recovery Mode or Safe Mode w/ Command Prompt.  I'm not entirely familiar with the layout of the boot menus for Windows, but poke around a bit (whatever you do, do NOT format the drive--then you'll lose all the data).
Anyway, when you get to a Windows command line, use:
```
chkdsk C: -r -x
```
This should check the disk for errors and bad blocks, and recover what it can.

Now, if these don't work, don't give up hope--recovering data is often a series of shots in the dark to probe for the problem before you can actually find a method to fix it.  Try that, though, and post back.

---

### Post by rillip on 2007-07-02
If the disk isn't able to load Windows, I'm not suprised it can't be mounted either.  I would recommend running the chkdsk as recommended above and trying again.  You might be able to boot normally then or if not possibly mount it.

---

### Post by wolfen69 on 2007-07-02
just use knoppix or sabayon live cd. they will automount all drives.

---

### Post by Ocxic on 2007-07-03
it's possible it;s the drive itself, if it is... i know this'll soud wierd but it works,
place the drive in a zip-lock, bag and place in freezer for 1-2 hours, then remove from freezer, and replace in computer quikly, and boot up your comp, ans see if you can mount the drive, if it works get all the data you can off as fast a possble... b4 the drive dies again... this may only work 2-3 times if that, but it does work.

---

### Post by Tsen on 2007-07-03
Oops, just realized--that chkdsk command is wrong.  Should be:
```
chkdsk C: /r /x
```
Windows does flags differently from Linux.

---

