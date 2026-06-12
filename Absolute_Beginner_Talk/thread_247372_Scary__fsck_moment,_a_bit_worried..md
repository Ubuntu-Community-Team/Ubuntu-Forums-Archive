---
title: "Scary  fsck moment, a bit worried."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-30
Hi all,

As happens fairly frequently when I started up this morning for the first time my system auto-ran the fsck. This morning it found errors (this is the second time on this installation of Dapper. It said that I had to manually run fsck, but as I was a little freaked out, I didn't read the part about using ctrl-d to exit the maintenance shell before I typed fsck into the terminal (console?). It ran a manual fsck and found four problems that it wanted me to fix and the only option I could see was to say yes to all of the fixes. So far so good. After all of this, I did ctrl-d to reboot, after which the system started as normal until Nautilus is supposed to load (I think). I got the target (the open X), then I got the spinney gear, then I got my cursor, then I got *nothing*!! Frozen hard. Had to hold the power button down for however long it took to power down. When I restarted everything *seemed* fine, but now I am worried. How can I check? Also, if I want to get to a console at start-up so that I can apt-get update or something, how do I do that, just in case my GUI doesn't load.

Thanks for your patience with my n00biness, but I'm workin' on it.

Kent

---

### Post by Anduu on 2006-08-30
I wouldn't worry about it too much unless things start acting funky on a regular basis...

   I remember once I had a major lockup and had to hard reboot.I had to go thru the whole manual fsck deal and when I restarted I got to the GDM screen,logged in and...nuthin.Just blank brown screen.
   I rebooted again and logged in again and still a blank screen.So I sat there thinking "OK.What do I do now,dammit!?".After a good 2 or 3 minutes the Ubuntu splash screen popped up...then a minute later my desktop started popping up a bit at a time.It took a total of about 5 minutes in all for Ubuntu to fully load.Everything has been fine since!

I think Ubuntu/Linux must have some pretty sophisicated methods of recovering from data loss/corruption as it seems to me the long load time was Linux just sorting everything out

As for what to do if GDM fails to load or whatever...typically if X fails you get kicked to a text login where you can use the command line.If you don't get a login you can always boot into recovery mode from the grub menu.

---

### Post by Carbonfish on 2006-08-30
Thanks Anduu,

You have put my mind a bit more at ease. I will just go about me business and wait for the next adventure.

Thanks,

Kent

---

