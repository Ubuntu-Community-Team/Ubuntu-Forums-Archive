---
title: "[SOLVED] I broke my hard drive while trying to install another OS"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-28
I had 6 gigs empty on my laptop hard drive so that I could install other Linux OS's and see what they were like.

I first tried to install PCLOS from a livecd, the next time I rebooted, my Xubuntu grub menu came up with no extra choices.

I tried editing the menu.lst to have a choice to boot PCLOS from /dev/sda8, where I'm pretty sure I installed it. It didn't work, there is no such partition apparently.

So I open Gparted. And it shows NO PARTITIONS. Just 40gigs of empty hard drive. My Xubuntu loads fine, so I thought Gparted sucked, so I put my Gparted Livecd in and it said the same thing.

I decided to share my /home partition and I can access the /home for PCLOS. I actually, can access all of the OS from Xubuntu file system.

What the heck did I do?

---

### Post by logos34 on 2007-12-28
what does 

sudo fdisk -l

show?

---

### Post by Pogeymanz on 2007-12-28
"Unable to seek on /dev/sda"

---

### Post by logos34 on 2007-12-28
wow, what DID happen?

edit: apparently pclinuxos screwed up just the partition table because everything is still there.  TestDisk is one option to straighten it out, but read the documentation first and use with caution.

---

### Post by gn2 on 2007-12-28
> **logos34 said:**
> wow, what DID happen?

Incompatibility between DiskDrake and Gparted happened.

---

### Post by Pogeymanz on 2007-12-28
Since I want my Xubuntu to have top priority, what can I do to make Gparted work right and not Diskdrake?

I thought about just deleting everything on that partition through Xubuntu, but I didn't want to mess with anything this important without advice.

---

### Post by logos34 on 2007-12-28
> **gn2 said:**
> Incompatibility between DiskDrake and Gparted happened.

ah, so that's what happened...So would TestDisk still be the way to fix or can DiskDrake undo changes?

---

### Post by gn2 on 2007-12-28
> **logos34 said:**
> ah, so that's what happened...So would TestDisk still be the way to fix or can DiskDrake undo changes?

Honestly haven't a clue.

If it was me I would back everything up to an external drive then wipe the hard drive clean, but that's probably a bit brutal.

It's how I would proceed because I can never be bothered spending ages finding out clever ways of doing things. (too lazy)

---

### Post by Pogeymanz on 2007-12-28
Well.... I don't really like that idea that much. I guess I COULD do it if I have to. I hope someone comes here to save the day...

---

### Post by logos34 on 2007-12-28
You definitely want to backup what you can to cd/dvd, flash or another hard disk if possible.

I wonder if replacing the xubuntu grub with pclinuxos's version or whatever bootloader it uses would solve the problem so the partitions are recognized?

edit: wait, nm--if you can't boot pclinuxos (because can't see sda8 or anything) then that idea's no good

---

### Post by logos34 on 2007-12-28
Or maybe use the pclinuxos[ live cd]("http://docs.pclinuxos.com/Repairing_a_broken_bootloader")...just brainstorming

---

### Post by Pogeymanz on 2007-12-29
So, my question now is: Did Diskdrake break something, or can gparted just not read what diskdrake did?

If diskdrake broke my tables or something, how could this testdisk thing help?

If it didn't break anything, can I just use Diskdrake in Ubuntu and have everything be okay?

---

### Post by Atreus12 on 2007-12-29
I had something similar happen when I installed windows to an empty partition. It ended up blowing away my partition table, and I couldn't use gparted to do anything because it wouldn't recognize the disk.

I used [System Rescue CD]("http://www.sysresccd.org/Download.en.php") and rebuild the partition table using testdisk. Although, I think testdisk is also available on a knoppix live cd.

Check out this [howto]("http://cabmec1.cnea.gov.ar/linux/soft/testdisk/doc/testdisk.html")

It's pretty straight forward, and it worked great.

Andrew

---

### Post by K.Mandla on 2007-12-29
There's also the Ubuntu Rescue Remix CD, which might have some tools that would help.

[www.ubuntu-rescue-remix.org](www.ubuntu-rescue-remix.org)

---

### Post by Pogeymanz on 2007-12-29
Atreus: What did you have to do to fix your problem? Did you just "analyse" with testdisk?

---

### Post by Atreus12 on 2007-12-30
> **EmosSuck777 said:**
> Atreus: What did you have to do to fix your problem? Did you just "analyse" with testdisk?

Well, this was some time ago, but I'll try to remember. I did the *analyze* mode, and I'm not sure if it found them automatically or not.

If it did find them automatically, then I just told it to *write*, if it didn't find them automatically, then I would have done a *search*, followed by a *write*.

So it's definitely *analyze* mode, but I forget exactly how I made it find the "missing" partitions, probably doing a *seach*. In any case, once it lists the correct partitions, simply use *write* and testdisk will create a new partition table.

Hope this helps, post back the results for reference.

-Andrew

---

### Post by Pogeymanz on 2007-12-30
For some reason it recovered my partitions the way they used to be, which was close enough for me, but screwed up my GRUB booter. I just reinstalled Xubuntu.

I was just worried about losing Windows XP because I don't have a good way to get it back. Plus it's full of old essays and mp3's and stuff that I might want.

So, problem solved in a weird round-about way. Hopefully if this happens to someone else, they'll see this and testdisk will work perfectly for them.

Question: Is diskdrake not good for me to ever use again, or did it just have an error once?

---

