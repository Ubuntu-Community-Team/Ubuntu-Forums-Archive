---
title: "Check Forced"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Snoo on 2007-07-08
"SDA 4 has been started 31 times without check - check forced"


Or words to that effect. Why does this keep happening? Ubuntu is always shut down properly? I regularly get the firefox "restore last session message" too and I don't know why. Any ideas?

---

### Post by mikewhatever on 2007-07-08
> SDA 4 has been started 31 times without check - check forced
SDA4 must be your root partition, so it is checked for integrity every 30 reboots. That is normal, in case you were worried.
> I regularly get the firefox "restore last session message" too and I don't know why
Firefox must be closed before the shut down, otherwise it appears to have force quit, hence the message you get.

---

### Post by NeghVar on 2007-07-08
The Force Check happens after so many boots regardless of whether it was shut down properly, it is just designed to ensure your Hard Drive is always working properly and your files are intact.

As for the Firefox issue, there are a few possibilities I can think of,

do you ever have it freeze and have to force it to quit?

there is also an extension I remember, I'm not sure what it is called but it gives you the option of saving a session so you can restore it, is it possible this is installed?

---

### Post by ggaaron on 2007-07-08
Firefox - maybe you log our without closing it, it is killed instead of shutting down.

Disks - it's normal, disks are checked for errors about every 30 times they are mounted, you can use tune2fs to postpone check or turn it off.

---

### Post by Skidpad on 2007-07-08
This is normal, and is the equivalent of XP's Disk Check.  You can change the default setting (30 I think), or there are add-on programs to monitor when Ubuntu is going to perform this check.  I use "Bonager" for this.  It put a little icon in my system tray allowing me to instantly know how many boots before it does the check again.  This is handy information to know if you use your computer at work - you wouldn't want to do a disk check while your meeting attendees are sitting there waiting for your computer to boot prior to showing them your presentation.

Your FireFox message appears on my system from time to time if it didn't shut down properly the last time.  It is being kind in asking you if you want to start a new session, or restore the old one - which may lead you back to the website that caused FireFox to crash the first time.

Hope that helps.

---

### Post by nickm on 2007-07-08
Hi Snoo,

The first message you get is a tool called fsck or File System ChecK checking your drive for errors on start up, it does so every so often to fix non contiguous files and is perfectly normal.
In ubuntu fsck is run every *n* bootups as well as when an error is detected.
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

I also get the second message from firefox quite a bit and its always stumped me too! :)

---

### Post by Snoo on 2007-07-09
Thanks guys.

No worries about the disk check then. As for the other. I always shut all programs down beforre shut down. Maybe I just need to leave it a few seconds after closing firefox before I hit a system shutdown?

Is there a windows style process monitor I can see (ctrl alt del) to see how long it takes to close out.

I'll keep an eye on it I guess. Thanks.

---

### Post by lunamystry on 2007-07-09
My computer says there is an error in my hard drive, i think. Apparently sda1, which i presume is my root partition has an error. I am suppose to run fsck or something of the sort. I really hope i made sense. :-( but anyway I think it could be one of two things:

>I backed up some of my videos using Nero while I was still a winuser and when i installed ubuntu i thought it would be deleted together with Nero because I remember there was something that irritated me about win when i installed ubuntu. 
>The second thing i think it could be is that the hard drive is F@$% and I need a new one.

HELP ME please

Thank you for your Valuable time

---

### Post by Old Pink on 2007-07-09
Worth a look: [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477) :)

---

### Post by lunamystry on 2007-07-09
Thank you hey. I'll check out the link now. :-(

---

