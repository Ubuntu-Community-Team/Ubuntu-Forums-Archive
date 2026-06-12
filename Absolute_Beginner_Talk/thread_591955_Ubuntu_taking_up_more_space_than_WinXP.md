---
title: "Ubuntu taking up more space than WinXP"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by keech on 2007-10-25
I have just installed gutsy. I also have WInXP with Office in my system. I have everything loaded in my system all multimedia codec and players, all essential softwares for surfing the net in WinXp but to my astonishment, I find the Ubuntu file system is taking more space than WinXP. I have attached the screen shots of both drives. Could anyone explain to me why this is happening????

Ubuntu File System
[[IMG]http://img143.imagevenue.com/loc1009/th_71292_File_Sys_122_1009lo.jpg[/IMG]](http://img143.imagevenue.com/img.php?image=71292_File_Sys_122_1009lo.jpg)

Windows XP
 [[IMG]http://img139.imagevenue.com/loc152/th_71297_Windows_HD_122_152lo.jpg[/IMG]](http://img139.imagevenue.com/img.php?image=71297_Windows_HD_122_152lo.jpg)

Regards...Mohan

---

### Post by thelocust on 2007-10-25
(no screenshots) could you run firelight, might have to install it but it's pretty handy, and post a screenshot of it fot the whole drive.

---

### Post by p_quarles on 2007-10-26
I'd say that's pretty unusual. In my experience, an Ubuntu installation with a pretty wide range of applications takes up maybe 4 gigs (not counting data).

To ensure that you have an accurate reading, you can open a terminal and type the following command:
```
df -h
```
Post the results here if you need help interpreting them.

---

### Post by Paulmd on 2007-10-26
> **keech said:**
> I have just installed gutsy. I also have WInXP with Office in my system. I have everything loaded in my system all multimedia codec and players, all essential softwares for surfing the net in WinXp but to my astonishment, I find the Ubuntu file system is taking more space than WinXP. I have attached the screen shots of both drives. Could anyone explain to me why this is happening????

Ubuntu File System

Regards...Mohan

Try this in the terminal

sudo apt-get autoclean

In the process of installing and updating software, packages get cached on the hard drive, and persist even when you unistall the packages in question. The theory is to save the from having to re-download something if you want it to be reinstalled. If you've been using ubuntu a long time, the cache can get quite large (there is no proper cache limiting feature at present). Mine had grown to almost 4GB by the time I figured out what was eating so much space on my system. I've only had ubuntu since about August.

---

### Post by swoll1980 on 2007-10-26
when windows reads my hard drive it says its 15gb when ubuntu reads it it says its 20gb why the discrepency

---

### Post by thelocust on 2007-10-26
> **swoll1980 said:**
> why the discrepency
not on a fresh install.

---

### Post by Paulmd on 2007-10-26
> **swoll1980 said:**
> when windows reads my hard drive it says its 15gb when ubuntu reads it it says its 20gb why the discrepency


It is possible that windows cannot read your ext3 partitions (it can be made to read ext3, but defiantely not without geek intervention)

Do you have screenshots?

---

### Post by Paulmd on 2007-10-26
> **keech said:**
> I have just installed gutsy. I also have WInXP with Office in my system. I have everything loaded in my system all multimedia codec and players, all essential softwares for surfing the net in WinXp but to my astonishment, I find the Ubuntu file system is taking more space than WinXP. I have attached the screen shots of both drives. Could anyone explain to me why this is happening????

Ubuntu File System
[[IMG]http://img143.imagevenue.com/loc1009/th_71292_File_Sys_122_1009lo.jpg[/IMG]](http://img143.imagevenue.com/img.php?image=71292_File_Sys_122_1009lo.jpg)

Windows XP
 [[IMG]http://img139.imagevenue.com/loc152/th_71297_Windows_HD_122_152lo.jpg[/IMG]](http://img139.imagevenue.com/img.php?image=71297_Windows_HD_122_152lo.jpg)

Regards...Mohan

The discrepancy here is this:

On linux, the root directory ( / ) is not just the hard drive. Other devices like CDs, dvds, floppies, tapes and other hard drives, are all mounted as subdicecories. For example, the cdrom is /mnt/cdrom (ubuntu uses /media, which is essencially the same thing)

I bet you have a dvd in your drive (a full dvd is around 4gb). (or some other media) this would explain the diffence between what you see in / vs /media/HD01

The used space in / is the total of your hard drive, and all other drives installed on your system.

The space in /media/HD01 is just what is allocated to the main hard drive.

---

