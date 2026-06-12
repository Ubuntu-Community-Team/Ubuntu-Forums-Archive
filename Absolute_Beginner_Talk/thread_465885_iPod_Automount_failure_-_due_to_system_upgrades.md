---
title: "iPod Automount failure - ?due to system upgrades?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Zeedok on 2007-06-06
Sorry to post on this again - there's already so many problems with iPods not automounting, maybe we should have a stickie??

Anyway, my iPod (5G, 60GB) was automounting perfectly on both my Feisty machines then . . .

It stopped automounting on my desktop (still works on the laptop). It stopped working immediately after some routine updates from the 'autoupdater'. It works with XP, and my Feisty laptop.

I can only conclude that an update to software only on the desktop has mucked up a setting or my fstab or something. 

I saw a reference to problems with ntfs-config and ipod automounting, and that extra ntfs utilities are needed to get it working again, but I can't find that thread (after 45mins of looking)

Any ideas?? Grateful for any help.

---

### Post by Ek0nomik on 2007-06-06
iPod's aren't NTFS formatted though are they?

Can you post your output of:

```
sudo fdisk -l
```

and  ```
sudo mount
```

and

```
sudo cat /etc/fstab
```

---

### Post by Zeedok on 2007-06-09
An update.

I have managed to almost completely fix the problem.

I manually mounted my ipod and used storage device manager to change the settings back to default. I also selected the option to have it mounted at boot.

It now - somewhat unreliably - is mounted and accessible, especially when device is connected at boot. Floola and Amarok recognise it, though Banshee doesn't (I'm trying to decide on the best music manager!)

I have used my sister's ipod (a 30GB model, otherwise the same gen etc as my 60GB) and it automounts perfectly.

Maybe it wasn't the upgrades, but I've obviously changed a setting on my desktop that works for most apps, but not for Banshee.

I'd be happy to post the output of what you've suggested, but I'm away from my desktop today. I'll try to most the output in the next few days. Thanks for your interest.

---

### Post by Zeedok on 2007-09-29
I fixed this problem in June only to repeat a similar stuff up in September.

I found the best way to get my ipod mounting as it did on a clean Ubuntu install by default is to delete any mount points or references to it in my fstab.

Now it automatically mounts as it should - thought I give you an update (and put it down on paper for myself in case I stuff it up again!!)

---

