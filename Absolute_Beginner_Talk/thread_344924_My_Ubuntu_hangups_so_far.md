---
title: "My Ubuntu hangups so far"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by stephentyler20 on 2007-01-23
So far I'm getting used to Linux and Ubuntu, but there are still somehangups that go unanswered, that I can't find a solution for by searching.

For one, I can't figure out how to access the files on my Windows XP OS, such as my pictures and music. I've read so much about partitioning and file systems it's making my head spin, but I can't figure out the solution!

Second, the touchpad on my computer is getting extremely annoying... it doesn't do tap-to-drag or tap-to-scroll, so I have to use the physical button, which I find annoying because i like using one hand. Again, I've read a lot about it, but nothing seems to fix it!

Those are the big ones for now! If I can get those going, I'll really enjoy this system!

---

### Post by meng on 2007-01-23
> **stephentyler20 said:**
> i like using one hand
Yeeesssss ... thanks so much for sharing.

Anyway, to your Windows partitions, you should be able to get read access to these quite easily.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

If you can't work through it yourself, start off by telling us what you get with this command:
sudo fdisk -l
(l as is larry not iodine)

---

### Post by Happy_Man on 2007-01-23
All right... for read/write access to your windows partition from Ubuntu, then I highly suggest you install ntfs-3g (search it on these forums). That'll solve all your drive problems, and it's easier than me telling you commandline stuff :biggrin:. Now as for your touchpad... I can't really help you on that, that's an issue for your computer manufacturer, Ubuntu, and drivers to resolve. Try searching Google. That usually helps.

---

### Post by Bachstelze on 2007-01-23
1. Do you need write access to your WIndows drive ? If you don't, I recommend you don't use ntfs-3g. While the risks of it breaking your whole partition are very low, they don't equal zero so using it if you don't need it seems a bad idea to me.

2. Is your touchpad an ALPS or Synaptics ? Synaptics one canbe configured very easily.

---

### Post by stephentyler20 on 2007-01-23
OK. I got access to my Windows files (finally!) by the ntfs-3g thing, which seems to work fine. I now have a link on the desktop that goes straight to my Windows desktop files... rockin. 

I have the synaptics touchpad I believe... I tried one of the fixes, but with no luck.

EDIT: WOW, having access to my files I can finally play with some of the software. Everything runs so smoothly and seems so simple! I love it! Maybe I'll just back everything up to my external disc, erase windows and do a clean install of Ubuntu... dangerous thinking.

---

