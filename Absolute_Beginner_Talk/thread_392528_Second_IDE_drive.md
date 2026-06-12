---
title: "Second IDE drive"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-03-24
A friend of mine has an 80 gb drive with ubuntu installed on it and it is the master drive and now  he added a second one(slave)...and i downloaded gparted and made a fat32 partition on the drive temporary before we install windows on it but when we click on it it says it can't be mounted.

 what we should do to be able to read/write on that drive?

AND

Also after we install windows on that second drive will we be able to choose what OS to use from the grub menu when the PC starts?

---

### Post by chewearn on 2007-03-24
Here is how I would do this:
1. remove the ubuntu HD, put the new HD in IDE master
2. install windows
3. put back the ubuntu HD in IDE slave
4. boot into ubuntu LiveCD, make the necessary additions / corrections to /boot/grub/menu.lst and /etc/fstab
5. set BIOS to boot to IDE slave

and you are good to go.

---

### Post by fasoulas on 2007-03-24
Can u descibe it in a simplier way so i can understand

---

### Post by chewearn on 2007-03-24
1. remove the ubuntu HD, put the new HD in IDE master
This means you physically unplug the ubuntu HD, plug in the new HD (set the jumper for the HD as master).  The ubuntu HD will stay unplugged from the PC during the next step, so there is no chance it will be overwritten by Windows.

2. install windows
Install Windows into the new HD.

3. put back the ubuntu HD in IDE slave
With th new HD now containing Windows in the PC, plug in the ubuntu HD (change the jumper for ubuntu HD to slave).

4. boot into ubuntu LiveCD, make the necessary additions / corrections to /boot/grub/menu.lst and /etc/fstab
Set the BIOS boot to CD/DVD-ROM, put the liveCD into the drive and boot.
At the liveCD desktop, mount you ubuntu harddisk, then edit the files

/boot/grub/menu.lst
Since the ubuntu harddisk has moved from hd0 to hd1, you need to change all related references.  Secondly, disable hiddenmenu and thirdly, add the entry for windows.

/etc/fstab
All references to ubuntu has moved from hda to hdb, though if UUID is used, then no change is required.  Also add entry for Windows in hda.


5. set BIOS to boot to IDE slave
Basically, you PC will now boot into IDE slave, right into grub, where you can select ubuntu or windows.

---

### Post by confused57 on 2007-03-24
Maybe this link will help also:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by chewearn on 2007-03-24
Hey, very impressive guide.
:popcorn:


Bookmarked for future reference.

---

### Post by confused57 on 2007-03-24
> **AstalaVista said:**
> Hey, very impressive guide.
:popcorn:


Bookmarked for future reference.

Thanks, the method you described would work also...it's just personal preference & choice for how someone wants to set up their dual boot.

---

