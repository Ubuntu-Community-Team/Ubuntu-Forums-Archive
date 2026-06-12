---
title: "Laptop with two hard drives"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Ninorcjw on 2006-11-01
I have a laptop with two hard drives, one 80GB the other 30GB, Windows XP is on the 80GB so i want to put Ubuntu on the 30GB. I would rather go through the F8 menu to choose what to boot to but im not sure how to do this with the two hard drives. I looked at this thread 
[http://www.ubuntuforums.org/showthread.php?t=275728]("http://www.ubuntuforums.org/showthread.php?t=275728")
but it require disconnecting one hard drive which isn't an option for me since im on the laptop.

---

### Post by Kateikyoushi on 2006-11-01
Isn't it possible to disable the drive from bios ? I know laptop bioses are usually limited but worth a try.
You could try the alternate install cd which as far as I know let's you to select where to install grub or you can skip it and install it manually.

---

### Post by gn2 on 2006-11-01
> **Ninorcjw said:**
> I have a laptop with two hard drives, one 80GB the other 30GB, Windows XP is on the 80GB so i want to put Ubuntu on the 30GB. I would rather go through the F8 menu to choose what to boot to but im not sure how to do this with the two hard drives. I looked at this thread 
[http://www.ubuntuforums.org/showthread.php?t=275728]("http://www.ubuntuforums.org/showthread.php?t=275728")
but it require disconnecting one hard drive which isn't an option for me since im on the laptop.

Perhaps not as difficult as you would think to disconnect a laptop hard drive, on some it's just one screw, pop a panel and slide out...

Is it out of warranty? What model is it? How confident are you with hardware mods?

If you can work on the guts of a desktop then a laptop should be easy enough...

---

### Post by Ninorcjw on 2006-11-02
I have a Dell Inspiron E1505 and there seems to be lots of screws on the bottom, i am confident with a desktop but ive never opened up a laptop. I was just hoping to avoid having to do this.

---

### Post by gn2 on 2006-11-02
> **Ninorcjw said:**
> I have a Dell Inspiron E1505 and there seems to be lots of screws on the bottom, i am confident with a desktop but ive never opened up a laptop. I was just hoping to avoid having to do this.

From a quick look at Dell's website, it looks like you have a single 120Gb hard drive, partitioned 80, 30, and remainder hidden for recovery software.

Also I'm guessing it's fairly new and still under warranty.
So best to leave it in one piece.....

If you do not have a set of recovery disks on CD's or a Windows CD, I would strongly advise against attempting to dual-boot with Ubuntu.

You can still set-up a dual boot, but with your hardware I would advise trying Parallels or VMWare server first.

[www.parallels.com](www.parallels.com)

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by Kateikyoushi on 2006-11-02
So if it has one hard drive then why take it apart ? :confused: 
Just do a backup defragment partitions and resize or delete and make new partition for linux.

In case you do not have recovery cds try to create it, some machines can do it.

---

### Post by gn2 on 2006-11-02
> **Kateikyoushi said:**
> So if it has one hard drive then why take it apart ? :confused: 


Originally poster said he had two drives. The reason for disassembling/disconnecting is because he wanted to do this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Since it turns out that there's only one hard drive, that's not going to be possible.

Simple really.

The creation of recovery disks and backup is sound advice.

You can never have enough backup :)

---

### Post by Kateikyoushi on 2006-11-02
Okay seems I misunderstood you.

I know why he needs to disconnect the drive but after you noticed he has only one drive wrote it is best to leave it in one piece.
Actually it has no benefit to take it apart if he has one drive.

---

### Post by Ninorcjw on 2006-11-02
I looked at the BIOS and it does seem i have only one 118GB hard drive, then i looked at the system information and it shows the partitions, 80GB and 30GB. I do have a Windows CD, what would the benefit of using Parallels or VMWare be? Is is still possible to install Ubuntu on the 30GB partition?

---

### Post by Kateikyoushi on 2006-11-02
Some notebooks do not come with recovery cds, those have a hidden partition and when you boot the machine can choose to boot the hidden partition and restore the system to factory defaults.

So if you wouldn't have a recovery cd deleting that partition would mean loosing your windows installer.

The benefit of vmware would be that you could run linux in windows.
Because you have the cd you shouldn't really worry about it.
Follow this installation guide and partition the 30GB space manually, the installer takes care of setting up the bootloader for you so can choose which OS to boot on startup. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Ninorcjw on 2006-11-04
I actually have an XP installation CD, but using the "Repair XP" would work right?

---

### Post by Ninorcjw on 2006-11-05
While attempting to install i get to the screen to manually partition the drive, there is one 80GB partition with windows on it, a 26GB where i want to put Ubuntu, the next screen shows 4 mount points, i chose a 3GB partition that was already there for the swap, the 26GB for the / and the 80GB(where windows is) part i put /windows, as shown [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing") there is also a 47Mb partition that im not sure what to do with, i left the name as it was and i get "No root file system" not sure what to do

---

