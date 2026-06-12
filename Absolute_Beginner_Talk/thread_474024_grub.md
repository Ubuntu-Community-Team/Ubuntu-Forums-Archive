---
title: "grub"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by JerseyDevil1111 on 2007-06-14
What is the GRUB bootloader? In a dualbootable system which bootloader comes on in startup , the Linux or the XP loader?

---

### Post by shae on 2007-06-14
GRUB bootloader is the leading opensource program which is installed onto the Master boot record.  When you turn on the computer, this program is responsible for pointing to the computer where the operating system.  It also allows you to select which kernel image to load as well as select different operating systems in a dual boot environment.  When you turn on your computer, you see grub.

---

### Post by soul_motor on 2007-06-14
Is there any way to get the GRUB to load Windows as a default?  Ubuntu just doesn't want to work on the computer, and now I have to wait for the menu to pop up so I can start Windows :icon_frown:  Thanks in advance.

---

### Post by shae on 2007-06-14
Yes you can do so.  But it requires some text editing.  First open terminal and type:
```
sudo gedit /boot/grub/menu.lst
```

In the file, find near the top:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

For example, if XP is the second operating system, you change 0 to 1.

Click the save button in gedit and close.  When you reboot, Windows should be the default.

---

### Post by JerseyDevil1111 on 2007-06-14
Simply put, does GRUB co-opt the XP bootloader?

---

### Post by shae on 2007-06-14
Well sortof.  When you select to boot XP, Grub points the computer to XP bootloader.  The control of booting is taken over by grub until you select windows in grub at which point it goes to windows bootloader.

---

### Post by chiefboats on 2007-06-14
> Simply put, does GRUB co-opt the XP bootloader?

Yes.

If you want to return to the XP bootloader you can.

Put you WinXP CD in the drive and boot from it.

Choose the repair option and then the installation you want to repair. It will dump you out to a "C:\" prompt from which you can enter the command "fixmbr" and reload the XP boot loader on the mbr.

---

### Post by sailor2001 on 2007-06-14
changing default 0 to 1 DOES NOT put you into windows.  When booting up, count down from the 1st ubuntu (generic?) starting with 0 and count to your xp home edition (3? 5? 7?) Then change the default in sudo gedit /boot/grub/menu.lst to that #.

---

### Post by dreadlord_chris on 2007-06-14
> **JerseyDevil1111 said:**
> Simply put, does GRUB co-opt the XP bootloader?

More of less, Yes. Technically, the XP bootloader is still there - GRUB just superseeds it. If you choose XP at the boot menu, GRUB then passes control to the XP bootlooder. Usually, the last OS installed will install its own bootloader.

---

### Post by soul_motor on 2007-06-14
Is there a terminal function in Windows?  I can't get Ubuntu to load at all.  Thanks in advance.

---

