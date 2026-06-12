---
title: "how to back up my themes"
date: 2008-03-18
forum: Apple PPC Users
---

### Post by Venom_Man on 2008-03-18
i currently have fiesty running and i want to reinstall  OS X  so i have to repartition my drive into two seperate parts and i want ubuntu on one and tiger on the other. so it reparation it have to wipe the drive clean and start over. All i really want to keep is my themes and icons and window boarders. where can i find those  to backup. andy help would be greatly appreciated.

---

### Post by ajgreeny on 2008-03-18
Not certain about using macs as opposed to windows PCs but you shouldn't need to wipe and reinstall Ubuntu.  In windows you would simply reduce your Ubuntu partition size to make room for windows and then install windows.  OK, you would lose your grub but it is very easy to add it back after.  Perhaps mac is different, or doesn't even use grub, I really don't know, and if I'm wrong, I apologise for wasting your time.

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> i currently have fiesty running and i want to reinstall  OS X  so i have to repartition my drive into two seperate parts and i want ubuntu on one and tiger on the other. so it reparation it have to wipe the drive clean and start over. All i really want to keep is my themes and icons and window boarders. where can i find those  to backup. andy help would be greatly appreciated.

You should be able to make a backup copy of the .icons and .themes directories in your home folder.  Burn them to a disk or copy to a flash drive, once you've reinstalled you can just copy them back to your home directory.

---

### Post by Venom_Man on 2008-03-18
how would i go about doing this. i have gparted installed but when i click my drive i have ubuntu on it has a lock next to it so i cant resize it. if i could do it this way it would be way eaiser and perfered.

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> how would i go about doing this. i have gparted installed but when i click my drive i have ubuntu on it has a lock next to it so i cant resize it. if i could do it this way it would be way eaiser and perfered.

I think you will have to boot from a live-CD if you want to resize your partition.  I don't think you can resize it while it's mounted.  [GParted]("http://gparted.sourceforge.net/") has a live-CD you can download and burn.

---

### Post by Venom_Man on 2008-03-18
> **ajgreeny said:**
> Not certain about using macs as opposed to windows PCs but you shouldn't need to wipe and reinstall Ubuntu.  In windows you would simply reduce your Ubuntu partition size to make room for windows and then install windows.  OK, you would lose your grub but it is very easy to add it back after.  Perhaps mac is different, or doesn't even use grub, I really don't know, and if I'm wrong, I apologise for wasting your time.
ok i have gparted running from a live cd but it is still telling me that i can resize the partion. am i doing something wrong or not doing something i should be

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> ok i have gparted running from a live cd but it is still telling me that i **can** resize the partion. am i doing something wrong or not doing something i should be

If it is telling you that you can resize then what's the problem?  Check out the documentation.  [http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by Venom_Man on 2008-03-18
it is telling me i can resize it but when i click apply iget an error that says /dev/sdb3 is mounted

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> it is telling me i can resize it but when i click apply iget an error that says /dev/sdb3 is mounted

While running from the live CD, right click on /dev/sdb3 and click unmount.  Then try to resize it.

---

### Post by Venom_Man on 2008-03-18
thank you for being patient with me im kinda new to the linux sceene and this was a great help. its still resizing the drive but i think its ganna work i got past the initial spot where i got the error before. Thanks again

---

### Post by Cybergod on 2008-03-18
I hope all is well now :)

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> thank you for being patient with me im kinda new to the linux sceene and this was a great help. its still resizing the drive but i think its ganna work i got past the initial spot where i got the error before. Thanks again

No problem, that's what this community is for (to help each other out).  If you have any more trouble post back and I'll try to help.

---

### Post by Venom_Man on 2008-03-18
well my next endeavor will be installing tiger on the new open disk room that i just freed up so if i run into problems ill post back

---

### Post by Venom_Man on 2008-03-18
already ran into a problem. i now have 50 gb of open disk space on my hard drive. i formated it to fat32 and i stuck in a OS x install disk and was going through the install steps and i got to the step of selecting a destination for os x. OS X did not see  my new partition. is it because its a fat32 format? should it be something else?

---

### Post by Cybergod on 2008-03-18
> **Venom_Man said:**
> already ran into a problem. i now have 50 gb of open disk space on my hard drive. i formated it to fat32 and i stuck in a OS x install disk and was going through the install steps and i got to the step of selecting a destination for os x. OS X did not see  my new partition. is it because its a fat32 format? should it be something else?

I've never installed OS X so I really have no idea but I would guess it doesn't use fat32.  Once you resized your Ubuntu partition, you should have left the free space unformatted that way the OS X installer could create its own partition with the free space.  I would boot with the gparted live CD and delete the partition you created for OS X and let the installer create what it wants.

---

### Post by Venom_Man on 2008-03-18
i tired leaving it open space at first and it didnt't find it either so ill play around with it some more tomorrow.

---

