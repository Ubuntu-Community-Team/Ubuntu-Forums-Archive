---
title: "Newbie questions about partitioning"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Faramir on 2007-05-07
I'm interested in installing Ubuntu on my computer, but I don't have any experience with drive partitioning and so I'd like some basic questions answered. I guess I should mention that I have a 3-year-old Compaq laptop with a 56GB hard drive, and currently about 42GB is taken up by XP and all my files. So, my questions are:

1. Is it possible (easily) to access files in the Windows partition from the Ubuntu partition?
2. Is it possible to move files from one partition to another, or do they need to be moved off one partition and onto another?
3. How hard is it to set up one partition for just the Windows OS and applications, another for the Ubuntu OS and applications, and a third for files? Will this cause problems with my applications?
4. Can I undo or resize a partition later?

I've always been curious about Linux and open-source, and I think I'm finally ready to give it a try. I just want to make sure I'm not going to completely screw up my hard disk before I start messing with it.

---

### Post by felicity on 2007-05-07
1. Yes it's easy!
2. Yes you can read/write from linux to a windows partition easy. I'm not sure about within windows to a linux drive though. I know you can access the files from windows, I'm just not sure about writing data.
3. It's easy! It won't affect your applications.
4. You can change partitions later, just make sure you backup the files to another partition first, or better yet off the drive if possible (so you don't accidentally mess up!)

Give it a try, but read up first, there are lots of good tutorials on the web for doing a dual-boot system. Linux is fun, I think you'll like it if you give it a try and are willing to learn. :mrgreen:

---

### Post by Wiebelhaus on 2007-05-07
> **felicity said:**
> 1. Yes it's easy!
2. Yes you can read/write from linux to a windows partition easy. I'm not sure about within windows to a linux drive though. I know you can access the files from windows, I'm just not sure about writing data.
3. It's easy! It won't affect your applications.
4. You can change partitions later, just make sure you backup the files to another partition first, or better yet off the drive if possible (so you don't accidentally mess up!)

Give it a try, but read up first, there are lots of good tutorials on the web for doing a dual-boot system. Linux is fun, I think you'll like it if you give it a try and are willing to learn. :mrgreen:

/agree
There's a tool that will allow you to see Linux partition from windows, but not write to.

---

### Post by Faramir on 2007-05-07
Thanks! That gives me a lot of confidence. I think I'll try the install in just a little bit. I'll let you know how it went.

---

### Post by thefoolisme on 2007-05-07
Just for curiosity's sake, I noticed that based on the inform provided, you only have about 14 GB of space left on your drive.  You talked about putting a 3rd partition in just for files.  What size partitions are you looking at for Ubuntu and the 3rd partition?  You want to make sure you give yourself enough room.

---

### Post by Faramir on 2007-05-07
Unfortunately, things did not go as well as I had hoped.

I selected the default partitioning option, which I thought would keep XP and create a new partition for Ubuntu in the free space. However, what actually happened was that XP got erased and Ubuntu was installed over it. Of course, this annoyed me somewhat, especially since I hadn't backed up (which is of course my fault), but luckily there wasn't anything of great importance on my computer that's not stored somewhere else. I'm not looking forward to copying all my music back, though.... I wish there was some way to make it more clear in the installation setup exactly what the partitioning is going to do, without using a bunch of acronyms and names that don't make sense to someone who knows very little about drive partitioning (like me).

Anyway, I was also frustrated to find that after erasing Windows, even Ubuntu didn't work! It would boot and bring up the login screen just fine. Once I logged in, I saw the desktop wallpaper and the little screen that shows GNOME, Nautilus, etc. loading, and heard the startup music. However, the taskbar and top menus never appeared after about 15 minutes, although my hard drive kept spinning. I had a completely blank screen (except for the wallpaper), so I had no choice but to manually shut down my computer. I tried twice and got the same result both times. It also didn't recognize my wireless card, but I decided to worry about getting a working OS installed before tackling that. Now I've reinstalled XP, which is how I'm able to type this.

I still want give Ubuntu a shot. Are there any suggestions for how to make sure that the partitioning program does what I want it to this time? I really don't want to have to install XP and 3 years worth of security updates again.... Plus, what should I do if I end up with a blank desktop and no menus again?

Oh, and to TheFoolIsMe: I know I have a small hard drive for nowadays, but I'm not planning to install any more large programs on my system. Plus, now that the partitioner wiped my disk without asking me, I have a lot more free space than I did before.

---

