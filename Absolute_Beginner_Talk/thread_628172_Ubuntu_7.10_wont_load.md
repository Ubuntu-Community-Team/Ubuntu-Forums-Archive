---
title: "Ubuntu 7.10 wont load"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Rings on 2007-11-30
I just tried installing ubuntu on my computer

AMD 64 4400
Nvidia GeForce 8500GT 512
1024 Megs of Ram

I had to use the alternate CD to get the initial install working.

When booting normally the screen turns off.
When booting in recovery mode I get the command prompt. I already adjusted my settings using

sudo dpkg-reconfigure xserver-xorg

When I enter startx the screen goes blank and nothing happens. I read about something called Envy, but I don't have a internet connection setup on this machine yet so I can not download it.

---

### Post by Nano Geek on 2007-12-01
It could be that something went wrong during the installation. First check the CD for errors, and if that passes, reinstall.

---

### Post by sethvath on 2007-12-01
boot with the options: acpi=routeirq noapic and remove the quiet option

---

### Post by Rings on 2007-12-01
I just entered the command lines you gave me and booted.

My monitor still went into standby. I can hear the hard drive working like it is loading.

I am using a Sharp LL-173C-B LCD monitor

I checked the refresh rate and the horizontal scale on the back of the monitor and they match up with my xorg.conf file.

---

### Post by sethvath on 2007-12-02
Is this the same issue you have? [http://ubuntuforums.org/showthread.php?t=611318](http://ubuntuforums.org/showthread.php?t=611318) (look at the last post for solution)

---

