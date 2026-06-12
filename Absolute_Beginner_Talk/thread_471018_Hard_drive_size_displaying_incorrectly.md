---
title: "Hard drive size displaying incorrectly"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-06-11
I have just installed a new 160GB hard drive.  It is hdd.  I formatted it with gparted to be ext3.  Gparted says it is 149.05 GB.  The format process used 2.52 GB.  
I edited my fstab to automount the drive with this line > /dev/hdd1	/media/warchest			ext3	defaults	0 0

When I explore the drive with nautilus, however, there is 1 folder inside (lost and found) with "contents unreadable".  Nautilus also says 139.1 GB available.  

My bios saw the drive as the 137GB barrier.  However, gparted is reporting it as 149.05, so I figured the Kernel was able to handle drives over 137.  

Any ideas where to start troubleshooting?  Is it safe to use the drive as a 139.1GB drive (as reported by nautilus) or will using lose data (putting it somewhere in the unreported GBs of drive space)?

---

### Post by taurus on 2007-06-11
Can you post the outputs of these commands from a terminal here?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
free
```

---

### Post by l951b951 on 2007-06-11
df -h

> [root@linuxbox media]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                       18G  6.0G   11G  37% /
/dev/hda1              99M   16M   78M  17% /boot
tmpfs                 252M     0  252M   0% /dev/shm
/dev/hdb1              74G   64G  6.0G  92% /media/linuxstore
hpmediavault:/shares/Volume1/Backup
                      466G  116G  350G  25% /media/vault/Backup
hpmediavault:/shares/Volume1/CinemaNow
                      466G  116G  350G  25% /media/vault/CinemaNow
hpmediavault:/shares/Volume1/MediaShare
                      466G  116G  350G  25% /media/vault/MediaShare
hpmediavault:/shares/Volume1/FileShare
                      466G  116G  350G  25% /media/vault/FileShare
/dev/hdd1             147G  188M  140G   1% /media/warchest


free 

> [root@linuxbox media]# free
             total       used       free     shared    buffers     cached
Mem:        514156     507900       6256          0       3832     264544
-/+ buffers/cache:     239524     274632
Swap:      1048568        188    1048380


fdisk command not found.  This is on Fedora Core 6 machine, so apparently redhat didn't include that one.  is there an alternative?

---

### Post by l951b951 on 2007-06-11
Actually, man  fdisk brings up the manual pages for fdisk, but no combination of fdisk works.  they all say bash: fdisk: command not found

That's probably another problem entirely.  Fedora has been difficult since I installed it.  I will eventually replace it with Ubuntu, but I'm waiting for the next LTS variant.

---

### Post by bodhi.zazen on 2007-06-11
> **l951b951 said:**
> Actually, man  fdisk brings up the manual pages for fdisk, but no combination of fdisk works.  they all say bash: fdisk: command not found

That's probably another problem entirely.  Fedora has been difficult since I installed it.  I will eventually replace it with Ubuntu, but I'm waiting for the next LTS variant.

LOL

With Ubutnu you need to use sudo with fdisk :

```
sudo fdisk -l
```

Also that is a small "L" and not the number 1

---

### Post by l951b951 on 2007-06-11
I did a copy and paste for fdisk -l.  even fdisk by itself doesn't work, but the package (linux basics, or something similar) is installed.  weird.

Here's something else weird.  I copied some files over.  nautilus reduced the available size accordingly.  I deleted the files.  Nautilus did not change the available size.  The files were not sent to my trashcan, but they were put into .trash-levi.  I had to go into the hidden folder and manually delete them?  'Sup with that?

---

### Post by l951b951 on 2007-06-11
Regarding the .trash, the answer was posted [here]("http://ubuntuforums.org/showthread.php?t=468997&highlight=delete+trash+can") by Lord Illidan.

But my 160 GB drive is still only showing 139.1 GB available.  Any ideas out there?

---

### Post by logos34 on 2007-06-11
I know this part at least is correct:

> I have just installed a new 160GB hard drive. It is hdd. I formatted it with gparted to be ext3. Gparted says it is 149.05 GB.

Hard drive manufacturers measure space where '1GB=1,000,000,000 bytes' (base 10 or decimal format).  But OS's (windows, linux, the rest) measure capacity using base 2 or binary format (where 1GB actually = approx. 1.073 billion bytes). So 160gb drives show up as 149gb, a 100gb as ~93gb, 120gb as ~114gb, etc.

---

### Post by Rocket2DMn on 2007-06-11
It might just be that the "true capacity - built in stuff - ext3 allocation table" = 139.1GB.  Just because they say it's 160 gigs, doesn't make it so.  When they say Giga they use 1,000,000,000 whereas the true Giga in hardware is at 2^30=1,073,741,824.

---

### Post by l951b951 on 2007-06-11
> **Rocket2DMn said:**
> It might just be that the "true capacity - built in stuff - ext3 allocation table" = 139.1GB.  Just because they say it's 160 gigs, doesn't make it so.  When they say Giga they use 1,000,000,000 whereas the true Giga in hardware is at 2^30=1,073,741,824.

Thanks guys, I was thinking that might be the case, but here's the kicker:  Gparted is saying I have about 10GB available more than Nautilus.  Take a look at availabe space readouts on my attachments.

---

### Post by Rocket2DMn on 2007-06-11
Nautilus is probably more of an estimate, I would probably trust Gparted a little more, but don't quote me on that.

---

### Post by l951b951 on 2007-06-11
> **Rocket2DMn said:**
> Nautilus is probably more of an estimate, I would probably trust Gparted a little more, but don't quote me on that.

Too late, I just pressed the quote button.  

That answer actually kinda makes sense, and if Gparted is correct, then everything is working fine, out of the box, despite my bios limitations.  Thanks everyone.

---

