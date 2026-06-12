---
title: "Does this mean my recovery partition was saved?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-07-13
I recently installed ubuntu, and I'm loving it. I was going to make it so I could dual boot it with my windows XP, but I rushed it and messed up a bit (lol) so ubuntu took over windows and now I can only boot into ubuntu. There are several things that I need to use in windows, games, apps, etc. that don't work in linux even with WINE or virtualbox. So I want to get windows back and try to get it to dual boot with linux again. I have an HP, and my computer came with the recovery console installed in it. No CD's :( So I need to know if my recovery partition was written over by ubuntu as well.  My computer came with 250 GB memory. Approximately 23 gb's of that are dedicated to the recovery console (I believe). When I checked my disk usage analyzer it said this:

[IMG]http://img380.imageshack.us/img380/208/screenshotdiskusageanalrm4.png[/IMG]

It says I only have 221GB or whatever .I'm wondering if my recovery partition got deleted, or if it's just hidden from the disk usage analyzer. Is there any way I can check to see if it's still there? I'm a pretty huge noob when it comes to partitions, etc. Plz help a nub in need.

-Stephan

---

### Post by bme on 2007-07-13
run gparted from admin menu to see the partitions. Disk usage does not show partition info.How did you install ubuntu? did you select a partition or used the whole disk? If you used the whole hd then your recovery partition is gone.....

---

### Post by StephanGFX on 2007-07-13
I'm not sure what I selected. Where can I find gparted? I can't find it :P

---

### Post by imran7567 on 2007-07-13
hey, I am in a similar dilemma, although I have been a little more cautious and haven't proceeded with the installation yet. I am running a dell notebook which has a built in system restore partition (DellRestore). When I ran Ubuntu from the LiveCD and went to the file manager I saw 3 drives. Windows, DellUtility and DellRestore. The later two being partitions installed by Dell. I'm not sure about HP but if their restore is similar then I assume you should be able to see it. If you can't then you might be out of luck. 

On a similar note, does anyone know how to keep the Dell restore partitions and Windows *AND* install ubuntu? I am trying to do it but when I run GParted it will not let me create 2 more partitions (ext3 and swap) required. I am really frustrated, help pplz. (srry if i kinda hijacked ur thread)

---

### Post by Outrunner on 2007-07-13
@StephanGFX: First you'll need to install gparted, like this:

```
sudo aptitude install gparted
```

Now you can use it from System-> Administration-> Gnome Partition Editor - or something like that ;)

---

### Post by splintercellguy on 2007-07-13
imran you have to create an extended partition and put your swap in it.

---

### Post by bme on 2007-07-13
Imran,
In order to use any of the Dell utilities preinstalled on your laptop the partition information should NOT be altered in any manner...
What I did was to copy the contents of the Recovery partition to a dvd then installed Ubuntu into the recovery partition.This will preserve the partition table in order to use the recovery when needed later...
I have already tried recovering to the factory state SUCCESSFULLY. What I did was to format the recovery partition back to NTFS(removes the Ubuntu installation),rename it back to "RECOVERY" then recopied the contents of the dvd I created earlier. Then at reboot pressed F8 and selected "repair computer".

Stephan,

Use the live cd again and run gparted from it....

---

