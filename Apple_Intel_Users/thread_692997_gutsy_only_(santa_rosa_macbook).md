---
title: "gutsy only (santa rosa macbook)"
date: 2008-02-10
forum: Apple Intel Users
---

### Post by digy79 on 2008-02-10
Hi all,

I have an only ubuntu 7.10 booting MacBook Santa Rosa (3,1 generation).
It works fine but my only problem is the boot. It is so slow!

When a push my MacBook power-on button it takes more than one minute before grub loads! I tried to install the grub-efi package from apt but the problem still remains...

May you help me?
Thx in advance!

---

### Post by lubeck on 2008-02-10
Had same problem on an Acer, and many people have reported this problem.  This solution seems to be the fix for most of us... [http://ubuntuforums.org/showthread.php?t=622836](http://ubuntuforums.org/showthread.php?t=622836)

---

### Post by cyberdork33 on 2008-02-10
> **lubeck said:**
> Had same problem on an Acer, and many people have reported this problem.  This solution seems to be the fix for most of us... [http://ubuntuforums.org/showthread.php?t=622836](http://ubuntuforums.org/showthread.php?t=622836)Not the same problem. He having a delay before grub even shows up.

Is this an Ubuntu-only install or are you dual booting with OSX? The EFI firmware has quite a delay looking for GPT bootable partitions on startup before it looks for a legacy MBR partition... Using Grub2 to boot directly via EFI is much more complicated then just installing the grub-efi package, if you can even get it to work at all.

---

### Post by digy79 on 2008-02-14
Hi guys and thanks for your answers.

@cyberdork33
When I started this thread there was only Ubuntu on my Sant Rosa MacBook.
I tried Grub2 installing it by apt, but nothing changed (my error, sure...), so I decided to use rEFIt. 
It works fine... This is what I have done:

I installed again macosx on the entire macbook disk, then I installed rEFIt on the hidden efi partition by using bless command in the macosx shell
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

Finally I installed Ubuntu Gutsy removing the macosx partition (using simply the installer). 
Now rEFIt starts at the macbook boot in a few seconds and launch Ubuntu through Grub.
I'm sure this is not the best procedure... but for now it works.

The most important thing is that you install rEFIt using the bless command!

---

### Post by cyberdork33 on 2008-02-14
> **digy79 said:**
> The most important thing is that you install rEFIt using the bless command!
Yea, you have to bless the EFI bootable item... Unfortunately, there is no Linux equivalent of Bless (yet). 

For future reference, you can install OS X on an external drive, and boot from that when you need to use OSX (for updates and such). This way, you don't have to take space on your internal hard drive, and you don't have to wipe your system to bless something! (course, I think you could have just ran bless from terminal on the Install DVD)

---

