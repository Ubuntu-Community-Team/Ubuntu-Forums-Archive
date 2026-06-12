---
title: "once ubuntu is loaded, how do you load back to vista?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-10
ok, i posted before on how to dual boot. i was told that when you install ubuntu it will ask to alocate room on existing hard drive and will be able to boot.

so i have installed ubuntu successfully, now i would like to know how do you load vista back up once you have install linux onto the computer. or was i support to have a boot manager.

---

### Post by bodhi.zazen on 2007-04-10
If it is installed and properly configured, you don't :lolflag:


Actually, reboot your computer, unless you overwrote Vista, in which case you will be needing to re-install ...

---

### Post by JayDeePlus on 2007-04-10
so what if you just installed ubuntu, and told it to alocate room from existing partion. i thought it didn't format the hard drive if you did that.

---

### Post by ryckmonster on 2007-04-10
ubuntu should have detecting already installed operating systems, and added it to the grub boot loader.

when you restart, hit 'esc' when it gives you the option to, and then select windows.

---

### Post by xsprayx313 on 2007-04-10
It depends, The first option was to let ubuntu automatically do the partitioning, the 2nd one was to overwrite your current OS with ubuntu, the 3rd was to use all the freespace for the ubuntu partitioning and the last one was to manually do the partitioning. Do you remember which you chose?

---

### Post by JayDeePlus on 2007-04-10
i think it was the alocate free space. i tried the "esc" and i do not see vista or window. all i see is ubuntu and like ubuntu recovery. which one was the right one to choose

---

### Post by bodhi.zazen on 2007-04-10
Reeeeebooooot .....

If you can not boot to Vista, well open a terminal and post the output of this command :```
sudo fdisk -l
```

_Note_: That is a small "L" and not the number 1

That will give us a look at your partitions and if needed we can configure grub (or tell you if you are looking at a Vista Re-install ..... )

---

### Post by xsprayx313 on 2007-04-10
That's what I chose, When i reboot the computer it automatically comes to the GRUB screen where theres the list of OS's... I'm not sure if you mentioned that you did restart or not, sorry been a long day.

---

### Post by JayDeePlus on 2007-04-10
i mean automatically

---

### Post by JayDeePlus on 2007-04-10
> **bodhi.zazen said:**
> Reeeeebooooot .....

If you can not boot to Vista, well open a terminal and post the output of this command :```
sudo fdisk -l
```

_Note_: That is a small "L" and not the number 1

That will give us a look at your partitions and if needed we can configure grub (or tell you if you are looking at a Vista Re-install ..... )

this is what i get from that command

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1259    10112886    7  HPFS/NTFS
/dev/sda2            1260       13259    96390000    7  HPFS/NTFS
/dev/sda3   *       13260       19201    47729115   83  Linux
/dev/sda4           19202       19457     2056320    5  Extended
/dev/sda5           19202       19457     2056288+  82  Linux swap / Solaris

---

### Post by bodhi.zazen on 2007-04-10
You mean change the default OS when you (re)boot (from Ubuntu to Vista) ?

If that is the case, see here : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by JayDeePlus on 2007-04-10
when i hit "esc" when booting i do not see anything that say windows or vista.

---

### Post by JayDeePlus on 2007-04-10
still need help.

---

### Post by JayDeePlus on 2007-04-10
still need help.

---

### Post by bodhi.zazen on 2007-04-10
Post the file /boot/grub/menu.lst (and, since you appear to be bored, read the link on Grub I gave you while you are waiting for us volunteers to help).

---

### Post by JayDeePlus on 2007-04-10
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bodhi.zazen on 2007-04-10
Wow, that was fast posting ...

OK, in a terminal enter : ```
gksudo gedit /boot/grub/menu.lst
```

Add these lines at the end :

> title Windows Vista
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
boot

Reboot.

If that does not work, change the rootnoverify line to 

rootnoverify (hd0,1)

(I am not sure which partition is your C: partition)

---

### Post by alexlex on 2007-04-10
i am not sure if i am understanding this or not but what i have got is that in grub under the other operating systems it does not list anything. if this is the case you have probably overwriten your vista mbr (msater boot record) if this is the case then there are steps but it is kinda lengthy let me know if the above is true.

---

### Post by confused57 on 2007-04-10
bodhi.zazen made an honest typo, it's:
```
gksudo gedit /boot/grub/menu.lst
```

I hope you don't have this problem resizing Vista partition with gparted:
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)

---

### Post by JayDeePlus on 2007-04-10
bodhi

that code almost worked! it began to load vista, but it got to a black screen and the mouse became live and that was it i think. what does this mean?

---

### Post by JayDeePlus on 2007-04-10
help still needed

---

### Post by lamalex on 2007-04-10
try doing it again, I've often heard that the first boot back to a resized windows causes a freeze/bluescreen but if you do it twice it doesn't happen. Vista is new/not friendly with linux (picture Mike Tyson beating up Stephen Hawking) so you might run into some trouble, but try booting into it again and see what happens.

---

### Post by JayDeePlus on 2007-04-10
still the same thing. i even tried changing the default to vista, it goes to the microsoft loading screen. then like the screen loads or changes then i just see a black background and i'm able to move the mouse.

could there be a missing line to that code bodhi gave me?

---

### Post by JayDeePlus on 2007-04-10
still need support.

---

### Post by JayDeePlus on 2007-04-10
still need help. guru plzz

---

### Post by NeoGreen on 2007-04-10
Did you get an option to choose from Ubuntu and Windows Vista at the beginning?

---

### Post by lamalex on 2007-04-10
recap: he can chose vista from grub, but vista won't finish loading.

---

### Post by JayDeePlus on 2007-04-10
that is correct, able to see vista option in grub boot, vista is not able to finish boot. any suggestions?

---

### Post by WicKeDcHilD on 2007-04-10
im having the same problem, installed windows first then edgy and it wont get paste the Starting page and hangs...

---

### Post by JayDeePlus on 2007-04-10
still need help

---

### Post by confused57 on 2007-04-10
You could try adding an entry to boot your other NTFS partition:
```
title Windows Vista
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
boot
```
 
If this doesn't work and someone else doesn't have a solution, you "might" need to boot your Vista install DVD:
[http://gparted.free.fr/screenshots/VISTA/Howto_move_VISTA.html](http://gparted.free.fr/screenshots/VISTA/Howto_move_VISTA.html)

see the screenshots for repairing your Vista

---

### Post by JayDeePlus on 2007-04-10
would that 1 work?

---

### Post by lamalex on 2007-04-10
try it and find out.

---

### Post by confused57 on 2007-04-10
> **JayDeePlus said:**
> would that 1 work?
If it doesn't work, and you don't have an install DVD,  you might read over the owner's manual that came with your computer & see if there is a way to enter a possible Recovery Console...possibly by press F8 or some other key that may allow you to access it.  You might want to contact the computer manufacturer & insist on an installation cd/dvd for your computer.

Added:  You might want to read over this "fix", if that's your problem:
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

---

### Post by lamalex on 2007-04-11
if they try and make you pay, don't stop arguing until they send it for free. They will. You just have to show em who's boss!

---

