---
title: "Help! Invalid compressed format (err=2)"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gator_grabber on 2007-06-16
I just downloaded Ubuntu 7.04 for 64-bit AMD. The OS ran fine from the CD, so I repartitioned 120G of my secondary drive (D drive) for the install and another 2G for a swap file. The install seemed to go well, but I get the following message when booting from the hard drive, " Invalid compressed format (err=2)". Searching the groups indicated there may be a problem with the disk I burned, so I burned a second copy at slow speed and then error checked it. This CD will also boot ubuntu just fine. I then tried to reinstall the OS, but nothing happened when I clicked the 'Install' icon.

Since I'm new to linux, what should I do next to fix my problem? I don't want to just crash around and make things worse. Any words of wisdom? Yes, I'm still searching the forums...

My system is a 64-bit AMD, 1.8 with 1G of ram (which I also tested), all mounted on an ASUS MB

---

### Post by plcdfa on 2007-06-16
When do you get that error message, before seeing the grub menu, or after selecting Linux from it? Also, what do you mean by "nothing happens"? Try running the install program from a terminal emulator and see what message it spits out there. I don't know its name, but you can probably see it if you right click on its icon and select properties. (?) I'm really not sure of this though, cause I use KDE. 
But here's a real "word of wisdom": try the i386 version instead. It will run equally well on your machine, and a lot of things are easier to set up on that then on the 64 bit edition. Also, you wouldn't feel any difference in performance most of the time anyway. I also have an Athlon64 system, but I'm using the 32 version, I don't intend to migrate till all the packages will be available for this architecture as well. If that cd doesn't work either, then you can still try the text-mode alternate install cd.

---

### Post by gator_grabber on 2007-06-16
During boot I get an OS menu. If I choose anything but MS XP Pro, I get the "Invalid" message. Ubuntu loads just fine if I boot from the CD, but clicking the desktop "Install" icon now does nothing. What is the correct procedure for using the terminal emulator? At what point do I bail on the 64 bit version and go with the i386? Please remember I'm new to Linux. Thanks.

---

### Post by plcdfa on 2007-06-16
I think the name of the terminal emulator is gnome-terminal, just select it from the applications menu, and you'll get a command line in a window. Just type the name of the installer program there. Also, do you see the ubuntu boot splash screen or not before the boot fails? If you do please press ctrl+alt+f1 to swithch to a console with all the boot messages to see exactly where the problem is, and post it here. Also, you'll have to download a different cd for the i386 version, the install proces is exactly the same.

---

### Post by gator_grabber on 2007-06-16
Well, it looks like the 3rd try was the charm. I loaded from the CD again and hit 'install'. This time it worked and everything seems to have loaded properly. There are now no errors during boot. I guess I wasn't holding my jaw correctly during the 1st install...:) Thanks!

---

### Post by plcdfa on 2007-06-16
Ok, at least it worked out ok finally, even tough I'm curious what was the problem.

---

