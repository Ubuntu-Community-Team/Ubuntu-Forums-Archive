---
title: "Installed video card drivers, and now I get a black screen. How do I fix it?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-03-24
I installed ubuntu, downloaded the drivers from the repository for my ATI 8500 card,
ran the command to edit the monitor (widescreen) resolutions etc, and now I get a black screen.
There is no signal going to the monitor.

What do I do? Just re-install ubuntu? Running Live CD at the moment

---

### Post by 1/0 on 2007-03-24
You should boot into recovery mode. Then you could copy the backup (xorg.conf.*.backup) in /etc/X11 to /etc/X11/xorg.conf. Make a copy first though!

Otherwise you could simply do:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ROUBOS on 2007-03-24
How do I enter recovery mode.??? Sorry.. noob here

---

### Post by 1/0 on 2007-03-24
You should have that choice in GRUB when you boot up. Press 'Esc' when the GRUB menu shows and you'll get some options.

If the above commands don't work, you could always:
```
sudo apt-get install --reinstall xserver-xorg
```

---

### Post by ROUBOS on 2007-03-24
Problem is that I have a USB cordless mouse and keyboard, and even though I have USB support enabled in BIOS, it does not detect it and I cannot hit ESC to enter menu...

I'll just re-install but how do I get the drivers for my card? Use ATI website or the repository?
Detecting the monitor in Digital mode is a problem

---

### Post by ROUBOS on 2007-03-24
It's simple things like these that are hard to setup and put me off linux everytime I install it.

---

### Post by 1/0 on 2007-03-24
The USB keyboard/mouse needs to be enabled in BIOS and GRUB that's probably why. No extra PS/2 keyboard or adapter available? 

Otherwise you could try to boot and hit ctr + alt + F2 and see if you can login in terminal mode. If you got another computer you could try to SSH in to it via terminal or putty (for Windoze).

---

### Post by ROUBOS on 2007-03-24
how do you enable the keyboard in grub?

---

### Post by 1/0 on 2007-03-24
You could also chroot into your drive from Knoppix or a liveCD.

First you create a folder, for instance:
```
mkdir /mnt/ubuntu
```
Then you mount the drive (the number can differ):
```
mount /dev/hda1 /mnt/ubuntu
```

Then chroot in to the drive:
```
chroot /mnt/ubuntu
```

You should be able to do the commands from there. Then exit and issue:
```
umount /mnt/ubuntu
```

Depending on distro these commands are done as root. This is done by typing su - and enter or simply by putting sudo in front of each command.

---

### Post by 1/0 on 2007-03-24
It should be the BIOS that's causing this. In that case enter the BIOS menu by pressing delete at start (the key depends on the main board).

Then look for USB legacy support or something similar. It should be enabled.

---

### Post by 1/0 on 2007-03-24
The weather is nice outdoors so, I'm hidding out over the day. Just so you know. I'll check in later tonight. Good luck with everything! You shouldn't need to reinstall. Google if in doubt or search the forum.

---

### Post by 1/0 on 2007-03-26
Any solution?

---

