---
title: "[SOLVED] How about that: Listen to a DVD, eject it, re-insert it: DVDs not working an"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-02-23
That's exactly what happened to me minutes ago.

I was listening to a DVD. Stopped it. Ejected it. I put a CD in the drive. Listened to one song. Ejected it. Put the same DVD back in: Nothing. My DVD drive is in the file system, but I can't "mount" the DVD disk in it. According to Ubuntu, there's no DVD in the drive. What a joke, hey, it's **there**, and it's **turning**. But I can't seem to "wake up" Ubuntu. I've put another CD in the drive, and it works. But only with CDs. Tried 2 different DVDs = nothing. DVDs aren't mounting. Even Brasero tells me that there is **NO** DVD in the drive, either when I put a bought DVD in, or a DVD+RW.

Looks like, for somewhat obscure reason, something, somewhere, and above all, **silently**, broke.
So if anyone knows any way to "repair" this, tell me.

And please do NOT tell me to reboot. I obviously do NOT want to reboot after every DVD change when i'm using ubuntu.

---

### Post by SpiderGorilla on 2008-02-23
Alright, first off, this sounds like you do unfortunately need a reboot. If you don't want to go all the way down and back, you can try restarting X and see if that does anything, but honestly this is probably a much deeper issue that will require a restart.

To restart X, hit CTRL-ALT-BACKSPACE. It'll save your current sessions (make SURE you save all of your files, first, before even attempting that because it'll be immediate and you'll lose all unsaved work) of open windows and such.

There are a number of things that could've caused this to happen, and there's no way to tell if this is a one-off problem or a real problem without a reboot. At least, no way to tell without a lot of dark and devious things done in the terminal that could cause you many many problems with your installation.

---

### Post by Mick8882003 on 2008-02-23
How long u had ubuntu on the system, had any trouble before?

---

### Post by LeDechaine on 2008-02-23
Hmm, 2 or 3 days ago my CDs wouldn't play, but this have ben "magically" solved..
Had a total system freeze while inserting a DVD in the drive, too, obligating me to reboot the machine.. But this was a CSS-Encrypted DVD and I had not installed libdvdcss yet..

Installed **libdvdcss** from here: [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)
And everything worked fine after.. For two DVDs. I put the second DVD back in and since then, no DVDs are "detected".

*Ctrl+alt+backspace* now...

---

### Post by LeDechaine on 2008-02-23
Well... ctrl+alt+backspace and re-logging in haven't solved the problem..
I was reluctant to reboot the computer since the main reason why I installed linux is that I wouldn't have to restart, which is, in windows, "the magic solution to solve all problems", but anyway, did it because I had no clue how to solve this problem...

...But even rebooting haven't solved anything. **Looks like Ubuntu killed it's own DVD playback mechanism.**

My CD/DVD player is an *HL-DT-ST DVDRAM GSA-4160B*, maybe this is the problem, don't know. It always worked flawlessly under windows, tought.

So, come on, send me the commands, I want to solve this. :P

*(Ah, also note that in the filesystem, Ubuntu *still* tells me that this drive is a CD-RW and DVD+RW/DVD-RW drive.)*

---

### Post by LeDechaine on 2008-02-24
Commented this as a bug... [https://bugs.launchpad.net/ubuntu/+bug/16351](https://bugs.launchpad.net/ubuntu/+bug/16351)

If anyone can still help anyway, let's go. ;)

---

### Post by LeDechaine on 2008-02-27
Any ideas? I don't want to wait until Heron to play DVDs on my computer...

---

### Post by LeDechaine on 2008-03-18
Nevermind, the CD/DVD drive is scrapped now (nothing works under XP/Ubuntu and the Ubuntu LiveCD on boot doesn't works too)..

Weird coincidence that it scrapped just after installing libdvdcss, when everything was finally working right, though..
(And that the CDs were playing..!)

---

