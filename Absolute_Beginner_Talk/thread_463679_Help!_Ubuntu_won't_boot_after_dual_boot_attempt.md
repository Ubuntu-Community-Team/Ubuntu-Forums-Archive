---
title: "Help! Ubuntu won't boot after dual boot attempt"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-06-03
I'm typing this from the live disk cuz I can't get Ubuntu to boot anymore. I tried to install Windows XP on an unused IDE HD on my PC, but I didn't finish the install. I unplugged the SATA HD that has Ubunto on it while I did this so I know nothing was affected there. I searched and came up with a little info that I may need to edit the grub menu.list file, but I have to do this from the live CD. I was trying to do it with the GUI text editor, but I don't have the permission to edit it. I'm assuming I need to go into the terminal and use a command or something.............Any help is appreciated.

---

### Post by confused57 on 2007-06-03
Here's how to install grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I was just helping someone else with a setup similar to yours:
[http://ubuntuforums.org/showthread.php?t=463608](http://ubuntuforums.org/showthread.php?t=463608)
might be something useful in this thread

Your IDE drive is probably (hd0) and your SATA drive is (hd1)...grub was probably installed to your IDE drive's mbr.

---

### Post by blazini on 2007-06-03
OK, I tried that. I get "Error 17: Cannot mount selected partition". Pressing a key gives a couple grub options that don't work. The bios is setup with the IDE HD boot disabled, or it will boot into the partial Windows install.

---

### Post by confused57 on 2007-06-03
> **blazini said:**
> OK, I tried that. I get "Error 17: Cannot mount selected partition". Pressing a key gives a couple grub options that don't work. The bios is setup with the IDE HD boot disabled, or it will boot into the partial Windows install.

Using the live cd, did you install grub to hd0 or hd1?  If you selected "setup (hd1)", then you'll need to highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary, but you can edit your menu.lst to make it permanent.

You can still select to "setup (hd0)" to install grub IPL to your IDE mbr, this will overwrite your partial Window's install  on the IDE mbr...then you can enable your IDE drive to boot first.

---

### Post by blazini on 2007-06-04
ok, bear with me I'm not quite sure what I'm doing....

The "find /boot/grub/stage1" command returns "(hd1,0)"

When you say "press "e", change root from (hd1,x) to (hd0,x)", I assume you mean at the startup screen, right? And "(hd1,x)" the x represents the partition, not meaning that I type x right?

I tried setting up (hd0) from the terminal and got the same error 17 I got at boot up before. I'm gonna reboot and try doing like you said.

---

### Post by confused57 on 2007-06-04
> **blazini said:**
> ok, bear with me I'm not quite sure what I'm doing....

The "find /boot/grub/stage1" command returns "(hd1,0)"

When you say "press "e", change root from (hd1,x) to (hd0,x)", I assume you mean at the startup screen, right? And "(hd1,x)" the x represents the partition, not meaning that I type x right?

I tried setting up (hd0) from the terminal and got the same error 17 I got at boot up before. I'm gonna reboot and try doing like you said.
Correct, you'll change root from (hd1,0) to (hd0,0)...after using the live cd to "setup (hd1)"
When you highlight the line with "root (hd1,0)", you have to press "e" again to change it...I'm not sure if you have to press "enter", before pressing "b" to boot.

---

### Post by blazini on 2007-06-04
OK that worked, thanks for the help. If ya don't mind one last question.......

in the menu.lst file, I assume I need to change.......

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

to

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
 
but then there is.........
 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2a41e04a-c1a3-4306-b537-d20c22435753 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2a41e04a-c1a3-4306-b537-d20c22435753 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2a41e04a-c1a3-4306-b537-d20c22435753 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2a41e04a-c1a3-4306-b537-d20c22435753 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Should I change all of those entries to (hd0,0) too?

---

### Post by confused57 on 2007-06-04
Yes, you need to change the groot & all the root entries in your menu.lst to (hd0,0):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
always a good idea to make a backup, then to edit:
```
gksudo gedit menu.lst
```
quit & save

Glad it worked...

---

