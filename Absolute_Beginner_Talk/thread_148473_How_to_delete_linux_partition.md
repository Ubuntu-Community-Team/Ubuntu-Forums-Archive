---
title: "How to delete linux partition?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by dearanna on 2006-03-22
Hey all,

I am turning one of my computers into a Windows XP machine, and the other into a Ubuntu machine.

Here's my problem:

on my to be windows machine, I have both a windows and a ubuntu partition. I need to delete my ubuntu partition, and get rid of the GRUB bootloader. How do I do this?

I tried using a partition manager to delete it, but it would not detect the partition.

Please help. I want to keep my windows partition because I lost the install disc.

I also tried using the install CD's partition manager to delete the ubuntu, but it would not allow me to. So please help!!!](*,)

---

### Post by kenweill on 2006-03-22
You can delete the ubuntu partition under windows. But doing so will prevent you from booting to windows at all.

Grub error will appear during boot up.
If this happens, you gonna need to have your windows install disc.

---

### Post by localzuk on 2006-03-22
First you need to get rid of grub from the MBR.

To do this, insert your windows xp cd and enter Rescue mode when asked. From the command line type 'fixmbr' and 'fixboot' and it should do this for you. Reboot and see if it has gone. If it hasn't, repeat but only use one command at a time.

Now that you have got rid of the grub bootloader:

In Windows XP, open the Control Panel, followed by the Administrative tools folder. Now open Computer Manager.

Select the 'Disk Management' option from the list. Select the partition you wish to delete and do so.

This should do what you want.

EDIT: Just noticed you say you lost your install cd - if you do not have a Windows XP disk you could try the [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) which contains some MBR recovery tools. Beware, this disk contains things that can damage your data!

---

### Post by goatflyer on 2006-03-22
boot into windows recovery mode
run FIXMBR
 (that will safely  overwrite grub)

---

### Post by dearanna on 2006-03-22
oh darn,

I don't have my windows CD!!

I lost it, I think my cleaning lady threw it away!!!
But  tried something else here.

I deleted the ubuntu system, then installed only the base system which took up about 600mb.

That way I still have 19GB for the windows machine.

Thanks anyway's guys!!

My windows machine is a dedicated Game Development machine
My Linux machine is a dedicated work horse!!
lol

---

