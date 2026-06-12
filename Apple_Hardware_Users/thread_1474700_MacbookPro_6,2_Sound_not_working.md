---
title: "MacbookPro 6,2 Sound not working"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by abel_bcn on 2010-05-06
First macbook. I've managed to get everything I really need running except sound.

Anyone with more experience has or knows how to fix this?

I'm 5-year ubuntu user so if anyone asks for any system info I'll probably be able to manage it.

This is the only sound-related entry I could find in lspci.

> 01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


I'll continue looking for drivers/fixes and post anything I can find.

---

### Post by linuxopjemac on 2010-05-06
did you install alsa backport module and unmute all channels ?

---

### Post by abel_bcn on 2010-05-06
Yeah I installed **linux-backports-modules-alsa-2.6.32-22-generic-pae** and still nothing.

Thanks for replying.

---

### Post by linuxopjemac on 2010-05-06
did you also unmute the channels ?
```
alsamixer
```
unmute with "m"

---

### Post by pan.kostechka on 2010-05-06
> **abel_bcn said:**
> First macbook. I've managed to get everything I really need running except sound.

Anyone with more experience has or knows how to fix this?

I'm 5-year ubuntu user so if anyone asks for any system info I'll probably be able to manage it.

This is the only sound-related entry I could find in lspci.



I'll continue looking for drivers/fixes and post anything I can find.

The sound fix described here [https://help.ubuntu.com/community/MacBookPro6-2/Lucid]("http://https//help.ubuntu.com/community/MacBookPro6-2/Lucid") worked for me.

---

### Post by abel_bcn on 2010-05-06
> **linuxopjemac said:**
> did you also unmute the channels ?
```
alsamixer
```
unmute with "m"

Thanks dude that worked! I'm a bit concerned though about sound quality. I have the perception it's much better on OSX. And although it doesn't really surprise me, has someone else had this perception?

---

### Post by itismike on 2010-08-18
The first time I didn't modify alsa-base.conf because my headphones were working fine. After changing it and rebooting, sound works for me, too! I'm trying to figure out how to modify the Community Documentation page so others don't make the same mistake I did.

---

### Post by furok23 on 2010-08-18
alright man i just took care of this on my mpb last week. 

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

after that ur gonna need to open terminal and type:

```
alsamixer
```then you need to unmute the "front" channels. use the arrow keys to navigate the devices til u get to that one, and press "m" to unmute

then restart.

worked for me!

---

