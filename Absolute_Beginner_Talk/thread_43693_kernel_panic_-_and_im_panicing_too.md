---
title: "kernel panic - and im panicing too"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by imboden on 2005-06-22
ok this is getting really frustrating.   


"kernel panic: IO-APIC + timer doesn't work! Try using the noapic kernel parameter"  

so something doesnt work in the kernel, and i have no idea how to fix it.. plz help.  i can get into the recovery console but thats as about as far as i get.

once again.. using 4.10 install.

---

### Post by desdinova on 2005-06-22
[QUOTE=imboden]ok this is getting really frustrating.   


"kernel panic: IO-APIC + timer doesn't work! Try using the noapic kernel parameter"  

so something doesnt work in the kernel, and i have no idea how to fix it.. plz help.  i can get into the recovery console but thats as about as far as i get.

once again.. using 4.10 install.[/QUOTE]
 [size=-1]If you are using **grub**, just press "e" and then add "**noapic**" to the end of the kernel
boot line - you can then login as root and add it to the grub menu.lst boot line
[/size]

---

### Post by imboden on 2005-06-22
ahhh fixed (so far)

---

### Post by desdinova on 2005-06-22
[QUOTE=imboden]ahhh fixed (so far)[/QUOTE]

You now need to edit yout boot (menu.lst in /boot/grub IIRC) and add that parameter to the end of the default choice so you don't need to do that anymore.

---

### Post by imboden on 2005-06-22
[QUOTE=desdinova]You now need to edit yout boot (menu.lst in /boot/grub IIRC) and add that parameter to the end of the default choice so you don't need to do that anymore.[/QUOTE]

and how does one do that??? remember, im new

---

### Post by Xian on 2005-06-22
[QUOTE=imboden]and how does one do that??? remember, im new[/QUOTE]
```
$ sudo gedit /boot/grub/menu.lst
```
Find the lines that looks similar to this (you will have a differently named kernel):
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-k7 
root		[hd0,8]
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda9 ro vga=791 quiet splash 
initrd		/boot/initrd.img-2.6.10-5-k7
```
And change the kernel line to read like this & save the file.
Note: Don't add everything in the line - just the 'noapic' part.
```
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda9 ro vga=791 noapic quiet splash
```

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=imboden]and how does one do that??? remember, im new[/QUOTE]

Sure. First you need to download this file:

[http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

and put it in your personal directory (/home/username/).

Then install it with this command in the terminal:

> sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb

to run it, put this command in the terminal:

> gksudo grubconf

Where it says "extra options" hit edit and add that noacpi command. Save, reboot and tell me how it works please!

---

