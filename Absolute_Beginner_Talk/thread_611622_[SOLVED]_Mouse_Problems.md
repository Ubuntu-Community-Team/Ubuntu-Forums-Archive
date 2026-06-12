---
title: "[SOLVED] Mouse Problems"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-11-13
a few weeks ago i started experimenting a little with my notebook, with adding another monitor, editing xorg, and so on. i killed it. so... as usual in times of the slightest glitch i reformatted (and yes i am using ubuntu gutsy). 

now my mouse wont work, but its not every one, my internal mouse (the one build into the keyboard) works! but that thing sucks! so i have another mouse i use, its usb, and it works on all my other computers, and worked on this one before i reformatted!

HELP!!!

---

### Post by Paul820 on 2007-11-13
Does it show up when you type **lsusb** in the terminal?

---

### Post by kevin11951 on 2007-11-13
that was the only thing plugged in, and yet i got this response:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

um... makes no sence to me!

---

### Post by Paul820 on 2007-11-13
Here is some info on configuring your mouse [https://help.ubuntu.com/community/ManyButtonsMouseHowto]("https://help.ubuntu.com/community/ManyButtonsMouseHowto")

---

### Post by kevin11951 on 2007-11-13
i figured it out!

all i had to to was change the 3 button emulation 'False' in xorg.conf!

---

### Post by erginemr on 2007-11-13
> **kevin11951 said:**
> a few weeks ago i started experimenting a little with my notebook, with adding another monitor, editing xorg, and so on. i killed it. so... as usual in times of the slightest glitch i reformatted (and yes i am using ubuntu gutsy). 

now my mouse wont work, but its not every one, my internal mouse (the one build into the keyboard) works! but that thing sucks! so i have another mouse i use, its usb, and it works on all my other computers, and worked on this one before i reformatted!

HELP!!!

Can you please post the contents of your /etc/X11/xorg.conf file here, esp. the section related to the mouse?

But the outcome of the lsusb command:

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

indicates that Ubuntu cannot detect the mouse at all. If you have more than one usb slot, you may try inserting the mouse into the slot and retry "lsusb".

---

### Post by erginemr on 2007-11-13
> **kevin11951 said:**
> i figured it out!

all i had to to was change the 3 button emulation 'False' in xorg.conf!

OK, then. But I would suggest you not to reinstall Ubuntu every time you run into a problem. You will learn much more about your system, if you abide by and try to resolve the issue as you just did.

You may also consider having regular copies of your important configuration files such as /etc/X11/xorg.conf, /etc/fstab and /boot/grub/menu.lst, via say;

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_rev1  ...rev2, rev3,etc,

This way, you can save your system easily in case of a problem.

Happy Ubunt'ing!

---

