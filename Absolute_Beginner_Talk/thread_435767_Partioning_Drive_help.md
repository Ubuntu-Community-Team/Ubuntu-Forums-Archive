---
title: "Partioning Drive help"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by wildteen88 on 2007-05-07
I have installed Ubuntu before but I did not do any partitioning. I installed it on the whole drive.

I have downloaded the Live Desktop CD and I am currently at the partition screen.

I am a little confused with the wording on this screen. I currently have the first option selected, which is this
> Guided - resize SCSI1 (0,0,0), partition #1 (sda) and use freed space
Then underneath it has a scroll bar for creating a new partition and I have it set to 9% (20.8GB)

Does this resize my Windows partition to 230GB and then installs Ubuntu on the remaining 20GB?

Thanks for any help.

---

### Post by wildteen88 on 2007-05-07
Here is a screenshot of what I mean:
[[IMG]http://img155.imageshack.us/img155/5704/screenshotinstallav9.th.png[/IMG]](http://img155.imageshack.us/my.php?image=screenshotinstallav9.png)

---

### Post by John.Michael.Kane on 2007-05-07
> **wildteen88 said:**
> Does this resize my Windows partition to 230GB and then installs Ubuntu on the remaining 20GB?

You answered your own question.

That slide you see allows you make space available for ubuntu to use. eg: if you have 300gb harddrive, and want 125gb for ubuntu you move the slide till you seen 125gb. 

The partition manager would then proceed to resize the disk, and place ubuntu on the newly made 125gb space.

---

### Post by quinnten83 on 2007-05-07
I have to wonder what it does with the remaining windows partition.
I installed ubuntu on the laptop of my niece some time ago and i put the ubuntu partition to 9Gb. After the install I started windows and in the windows discmanager, I saw that the empty partition space had a green outline around it.
The HD was partitioned into two disk in windows, the remaing free space on both partitions had the green outline and were marked by windows as "unknown".
I formatted the largest partition back to NTFS, cause she really uses windows and is only familiar with that (actually so am I, hence my nOOb status).
is there anywhere where I can find **[SIZE="4"]QUICK [/SIZE]**and **[SIZE="4"]EASY [/SIZE]**explanations about this?

---

### Post by frigin_AL on 2007-05-07
OK, here is another scenario.

Compaq Presario V2000 – 80GB
Windows XP SP2 installed 10GB
Files, My docs and all kind of crap = 69GB

How do I install Ubuntu 7.4 (partition problems)
When I use resize disk I get an error, I don’t want to nuke the windows partition!
I have all cd, drivers, backup of all my data, just don’t feel like installing everything again!

---

### Post by dptxp on 2007-05-07
I have not checked but Windows does not see the 9% you used for Ubuntu.
The two are for /, i.e., the root partition where you got ubuntu, and SWAP
that is used as RAM. It is normal. You can make Windows see the EXT3 partition
for root. But you got to install one program in Windows.

---

### Post by louieb on 2007-05-07
> **quinnten83 said:**
> ... where I can find **[SIZE=4]QUICK [/SIZE]**and **[SIZE=4]EASY [/SIZE]**explanations about this?
Depends on what you call easy. for quick visualization of hard drive usage try the GParted live CD.  [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

