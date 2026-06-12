---
title: "My 8x dvd burner burns at &lt;1x always"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by paker on 2008-02-08
I have 8x burner. I used both Gnome Baker and Brasero. I choose max speed or 8x, but it always burns at less than 1x. I tried different DVD blanks, 8x and 16x ones. No effect. Can someone solve this problem for me?

7.10 32 bit utuntu

---

### Post by amingv on 2008-02-08
Have you got sufficient resources to burn at that speed? (Remember that DVD-8x is much faster than CD-8x)

---

### Post by randy78 on 2008-02-08
I know it's probably not the reply you want to hear, but SLOWER is BETTER ;)

---

### Post by yaknowwat on 2008-02-08
Its probably your DVD's.

I have some DVD " + " RW 's with a max write speed of 4x

you most likely have DVD " - " RW 's and that is the reason you are only getting 1x speeds.

Next time when you buy some DVD's pay attention to the type you get its normally worth it to pay the extra few dollars to get the higher grade ones.

---

### Post by paker on 2008-02-08
> Have you got sufficient resources to burn at that speed? Do you mean fast CPU and large memory? I have AMD X2 3800+ and 1 GB of memory. Please let me know I need more resources to get out of 0.6X recording speed.

> SLOWER is BETTER If I am recording avi files, I don't care missing a few frames here and there. 0.6X is way too slow.

> Next time when you buy some DVD's pay attention to the type you get its normally worth it to pay the extra few dollars to get the higher grade ones. I am using HP DVD-R 8X and Office Depot DVD-R 16X. 

Thanks.

---

### Post by covert215 on 2008-02-15
I have the same exact issue.   My computer has similar specs, but it only burns at 0.6x.  Both CD and DVD burning is affected.  Does anyone have solutions?

Edit: I don't believe this belongs in the "Absolute Beginner" forum.

---

### Post by mgranet on 2008-02-15
> **randy78 said:**
> I know it's probably not the reply you want to hear, but SLOWER is BETTER ;)

Slower is NOT better. DVD media is designed to work at specific speeds(i.e., the one printed on the disk). You can get just as many errors from running too slow as you can too fast.

---

### Post by MarkX on 2008-02-15
The auto speed setting for burning also seems to choose the slowest speed for me too, though I can set it to any speed in the menu. Wondering if Ubuntu doesn't know the capabilities my LG DVDr/w or the disks and just defaults to the minimum  speed?

---

### Post by amingv on 2008-02-17
I was looking at the K3b FAQ, and saw something that reminded me of this thread:

[QUOTE=http://www.k3b.org/] Q: My DVD drive supports 16X but K3B keeps burning at 1X! What's happening?
A: Your kernel most likely didn't apply optimal settings for your drive when it detected it. You can find out what are the current settings of your drive with the command
```

hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
```

The following options are known to maximize burning and playback performance:

```
hdparm -d1 -c1 -a8 -u1 /dev/dvd
```

To make these options permanent, a quick and dirty solution is to include the command in /etc/rc.local. Consult your distribution documentation for a tailored solution.
Some drives have buggy DMA support. If you experience instability, leave these options disabled.
Some useful references:
[http://www.togaware.com/linux/survivor/CD_DVD_Drives.shtml](http://www.togaware.com/linux/survivor/CD_DVD_Drives.shtml)
[http://www.linuxjournal.com/article/6921](http://www.linuxjournal.com/article/6921) [/QUOTE]

I believe it may apply for other burning programs as well. I suppose you need to use sudo... Hope it's of any use, but I cannot warrant that.

---

