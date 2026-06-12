---
title: "partitioner erased my hard disk, no menu or taskbar in desktop"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Faramir on 2007-05-07
Earlier today I had posted on this forum, asking some basic questions about partitioning my hard drive. From the replies I received, I felt confident that everything would be fine and proceeded to install Ubuntu.

Unfortunately, things did not go as well as I had hoped.

I selected the default partitioning option, which I thought would keep XP and create a new partition for Ubuntu in the free space. However, what actually happened was that XP got erased and Ubuntu was installed over it. Of course, this annoyed me somewhat, especially since I hadn't backed up (which is of course my fault), but luckily there wasn't anything of great importance on my computer that's not stored somewhere else. I'm not looking forward to copying all my music back, though.... I wish there was some way to make it more clear in the installation setup exactly what the partitioning is going to do, without using a bunch of acronyms and names that don't make sense to someone who knows very little about drive partitioning (like me).

Anyway, I was also frustrated to find that after erasing Windows, even Ubuntu didn't work! It would boot and bring up the login screen just fine. Once I logged in, I saw the desktop wallpaper and the little screen that shows GNOME, Nautilus, etc. loading, and heard the startup music. However, the taskbar and top menus never appeared after about 15 minutes, although my hard drive kept spinning. I had a completely blank screen (except for the wallpaper), so I had no choice but to manually shut down my computer. I tried twice and got the same result both times. It also didn't recognize my wireless card, but I decided to worry about getting a working OS installed before tackling that. Now I've reinstalled XP, which is how I'm able to type this.

I still want give Ubuntu a shot. Are there any suggestions for how to make sure that the partitioning program does what I want it to this time? I really don't want to have to install XP and 3 years worth of security updates again.... Plus, what should I do if I end up with a blank desktop and no menus again?

---

### Post by jargoman on 2007-05-07
when you reinstalled windows you should have erased all partitions then created a new only using half your disk space then when installing ubuntu use the option to let ubuntu use all free space. The safest bet is to partition yourself manually. 

As far as your panel being missing that's unusual. probably a faulty installation. use the option when you first boot ubuntu to check the cd for burn errors. check the md5sum of your iso file then Try the installation again. other than that do you have more than 256 megs of ram? If you got as far as you did your computer is probably supported (except the wireless card but that can be fixed)

---

### Post by Faramir on 2007-05-07
I checked the CD and it didn't detect any errors. I reinstalled Ubuntu and realized where I had messed up the first time -- I had told the partitioner to use the entire drive. That's what I get for messing with things I'm not sure about. Anyway, the partioning went fine and now I have both XP and Ubuntu on separate partitions.

However, I still have the same problem with the taskbar and top menu missing. And yes, my laptop has 384MB of RAM. I suppose I could try re-downloading the ISO file, but everything else seems to be working fine, it's just this issue with the menu. Thanks for your help so far.

---

### Post by Gen2ly on 2007-05-07
I haven't looked lately but usually an alternative install disk is available, maybe you can give that a try?

---

