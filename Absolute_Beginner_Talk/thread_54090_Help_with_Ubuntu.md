---
title: "Help with Ubuntu"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by Rhyno_DaGreat on 2005-08-03
Hi, I just installed Ubuntu alongside my current Windows XP OS, and the install went OK, and then I restarted, and it said that it couldn't access or write some file because it was Read-only. Well, at the screen that it warned me about, I clicked OK so that it would try to access or write the file again. Now I'm getting this thing that comes up constantly, like 10-15 times on the screen consecutively that says:

open: Read-only file system
/usr/sbin/termwrap: line 136: $tmpfile: ambiguous redirect
/usr/sbin/base-config: line 26: /var/log/base-config.timings: Read-only file system


And then after it does that about those many times, it stops for five minutes, giving me this message:

* Id "1" respawning too fast: disabled for 5 minutes


What do I do to fix this? Some help would be greatly appreciated, thank you.


-DaRhyno

---

### Post by Lord Illidan on 2005-08-03
Strange..I think you need a re-install..
What are your system specs?
Is your version of Ubuntu for 64 bit or x86?

---

### Post by Rhyno_DaGreat on 2005-08-03
I'm using a x86 architecture. Pentium 4 3.2 gHz

---

### Post by KingBahamut on 2005-08-03
[QUOTE=Rhyno_DaGreat]I'm using a x86 architecture. Pentium 4 3.2 gHz[/QUOTE]
 Seems Illdian is correct. That sounds vaguely like KP to me. Read only file system? What are your full system specs? Hard Drives?

---

### Post by Rhyno_DaGreat on 2005-08-03
I called Sony for help figuring out what the HD brand is, because I can't access the onboard setup for it, and the representative said that he used Linux, and it doesn't matter what brand the harddrive is. But for starters, my system is a Sony Vaio, and it has a 250 GB HD with which when I resized  the partitions during installation, I set it up so the original partition had 80% towards it, while the partition for Linux had 20% towards it.

---

### Post by Rhyno_DaGreat on 2005-08-03
I hope that's enough information.

---

### Post by Rhyno_DaGreat on 2005-08-03
Hello?

---

### Post by Knome_fan on 2005-08-03
Hi, sorry I can't help you specifically, but something is definately really borked with your install. 

As someone already suggest, maybe trying a reinstall would help. To make sure that the problem didn't occur because of a broken install medium, maybe redownloading it would be worth a try.

You also could try out the LiveCD to see if you get the same problem with it.

Sorry again for not really being able to help, but just to give you some hope, from what I know from other people using Sony Vaios with Linux this kind of problem sure isn't normal. On the contrary from what I've heard Vaios do run pretty nice with linux.

Btw., did you do anything unusual during the install, or did you simply do a normal install?
How did you setup your hard drive (what filesystem did you use, etc.)

Good luck!  :grin:

---

### Post by Rhyno_DaGreat on 2005-08-03
It's cool. Um... I used the ext3 file format I do believe, and I resized the partition, just as I said. I downloaded the normal install like before. I'll try and reinstall it. If I get the same problem again, I'll redownload it. I tried Ubuntu LiveCD before I did this, and it worked great.

---

### Post by Rhyno_DaGreat on 2005-08-03
While reinstalling(Which it is currently doing now) it appeared twice, but it kept on installing, that it cannot find the config file.

---

### Post by Rhyno_DaGreat on 2005-08-03
It's working now, thanks. But I'm still a bit worried about that it cannot find that config file. Is that bad?

---

### Post by Knome_fan on 2005-08-03
[QUOTE=Rhyno_DaGreat]It's working now, thanks. But I'm still a bit worried about that it cannot find that config file. Is that bad?[/QUOTE]

What config file specifically?
But don't worry to much, getting some error messages is quite normal and as long as everything is working it shouldn't be a problem.

Now enjoy Ubuntu!  :grin:

---

### Post by Rhyno_DaGreat on 2005-08-03
It didn't exactly say, that's the thing. I'm not too worried. It's just that it reads the top DVD ROM drive (I have 2), but it can't open it when I hit the open button. But it reads the second one fine, and I can open that one.

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Rhyno_DaGreat]It didn't exactly say, that's the thing. I'm not too worried. It's just that it reads the top DVD ROM drive (I have 2), but it can't open it when I hit the open button. But it reads the second one fine, and I can open that one.[/QUOTE]

Thats a feature. The second one should not open if it has a CD in it. In Ubuntu, you must right click on the CD icon on the desktop and chose the "eject" option.

You should do that with your other drive to. Its to keep the system working good.

---

