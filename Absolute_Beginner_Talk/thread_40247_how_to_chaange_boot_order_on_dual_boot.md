---
title: "how to chaange boot order on dual boot"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by MrSandman on 2005-06-08
hi all, first off i would like to say what a great distro ubuntu, it is the only distro i found the installs and configures my inspirion 6000. after trying the live version i had to run install the distro. 
now my question is, how do i change the bootloader so that windows is the default OS to boot?

thanks in advance.

---

### Post by davidmigl on 2005-06-08
[QUOTE=MrSandman]hi all, first off i would like to say what a great distro ubuntu, it is the only distro i found the installs and configures my inspirion 6000. after trying the live version i had to run install the distro. 
now my question is, how do i change the bootloader so that windows is the default OS to boot?

thanks in advance.[/QUOTE]
 First make a backup of the file you will need to modify.  Browse to /boot/grub/ and copy 'menu.lst' to the desktop.

Now, in a terminal type:
```
sudo gedit /boot/grub/menu.lst
```[/code]

Toward the bottom of the document you'll find the entries for the operating systems that should look somewhat like this:

```
title PLD Live
	root (hd0,2)
	kernel /boot/vmlinuz root=0303 vga=791 video=vesafb:ywrap,mtrr noapic acpi=off i8042.nomux
	initrd /boot/initrd

title WinXP
	root (hd0,0)
	chainloader +1
```

Take the OS you want to default boot (in this case windows) and cut and paste it's entry before all the other entries.  While you're at it, you might want to delete the 'other operating systems' entry since it really doesn't serve much of a purpose.  Save the file, and you're done.

---

### Post by MrSandman on 2005-06-08
thanks for the quick reply and great support. that is exactly what i was looking for and now the wife will be happy (she loves windows ;-) ) 

thanks again

---

