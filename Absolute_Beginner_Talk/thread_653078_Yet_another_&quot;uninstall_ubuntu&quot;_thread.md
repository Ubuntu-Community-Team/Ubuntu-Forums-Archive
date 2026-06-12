---
title: "Yet another &quot;uninstall ubuntu&quot; thread"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by JewelOfSoul on 2007-12-29
hello. i hope someone can help me out with this problem:
i installed ubuntu in my slave hdd (not a partition) but this hdd is almost dead, it doesn't work anymore. i disconnected the hdd (because it useless now) but the "GRUB" says "Error" instead of showing the list to choose OS (i have WinXP installed too) and freezes. i can't choose the OS, i guess i have to uninstall Ubuntu. how do i do that?

but i will install Ubuntu in the good hdd after getting rid of the old, dead hdd. is there a way to make the GRUB load WinXP as default instead of loading Ubuntu?

sorry but i didn't find anything on the forums after a quick search.

---

### Post by erfahren on 2007-12-29
[http://ubuntuforums.org/showthread.php?p=4030157](http://ubuntuforums.org/showthread.php?p=4030157)

---

### Post by Tyke91 on 2007-12-29
disregard everything i said.

---

### Post by eternicode on 2007-12-29
If you're planning on reinstalling Ubuntu on the working HDD, I don't think you should have to uninstall grub first, unless you want to access windows prior to installing.

If you just go straight to the reinstall, it *should* update the grub to boot from the new ubuntu install.

Unless someone knows that it works differently...

---

### Post by erfahren on 2007-12-29
> **eternicode said:**
> If you're planning on reinstalling Ubuntu on the working HDD, I don't think you should have to uninstall grub first, unless you want to access windows prior to installing.

If you just go straight to the reinstall, it *should* update the grub to boot from the new ubuntu install.

Unless someone knows that it works differently...
actually that's true but it's a good idea to run check disk 2 or 3 times and defrag the Windows partition before resizing it (JKDefrag is a excellent standalone freeware defragger [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

that's a good point though. I didn't think of that.

---

### Post by eternicode on 2007-12-29
> **erfahren said:**
> it's a good idea to run check disk 2 or 3 times and defrag the Windows partition before resizing it (JKDefrag is a excellent standalone freeware defragger [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

Absolutely :D I'd recommend the same program ;) I'd run JkDefrag 2 or 3 times, but it's so efficient I'm not sure how effective running it 2+ times would be.  But better safe than sorry


EDIT:
Um...forgot the topic of the thread ^_^"
Does reinstalling the old, almost-dead hard drive bring back the GRUB bootloader?  If not, you'll have to use erfahren's link or something similar to restore the windows MBR.

---

### Post by JewelOfSoul on 2007-12-29
i downloaded JKDefrag. is it really on 60% of the process of defragging? it's too fast! you see way more action than when you use diskeeper or windows defrag tool.

i'll reinstall ubuntu in the good HDD and let the GRUB update, like eternicode suggested.

but none mentioned anything about the second question. is there a way to make the GRUB load Windows as default? because it loads Ubuntu as default.

---

### Post by hums07 on 2007-12-29
If you have Windows CD. Just boot with it, select repair.

---

### Post by eternicode on 2007-12-29
Once you have grub up and working, you can edit the /boot/grub/menu.lst file under Ubuntu.

UbuntuForums post regarding changing grub order:
[http://ubuntuforums.org/showthread.php?t=574789&page=2](http://ubuntuforums.org/showthread.php?t=574789&page=2)

Google search, should give you some decent material:
[http://www.google.com/search?q=grub+menu.lst+make+windows+boot+first](http://www.google.com/search?q=grub+menu.lst+make+windows+boot+first)

As for the JkDefrag being "too fast"....not quite sure what the problem is, but if the windows partition is not sufficiently defragged after running it, feel free to use other tools :)

---

### Post by erfahren on 2007-12-29
the JKDefrag might still need to go through it's "optimizing" stage.

I've heard of some people having problems with the LiveCD's "guided partitioning" when there were too many errors in the Windows file system. 

Running check disk a couple times fixed that (so I always suggest people to that from the start) - in my experience check disk doesn't always fix all the errors on the first run (in WinXP anyway). That can be checked through the "Winlogon" entry in the Window's Event Viewer.

good info on GRUB at hermanzone's [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by JewelOfSoul on 2007-12-31
alright. thanks for the info, guys.

---

