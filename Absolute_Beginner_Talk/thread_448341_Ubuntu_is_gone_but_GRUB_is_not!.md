---
title: "Ubuntu is gone but GRUB is not!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-05-19
Okay... I'm really tired and don't have the time to explain fully so I'll say it in steps:

1) I wanted to move Ubuntu to my second hard drive...
2) I used the livecd to delete every ubuntu partition on the first drive and resized the windows one to fill up the drive
3) Restarted... GRUB still wanted ubuntu...

I always happen to do things the wrong way.

Time to sleep.... Be back in the morning.

---

### Post by eentonig on 2007-05-19
I'm sure there are other guides out there. This was the first that came up on google

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

---

### Post by seshomaru samma on 2007-05-19
what do you want to achieve?
reinstalling grub will probably fix everything

---

### Post by Gorthus on 2007-05-19
I dont want grub... I want to have one hard drive with a NORMAL windows installation. I want to get RID OF grub.

---

### Post by icechen1 on 2007-05-19
> **Gorthus said:**
> I dont want grub... I want to have one hard drive with a NORMAL windows installation. I want to get RID OF grub.

If you have a Windows XP cd go in recory console and tape fixmbr

---

### Post by seshomaru samma on 2007-05-19
yes
boot from the windows CD
choose 'R' (recovery mode)
choose your partition
put in the admin password then the command 
```
fixmbr
```
windows will ask you something like "are you sure you want to do that?"
say 'yes'
and you wil have no grub

---

