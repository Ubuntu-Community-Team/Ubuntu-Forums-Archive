---
title: "duel boot up setting failure"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2007-01-21
Hi all,

I tried to do duel boot up. I have ubuntu installed earlier, and then I install window XP. But then the computer will only boot in window XP. I don't know what to do, so I use the live CD to clean up the window XP partition, hope things will go back to normal, but now, when I turn on my laptop, it just say no Operating System, instead of booting Ubuntu. If anything I can do to go back to the Ubuntu that I install, that would be great, thanks a lot.

---

### Post by [bigmac] on 2007-01-21
Hey mate, I think XP overwrote your GRUB bootloader in the MBR. From what I've gathered, it's best to install XP first, and then Ubuntu, because windows doesn't understand or tolerate Linux ;)

I can't tell you how to fix the bootloader, because i don't know that, but maybe you can salvage parts of you ubuntu installation, specifically the /home/user directory and back it up to another computer, say. 

And afterwards go ahead and reinstall with XP first on one partition, and then ubuntu on another.

Alternatively, if your /home dir has a partition for itself, you can install ubuntu again, without formatting /home (choose manual partitioning), and your personal files will be saved. But if you don't have /home on its own partition, then I'm not sure you can install without formatting, maybe it will get screwed up, i don't know.

---

### Post by bulldog on 2007-01-21
Just install windows again if you wish,and leave the ubuntu partitions as they are.
If done you can only boot into windows,but that's an easy fix.
To make your dual boot working you have to reinstall GRUB from the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Reboot and you will see the GRUB menu again.

---

### Post by clark0820 on 2007-01-21
Thanks a lot, now I can get back into Linux w/ window in the other partition, thanks

---

