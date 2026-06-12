---
title: "Things are fast going from bad to worse..."
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by atxformat on 2006-09-07
My original problem was that the computer locked up after a reboot, stopping at "Configuring Networking Interface."  Now, it stops even before that because it says my video card isn't configured correctly (something, something GDS X...).  It won't let me boot up to configure it or anything.  Any clues?  I've reinstalled Ubuntu about 4 times tonight, and I might be going for a fifth.

---

### Post by nalmeth on 2006-09-07
What kind of network device are you using? What kind of video card do you have?

Does it say GDM / X?

When grub is loading (right after your BIOS at boot) hit ESC for the GRUB menu and pick recovery mode

Enter:
```
sudo apt-get update
sudo apt-get upgrade
```

If this doesn't solve the problem, repeat, and enter:
```
sudo dpkg-reconfigure xserver-xorg
```
pick VESA for the video driver

---

### Post by orb9220 on 2006-09-07
Can't have clues without info. Need system specs and description of type of install you are trying to do.
cpu
ram
video card
network are some of the info needed.

---

