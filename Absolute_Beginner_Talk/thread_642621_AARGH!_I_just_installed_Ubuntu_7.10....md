---
title: "AARGH! I just installed Ubuntu 7.10..."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by geardawg on 2007-12-16
...and I boot it up, and it goes to a command prompt, which won't respond. I deleted it and want to do a complete reinstall. I tryed the CD, didn't work, try the Wubi thing, and it crapped out on me. Can someone help please? I can't find the article in the wiki... :evil:

---

### Post by Pumalite on 2007-12-16
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Vadi on 2007-12-16
Could you post what happened when you tried other things?

---

### Post by lamalex on 2007-12-16
What cd are you using to install? Is it the live cd, or the alternate? Is it one you burned or an official one you were given/ordered?

---

### Post by geardawg on 2007-12-16
Okay, I read about the LIVE thing, I tryed that, and it sticks in one place. Is it normal or is it bad?

---

### Post by geardawg on 2007-12-16
> **Iamalex said:**
> What cd are you using to install? Is it the live cd, or the alternate? Is it one you burned or an official one you were given/ordered?
Live; Burned

---

### Post by lamalex on 2007-12-16
Have you run the option to check cd for defects? Trying running that and make sure you did a good burn, you may also want to use the alternate install cd if you're sure you want to install. The live is good for playing with if you're not sure you want to install (i.e. have never seen/used Ubuntu), but the alternate is much faster if you already know you're going to install it.

---

### Post by geardawg on 2007-12-16
> **Iamalex said:**
> Have you run the option to check cd for defects? Trying running that and make sure you did a good burn, you may also want to use the alternate install cd if you're sure you want to install. The live is good for playing with if you're not sure you want to install (i.e. have never seen/used Ubuntu), but the alternate is much faster if you already know you're going to install it.
I want to install it, I used Wubi the 2nd time, and it worked until it got past the boot screen, and it turned into a command prompt. I tryed typing something, and it wouldn't work.

---

### Post by perixx on 2007-12-16
Well, after installing it, have you tried to press
CTRL+ALT+F7?

Because I had exactly the same problem with Gutsy (using Feisty again now). You can switch between the X-terminal (key-combo above) and the different virtual desktops (CTRL+ALT+F1-F4, I believe). 

You could also try to go into virtual Terminal and enter 'startx' or 'sudo /etc/init.d/gdm restart'. If that doesn't work, try not touching any of the boot-options (means changing resolution or similar). Or the other way round, select a lower resolution.

Btw., somehow my Grub-installation went wrong when installing Gutsy and Grub didn't create the right entries into /boot/grub/menu.lst. You might check that and edit the file as needed from your Live-CD, e.g.:
> # Linux bootable partition config begins
  title Xubuntu 7.10 Gutsy (on /dev/hda5)
  root (hd0,4)
  kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/[COLOR="Red"]hda5[/COLOR] ro vga=normal quiet splash
  initrd=/boot/initrd.img-2.6.22-14-generic
  boot
# Linux bootable partition config ends
You've got to refer to what your kernel-version is, in /boot... another way to find out the kernel-version in use is typing ```
uname -r
``` in a terminal.

Of course, you'll have to change the lines to mach your partition setup (e.g. root (hd[COLOR="Green"]1[/COLOR],[COLOR="Blue"]0[/COLOR]) if it's on the [COLOR="Green"]2nd[/COLOR] HDD, [COLOR="Blue"]1st[/COLOR] partition). Note, that the kernel-path is differently coded: [COLOR="Red"]/dev/hda1[/COLOR], for partition 1, in this example; when using [COLOR="MediumTurquoise"]SATA[/COLOR]-drives, you've got to use the term /dev/[COLOR="MediumTurquoise"]SDA1[/COLOR] instead!

Oh, and verify, that all files from your /usr/lib/grub/x86xxxx folder reside in your /boot/grub folder (but don't overwrite your menu.lst)!

Good luck!

P.S. if you wait 2-3 minutes, does the login-screen still not show up? Just figured it might be this problem:
[http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time]("http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time")


perixx

---

### Post by geardawg on 2007-12-16
If it helps, I use a HP Pavilion 6746c. 
I might try the Wubi Installer agian.

---

### Post by geardawg on 2007-12-17
Okay, I tried Wubi again, and it installed off of Windows 2000. Again, if it helps, I have a HP Pavilion 6746c, it has a 733mHz Intel Celeron, and 64MB of RAM.

---

### Post by Pumalite on 2007-12-17
With 64 MB of RAM, you should stick to a smaller distro like DSL or Puppy. Memory is cheap now a days.

---

### Post by geardawg on 2007-12-17
Which one would that be? And memory may be cheap, but a new computer to hold it is not cheap. :(
Yes, my dump-on-the-side-of-road machine can only hold 64. :( :( :(

---

### Post by Pumalite on 2007-12-17
Google Damn Small Linux and Puppy.

---

### Post by crjackson on 2007-12-17
> **Pumalite said:**
> With 64 MB of RAM, you should stick to a smaller distro like DSL or Puppy. Memory is cheap now a days.

With those specs, you really should try Puppy Linux.

---

### Post by agurk on 2007-12-17
I believe the Pavilion 6746c can handle up to 512 MB, though it came with 64 MB and one empty memory slot. Get some more RAM if you can afford it.
Anyway, as suggested, going with a more suitable (lean and mean) distro should let you get better performance out of your computer.

---

