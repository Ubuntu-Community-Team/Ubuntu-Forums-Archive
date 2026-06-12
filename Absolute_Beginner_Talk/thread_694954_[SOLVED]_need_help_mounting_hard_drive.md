---
title: "[SOLVED] need help mounting hard drive"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-12
i haven't been able to find any threads with my exact problem, so here it goes:

i only have one hard drive. i have no current operating system installed. i boot off the live cd, and go to places -> computer, only to find that ubuntu can't find my hard drive. there's nothing there. just the cd-rom drive and the filesystem. 

i've been trying to fix this for 2 days, and i'm just at a complete loss.

i would either like to know how to completely format whatever's on my hard drive from the live cd ('cause i'd previously tried to install windows, and that failed), or how to get ubuntu to see my hard drive. or both.

any help will be greatly appreciated. i can't wait to get ubuntu on this computer :guitar:

---

### Post by taurus on 2008-02-12
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Sinkingships7 on 2008-02-12
> **taurus said:**
> Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

here you go. 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ed14ed1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18236   146480638+  83  Linux
/dev/sda2           18237       18965     5855692+  82  Linux swap / Solaris

```

---

### Post by taurus on 2008-02-12
Use gparted in System -> Administration and delete those two partitions.  Then, format the whole thing as ext3 and then click the install icon on the desktop.  Tell the installer to use the whole harddrive unless you want to partitions that harddrive yourself first before you install Gutsy.

---

### Post by Sinkingships7 on 2008-02-12
opening gparted as we speak. i've tried opening this application before; is it supposed to take forever while it's scanning the devices? i waited about 15 minutes last night and it was still scanning devices so i just quit :confused:

also, while it's doing that, i get absolutely no hard drive activity. no light on my computer telling me that the hard drive is being written to or from.

---

### Post by taurus on 2008-02-12
Maybe GParted LiveCD works better.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Sinkingships7 on 2008-02-12
okay, it took a bit, but it's working now. i don't have an option to delete the swap partition. has a nice little lock after it. any ideas? 

thank you so much for your fast replies and help. 50% of why i love ubuntu is this community.

---

### Post by taurus on 2008-02-12
Looks like the swap is mounted right now so you can't delete it.  You must first unmount it so you have to shut down gparted first.  Then, open a terminal and run

```
sudo swapoff /dev/sda2
free
```
You should see the swap as 0 from the output of the second command.  Now, fire up gparted again.

---

### Post by kwacka on 2008-02-12
Alternatively, right-click on the lock symbol and select 'swap off'.

I would also recommend that you have at least 3 partitions - one for system, one for swap, and one for home.

That way you can delete the system partition for upgrades, re-installs, etc while keeping all the settings & data safe in the home partition.

---

### Post by Sinkingships7 on 2008-02-12
okay, so i did everything you told me to do. however, when i go to install it gets stuck on formatting. i also cannot format my drive with the ext3 filesystem using gparted, because it's not there. as i said earlier, when i go to places -> computer, my hard drive is not shown. not just not mounted, but not there at all.

---

### Post by Sinkingships7 on 2008-02-12
can anyone help me? i'm sick of being frustrated lol. i just want ubuntu up and running.

---

### Post by Sinkingships7 on 2008-02-12
pleaaase?

anyone?


no OS = waste of 600 dollars i spent on this computer.

---

### Post by taurus on 2008-02-12
It was there and now it's not!  Can you post the output of this command from a terminal again?

```
sudo fdisk -l
```

---

### Post by zozobra on 2008-02-12
If you're booting from the live cd, your hard drive will not show up under places as those places are actually on the cd. You would have to mount your hard drive in the live cd for it to show up. You should be able to run through the install process and see your hard drive though. Choose to use the entire disk when prompted by the installer.

---

### Post by Sinkingships7 on 2008-02-13
this has been solved, though my methods may have been a bit overboard. 

i reinstalled windows and got it working properly (it was messed up before, wouldn't even boot. that's why i could never shut the computer down properly). then i shut down windows the right way and booted from the ubuntu cd. now i have a successful dual boot, and plan on wiping out windows with gparted and letting ubuntu take over.


thank you everyone. you were all very helpful!

---

