---
title: "Can't boot Ubuntu in the boot menu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-28
Hi everyone, 
I have just installed my Ubuntu server 7.10 and it's not showing on my windows boot menu and when i run bcdedit.exe /enum all, it doesn't show that its installed into my system. 

How can I boot into my ubuntu server partition and add that partition to my boot menu?
NOTE: i can't even boot into my ubuntu partition so I don't know how I could get in to find the legacy number

PLEASE HELP!!!!!!!

---

### Post by spiderbatdad on 2008-01-28
It sounds like you used a windows partitioning program...installed Gutsy on a partition, and came to the Ubuntu beginner's forum to get an answer on how to use the Windows operating system. Is this correct?

---

### Post by Amstell on 2008-01-28
check out supergrub to fix any problems with the boot menu.

---

### Post by disappearedng on 2008-01-28
> **spiderbatdad said:**
> It sounds like you used a windows partitioning program...installed Gutsy on a partition, and came to the Ubuntu beginner's forum to get an answer on how to use the Windows operating system. Is this correct?

No you are not correct. I manually parted 26 Gbs of my harddisk, 5 as a swap partition and the rest as ext3 with "/". I am asking how I could get into Ubuntu if I can't even boot into Ubuntu so that I could start using ubuntu. I don't think it's nice for you to go around accusing people and acting like a smart ***.

---

### Post by spiderbatdad on 2008-01-28
I apologize for coming off that way. I misunderstood your post and was asking for clarification of what seemed like a great irony.

Since I have offended you, I will apologize again and not disturb you any further.

---

### Post by Amstell on 2008-01-28
> **disappearedng said:**
> No you are not correct. I manually parted 26 Gbs of my harddisk, 5 as a swap partition and the rest as ext3 with "/". I am asking how I could get into Ubuntu if I can't even boot into Ubuntu so that I could start using ubuntu. I don't think it's nice for you to go around accusing people and acting like a smart ***.

Dude just check out supergrub.  That will help you fix your boot menu.

then once your in ubuntu look at your boot menu.  i think its /etc/boot/menu.lst

something like that.

good luck

---

### Post by disappearedng on 2008-01-29
I did check out supergrub and I automatically fixed it and activated it.

However, when I try to manually boot it from supergrub, I get 
"
root (hd0,2)

Error 22: no such partition"

even though i could clearly see this partition when I activate it and fixed it automatically using super grub.

I tried hiding my windows partition but when I reboot, I still get booted into my original windows partition.

What's wrong?

---

### Post by apostate on 2008-01-29
In what order are your HD partitions?  GRUB starts counting from 0 not 1, so it may actaully be pointing to the wrong partition still.

---

### Post by disappearedng on 2008-01-29
Hm... How do I find out about that?

---

### Post by ibbill on 2008-01-29
this what I did when I lost my boot menu. (note  I am a newbie) cant remember where I found this fix sorry to the person that posted it.

I’ve found a simple solution to restore your Grub Boot Loader:

1. Start your System with a Live CD (Ubuntu as well).
2. Open a Terminal Windows to send command in a Shell.
3. Type “grub”
4. Type “root (hd0,2)”, or whatever your HardDisk + BOOT partition numbers are (my /boot is at /dev/sda2, which translates to hd0,1 for grub).
5. Type “setup (hd0)”, or whatever your HardDisk number is.
6. Quit grub by typing “quit”.
7. Reboot your System.

Your Boot Loader now will start up correctly! Have a fun with your Linux Box

---

### Post by Cchhrriiss on 2008-01-29
This may help too...kinda the same thing as the post above...

[http://ubuntuforums.org/showthread.php?t=680036&highlight=grub+two+sata+drives]("http://ubuntuforums.org/showthread.php?t=680036&highlight=grub+two+sata+drives")

---

### Post by disappearedng on 2008-01-29
Is this under "rescue mode" in Ubuntu Server?

---

### Post by disappearedng on 2008-01-29
I get this weird error:

#grub
Probing devices to guess bios drivers. This may take a long time.
Error opening terminal: bterm.

How do i go about fixing it?

---

