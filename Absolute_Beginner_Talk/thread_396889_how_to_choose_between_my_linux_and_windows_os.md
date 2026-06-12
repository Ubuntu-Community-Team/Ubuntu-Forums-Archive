---
title: "how to choose between my linux and windows os"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by endo666 on 2007-03-30
ok i installed ubuntu and my computer boots rite to windows. i tried to to change the boot order so that i could boot from my linux hard drive but it said grub error 17 or 37. what do i need to do.

---

### Post by nixclusive on 2007-03-30
Try pressing ESC repeatedly while the system is powering on. You should see a menu. If that doesn't work -- let us know.

---

### Post by seshomaru samma on 2007-03-30
need more information
did you finish the installation?
how many drives do you have (2 perhaps?)
where did you install GRUB (the boot menu) ?

I suspect you didn't install Grub to the MBR but installed it on the Linux drive

The easiest way to solve it - is to reinstall Grub -this time to the MBR
like this :
How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal.

3. Type "sudo grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by endo666 on 2007-03-30
ya i have windows xp installed to my main boot disk. i have another hard drive for storage and now i want to install linux to a third hard drive. i never saw my computer ask me where to install GRUB so i dont know where it is installed to. and from what i understood it completely installed.

---

### Post by kahrytan on 2007-03-30
Change the bios settings so the Linux drive or the storage drive boots first, whichever has the Grub installed.

---

### Post by nixclusive on 2007-03-30
Changing the positions of the drives wrt Master/Slave configurations will change the creation of /dev/ nodes as well. you may need to reconfigure grub and edit /etc/fstab as well after that!!

---

### Post by endo666 on 2007-03-30
tried that. i switched it so that my linux drive would boot first and all it says is grub error 17.

---

### Post by Doug11 on 2007-03-30
> **seshomaru samma said:**
> need more information
did you finish the installation?
how many drives do you have (2 perhaps?)
where did you install GRUB (the boot menu) ?

I suspect you didn't install Grub to the MBR but installed it on the Linux drive

The easiest way to solve it - is to reinstall Grub -this time to the MBR
like this :
How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal.

3. Type "sudo grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.


I always found that in step 6, if I went > setup (hd0,3) < I could not get my grub boot menu up. I had to do the > setup (hd0)<without the commaand extra number and grub would install to the MBR and would have a complete boot menu to choose from.

---

### Post by STREETURCHINE on 2007-03-30
the esiest way i found was to press f11 continually when starting the computer,this should then give you the option of which hard drive to boot,but that is the way i set it up it may not work for you but worth a try.

---

### Post by seshomaru samma on 2007-03-30
> **endo666 said:**
> tried that. i switched it so that my linux drive would boot first and all it says is grub error 17.


did you try reinstalling grub?

---

### Post by endo666 on 2007-03-30
no i havent been able to try to install just grub again i will try some time after i get off work.

---

