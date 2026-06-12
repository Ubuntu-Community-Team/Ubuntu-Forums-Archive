---
title: "Xubuntu is broken today"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-05-08
Yes, i know Xubuntu is technically beta software.

I did a apt update today and xubuntu basically broke and left me with an unusuable desktop. I tried removing packages and reinstalling xubuntu-desktop, but now it wont download the dependencies. Basically the same thing happens if i try to install xfce4 by itself.

Can anyone give me an ETA on a fix ?

Ide hate to have to use windows for the rest of the week :-(

---

### Post by nalmeth on 2006-05-08
Just what happened to make it unusable?
I'm on xubuntu right now, doing great.
Did you --purge remove xfce?
Maybe erasing all your config files will help.

---

### Post by dermotti on 2006-05-08
Are you using Dapper?

If so try a **apt-get update** right now

Anyways, it unusable because i have no panel, cant right click to open menu's, etc, etc. I basically have a blank desktop.

I tried creating a new user, which would have a fresh config file, and had the same results.

---

### Post by nalmeth on 2006-05-09
Yeah, I'm on dapper
I updated last night, but I'm not going to update now that you say it's all messed up! :p

Xubuntu-dapper is wicked isn't it? While it work's anyway. 
If I come across anything I will send it your way.
Please do post if another update sort's everything out for you.

---

### Post by dermotti on 2006-05-09
Looks like the Xubuntu packages are fixed, i was able to upgrade without issue this morning.

---

### Post by Micro Rotors on 2006-05-09
Well my system broke yesterday and I cannot get in as I have no desktop or else I have only the firefox ball all the way to the left on the top. I logged in in the terminal mode and did ```
sudo apt-get update
sudo apt-get dist-upgrade
```

I got some stuff but nothing has changed yet. I will try a restart.

---

### Post by Micro Rotors on 2006-05-09
Nope, still broken.

---

### Post by jhuff on 2006-05-09
I had the same thing happen to me.  I am reinstalling Flight 7 now.  Hopefully we'll hear something soon as to the cause and hopefully the fix.

I'm using it on a Pentium II Dell Inspiron 7000 Laptop.

---

### Post by jhuff on 2006-05-09
According to the following the update packages are fixed.  

[http://xubuntu.info/news.php]("http://xubuntu.info/news.php")

After I get done reinstalling I'll update and let you know how it went.

---

### Post by jhuff on 2006-05-09
Everything worked fine with the exception of the computer failing to boot the first time after the reinstall.  The update occurred without any problems.

---

### Post by nalmeth on 2006-05-09
No sweeping changes are there?
I have my xfce set up *just* the way I like it, and I'll be upset if lose anything, like my clipboard or anything, even small stuff like that.
xubuntu-development has been erratic, as far as I've personally seen.
For a while, there were basically no applets for the panels, and then suddenly they're all there. And more!
Seriously, the desktop icons were a long time coming, and i'm lovin them.

---

### Post by ds[de] on 2006-05-09
It's funny that you opened this thread today, because when I booted my computer an hour ago, xfce was fscked up too (panel and desktop are missing, taskbar is still there)...

Don't know what happened, after the last apt-get update/upgrade everything was still working fine.

I'm using xfce4 with breezy though, it's still a weird coincidence.

Regards,
ds[de]

---

