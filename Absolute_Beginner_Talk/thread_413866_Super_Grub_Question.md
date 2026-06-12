---
title: "Super Grub Question"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Harkainos on 2007-04-19
I have windows XP Pro and Ubuntu 6.10 installed on the same drive. Right now (since I installed Ubuntu last) I cannot boot into Windows. The option is there, put nothing happens (save a 'Starting Up...' line on a black page). I am thinking i need to rewrite the Grub boot loader to get it to start. I have read through the Super Grub page. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

How do I get the boot option to be permanent? If not, how do I go about making a solid duel boot load?
Does this write to the mbr so both can boot? 
Do I need the CD in when starting the OS?

---

### Post by Cicatrix on 2007-04-19
You probably don't need super-grub, because you can modify your grub menu in the /boot/grub/menu.lst file on your linux partition. (and anyway, I remeber super-grub as not really being useful when I had a similar problem.)
If it helps, my windows xp entry looks like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
It is on the first partition of the second hard-disk.

Modifying the /boot/grub/menu.lst file should be enough, no need for a cd or playing with the mbr.

---

### Post by Harkainos on 2007-04-20
I have the option to boot windows now.... it just goes to a blank screen. Will this resolve the issue?

I, honestly, have no idea what is being typed there. I am assuming my numbers need to be different. I will look for a grub tutorial on the forums. If you find one first, please post it here

---

### Post by Harkainos on 2007-04-22
I am coming across 2 roadblocks

1. the file menu.lst is read only and for some reason i cannot change that. Do I need to edit this in terminal?

2. Windows is on the same drive as Ubuntu and I installed it first and therefore the first partition. What would that code look like, once I put it in there?

---

### Post by adrian15 on 2007-04-23
> **Harkainos said:**
> I have windows XP Pro and Ubuntu 6.10 installed on the same drive. Right now (since I installed Ubuntu last) I cannot boot into Windows.
Aha.
> **Harkainos said:**
> 
 The option is there, put nothing happens (save a 'Starting Up...' line on a black page).

This is bad. Windows does boot but does not continue to boot.
> **Harkainos said:**
> 
 I am thinking i need to rewrite the Grub boot loader to get it to start.

You are wrong.

My advice:
Fix Windows boot with a windows install cd (All this stuff about the recovery console, fixmbr and fixboot).
Then fix Linux boot with Super Grub Disk: Linux -> Fix Boot of Linux.

And that's it.

Keep us informed about your improvements.

adrian15

The menu.lst piece of code for booting windows is:
```

title win
rootnoverify (hd0,0)
chainloader +1
boot

```

---

### Post by Harkainos on 2007-04-24
I did try fixing grub.... but its not broken. Everything in there looks fine in grub - just not actually loading windows. Looks like a repair is in order.

---

