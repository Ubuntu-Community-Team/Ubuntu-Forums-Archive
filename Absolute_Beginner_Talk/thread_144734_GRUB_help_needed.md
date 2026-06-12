---
title: "GRUB help needed"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by GregJKy on 2006-03-14
Any help would be greatly appreciated...  I'm new to Ubuntu and LOVING it!  I just have this one GRUB configuration issue I can't seem to fix...  

Ubuntu boots fine, but WinXP doesn't unless I go through the steps below which were found after many hours of trial and error...

First an overview:
The first hard drive is a SATA (sda) with WinXP installed using the entire drive and this is the drive the BIOS wants to boot by default.  The second hard drive is an IDE (hda) with Ubuntu taking the entire drive.

Ubuntu boots up just fine every time with the following GRUB config in menu.lst:

```

title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot
```


WinXP is the one giving me problems with this GRUB config:
```

title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

To get WinXP to boot I have to follow these steps every time:
1) Try to boot WinXP and get this error: "Error 13: Invalid or unsupported executable format".  I hit a key to clear the error and go back to the GRUB menu.
2) I edit the first line in GRUB changing it from (hd1,0) to (hd1) and tell it to boot.  I then get another error that flashes on the screen too quickly to capture and it takes me back to the GRUB menu.
3) At this point, I try to boot XP again and it works even though it's back to (hd1,0) and that didn't work the first time...

Any suggestions?  Obviously, it doesn't look right to me that both hard drives are listed as (hd1,0) but it does work after the steps above.  I'm suspecting the map commands...  Thanks for your help!!!

---

### Post by dermotti on 2006-03-15
map		(hd0) (hd1)
map		(hd1) (hd0)

to

map		(hd1) (hd0)
map		(hd0) (hd1)


worth a shot :-)

---

### Post by lha on 2006-03-15
[QUOTE=GregJKy]Any help would be greatly appreciated...  I'm new to Ubuntu and LOVING it!  I just have this one GRUB configuration issue I can't seem to fix...  

Ubuntu boots fine, but WinXP doesn't unless I go through the steps below which were found after many hours of trial and error...

First an overview:
The first hard drive is a SATA (sda) with WinXP installed using the entire drive and this is the drive the BIOS wants to boot by default.  The second hard drive is an IDE (hda) with Ubuntu taking the entire drive.

Ubuntu boots up just fine every time with the following GRUB config in menu.lst:

```

title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot
```


WinXP is the one giving me problems with this GRUB config:
```

title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

To get WinXP to boot I have to follow these steps every time:
1) Try to boot WinXP and get this error: "Error 13: Invalid or unsupported executable format".  I hit a key to clear the error and go back to the GRUB menu.
2) I edit the first line in GRUB changing it from (hd1,0) to (hd1) and tell it to boot.  I then get another error that flashes on the screen too quickly to capture and it takes me back to the GRUB menu.
3) At this point, I try to boot XP again and it works even though it's back to (hd1,0) and that didn't work the first time...

Any suggestions?  Obviously, it doesn't look right to me that both hard drives are listed as (hd1,0) but it does work after the steps above.  I'm suspecting the map commands...  Thanks for your help!!![/QUOTE]

Ubuntu boots fine? So that entry is correct and grub sees hda as (hd1). This means sda is (hd0). In Ubuntu, open terminal (Applications->Accessories->Terminal) and type following commands
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and add following lines to the end of the file:
```

title		Windows XP Media Center Edition (with better luck, hopefully)
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by mlind on 2006-03-15
I had the same problem when GRUB was installed on my SATA drives MBR.
I couldn't get it to work so I could boot on windows, just like you.

I made my old IDE drive as first bootable device and installed GRUB there and
it worked fine. I dunno why it didn't my SATA drive.

---

### Post by GregJKy on 2006-03-15
Thanks guys!  I'll give the suggestions a try as soon as I get home to the machine.

---

### Post by GregJKy on 2006-03-15
[QUOTE=lha]Ubuntu boots fine? So that entry is correct and grub sees hda as (hd1). This means sda is (hd0). In Ubuntu, open terminal (Applications->Accessories->Terminal) and type following commands
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and add following lines to the end of the file:
```

title		Windows XP Media Center Edition (with better luck, hopefully)
root		(hd0,0)
savedefault
chainloader	+1
```[/QUOTE]

This suggestion did the trick!  \\:D/  Thanks for everyones help!!!

---

