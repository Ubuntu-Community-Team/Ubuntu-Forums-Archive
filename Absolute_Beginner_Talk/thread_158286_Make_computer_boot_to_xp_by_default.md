---
title: "Make computer boot to xp by default"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by osama1234 on 2006-04-10
Hi,
i've tried some searches, however am having troubles finding a solution.
I have installed ubuntu, but as you can imagine am more comfortable in windows. So when my computer starts up, i would like it to boot to xp by default, instead of ubuntu. How can i make the default selection in the OS selection screen be xp instead of linux?

Thanks a baker's dozen. (thanks 13 times, for the cost of 12)

---

### Post by aysiu on 2006-04-10
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by osama1234 on 2006-04-10
Great! thanks.

---

### Post by Buffalo Soldier on 2006-04-10
note: NUMBER = the order of the **title** entry on the menu. For example if WinXP is the fifth entry on the menu then your number should be 4. (**start counting from 0**).

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
[color=red]default		**4**[/color]

**title**		Ubuntu, kernel 2.6.10-5-686 [color=red]<- first entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel 2.6.10-5-686 (recovery mode) [color=red]<- second entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel memtest86+ [color=red]<- third entry[/color]
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
**title**	Other operating systems: [color=red]<-  fourth entry[/color]
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
**title**		Microsoft Windows XP Home Edition [color=red]<- fifth entry[/color]
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by btnheazy03 on 2006-04-21
[QUOTE=Buffalo Soldier]note: NUMBER = the order of the **title** entry on the menu. For example if WinXP is the fifth entry on the menu then your number should be 4. (**start counting from 0**).

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
[color=red]default		**4**[/color]

**title**		Ubuntu, kernel 2.6.10-5-686 [color=red]<- first entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel 2.6.10-5-686 (recovery mode) [color=red]<- second entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel memtest86+ [color=red]<- third entry[/color]
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
**title**	Other operating systems: [color=red]<-  fourth entry[/color]
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
**title**		Microsoft Windows XP Home Edition [color=red]<- fifth entry[/color]
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```[/QUOTE]
Thanks for the information \\:D/

---

