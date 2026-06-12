---
title: "Damnit, I broke GRUB..."
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-11-12
Please help...

I was using this howto to get a graphical grub...

[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

and Now I can't see GRUB at all or get into UBUNTU...but I can get Windows...

Please help me...how do I get back into Ubuntu?

---

### Post by apjone on 2005-11-12
hmmm did you set windows as your default o/s???

---

### Post by idn on 2005-11-12
Does grub load at all?  Or does it go straight to windows? Can you see a 'press esc to view' and the time count down?

---

### Post by darth_vector on 2005-11-12
can you boot into single user mode? if so, do this and undo the changes you made to /boot/grub/menu.ls

EDIT: try booting from your live cd, mounting the relevant ubuntu partition (/boot if you have one or / otherwise) and correcting the changes.

---

### Post by lavarock09 on 2005-11-12
Thanks for your help guys, I've fixed...it just decided to work...

But I have another question...

In GRUB I have 6 options...

5 of them are for ubuntu...

This is because I updataed Ubuntu earlier today and It now shows the old one and the new one and my windows XP...

The other options are the recovery etc..

How can I remove the extra ubuntu one? Do I just delete the stuff from /boot/grub/menu.lst?

---

### Post by manicka on 2005-11-12
yes

---

### Post by Xian on 2005-11-12
Or you could just comment them out if the kernel(s) are still installed.
Nice to have backup entries ready if ever needed.

What you comment out will not show up in the grub menu.

---

### Post by Mustard on 2005-11-12
You can tidy it up if you like, but I would make a backup of the menu.lst prior to doing so.  Should you make an error and find yourself in trouble it will come in handy.

An easy command to backup the menu.lst is

```
sudo cp /boot/grub/menu.list /boot/grub/menu.list_backup
```

---

### Post by lavarock09 on 2005-11-12
Thanks for you help everyone...

Problem Solved

---

