---
title: "[SOLVED] Catch 22 with Ubuntu learning book :)"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by BurKaBU on 2008-02-28
So since a few days back Ive had Ubuntu installed and even though Im a total beginner and can hardly start the terminal window Ubuntu just make sence to me and I'm more then willing to put in the hours to make it work.
So I downloaded the Guide to Ubuntu to my NTFS partition where and while i had Windows XP installed, now the problem is that I cant get to it here in Ubuntu because its a .rar file.
And to open that file I need to mount sda1 (my ntfs) here in the terminal to unpack it and to do that I need to read the book on how to mount something in ubuntu and to do that I need to unpack it to read it... :)

So if someone could give me terminal guidence on this it would be greatly apreciated ;)

---

### Post by northern lights on 2008-02-28
Which Ubuntu release do you have installed?

Generally, Ubuntu should mount all your NTFS partitions automatically - at least with read support...

---

### Post by BurKaBU on 2008-02-28
> **northern lights said:**
> Which Ubuntu release do you have installed?

Generally, Ubuntu should mount all your NTFS partitions automatically - at least with read support...

he I guess I really need that book because I found as you said my sda1 in erm... explorer? =) 
So I change the question to: How do write in the terminal to get to sda1 so that I can unpack my book and start reading so I dont have to waste youre time with questions like this :P

ps. Ive unrared a few files in terminal that are on the ubuntu partition so I just need to know how to get to /sdai/downloads =)

---

### Post by warbird on 2008-02-28
should be in /media/sda1
or just go "cd media" and do a "ls" to see what you find  :)

---

### Post by SunnyRabbiera on 2008-02-28
could you just copy the guide over to your linux side?
you can use copy and paste.
also for rar you need some extra crap, there is something called unrar and its in the repos

---

### Post by BurKaBU on 2008-02-28
Tnx for the fast replies, got it to work now cheers ;)

---

