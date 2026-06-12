---
title: "GRUB looks ugly!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-08-30
Ok I don't know how many of you have actually used Suse on a dual boot system but I used it before I switched over to Ubuntu and I always liked the look of GRUB on it then when I installed Ubuntu I was ashamed that GRUB looked so crappy. Could someone tell me why GRUB looks so much better with suse opposed to Ubuntu?

---

### Post by BitTorrentBuddha on 2006-08-30
Have you tried changing your grub background?

---

### Post by dbk927 on 2006-08-30
> **BitTorrentBuddha said:**
> Have you tried changing your grub background?

How do you do that?

---

### Post by PPAAUULL on 2006-08-30
Yes but that is not all I mean suse has it animated and it just looks so neat. I will try to find a screenshot of it to show you.

---

### Post by jdong on 2006-08-30
SUSE and many other distros have pretty boot splashes for GRUB, making it all pretty. The downside is that the graphics mode causes weird hangs and corruption on certain hardware setups.

Ubuntu doesn't mess with GRUB that much, other than the bare essential functionality, because you just see it for that little bit at bootup.

If you want, you can find splash images for GRUB and tweak your grub to your heart's content, but seriously, find something more worthwhile :)

---

### Post by PPAAUULL on 2006-08-30
Ok I think I found this awsome HowTo for you it has some screenshots at the bottem. I am not going to do it personaly. I don't care what it looks like I just wanted to know why it looked so much better on Suse then Ubuntu. Anyways here is the page. [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

### Post by doobit on 2006-08-30
> **jdong said:**
> SUSE and many other distros have pretty boot splashes for GRUB, making it all pretty. The downside is that the graphics mode causes weird hangs and corruption on certain hardware setups.

Ubuntu doesn't mess with GRUB that much, other than the bare essential functionality, because you just see it for that little bit at bootup.

If you want, you can find splash images for GRUB and tweak your grub to your heart's content, but seriously, find something more worthwhile :)

I have my GRUB time set to 1 second anyway to you hardly even see it.

---

### Post by PPAAUULL on 2006-08-30
But I have windows XP on my PC too cause of my brother so I need at lease 25sec timeout I found how to do it anyway.

---

### Post by chips24 on 2008-01-15
> **doobit said:**
> I have my GRUB time set to 1 second anyway to you hardly even see it.

how did you do that?

---

### Post by PmDematagoda on 2008-01-15
Open the menu.lst file for editing and then edit this line:-
```
timeout		10

```

If you want GRUB to be shown only for one second, then the entry looks like this:-
```
timeout		1
```

---

