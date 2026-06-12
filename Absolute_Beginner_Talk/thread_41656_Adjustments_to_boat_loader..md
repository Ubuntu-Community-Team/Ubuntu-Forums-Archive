---
title: "Adjustments to boat loader."
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2005-06-14
Hi all,

I recently installed Ubuntu 5.04 with the goal of learning Linux. It was great to see a distro that supported my wireless card and widescreen display (Fedora Core 1/2 and SuSE already wasted 10 gigs of my bandwith in the past).

Too bad, I have one annoying problem. My laptop is configured in such a way when you click the play-button (a multimedia key) when it's off, it starts PowerCinema Linux. After installing Ubuntu, the boot loader showed up instead. As I use that PCLin for fast access to media (it boots in two-three seconds) I don't want that behaviour, especially since the boot loader doesn't list PCLin. I want to keep the old behaviour, no boot loader, no nothing, just PCLin.

I also would like to make Windows boot automatically after 5 seconds or so when I haven't picked anything. So basically, I want to mess with GRUB.

Is there any way of accomplishing this? I would greatly appreciate your help. :)

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=Nanaki]Hi all,

I recently installed Ubuntu 5.04 with the goal of learning Linux. It was great to see a distro that supported my wireless card and widescreen display (Fedora Core 1/2 and SuSE already wasted 10 gigs of my bandwith in the past).

Too bad, I have one annoying problem. My laptop is configured in such a way when you click the play-button (a multimedia key) when it's off, it starts PowerCinema Linux. After installing Ubuntu, the boot loader showed up instead. As I use that PCLin for fast access to media (it boots in two-three seconds) I don't want that behaviour, especially since the boot loader doesn't list PCLin. I want to keep the old behaviour, no boot loader, no nothing, just PCLin.

I also would like to make Windows boot automatically after 5 seconds or so when I haven't picked anything. So basically, I want to mess with GRUB.

Is there any way of accomplishing this? I would greatly appreciate your help. :)[/QUOTE]
 Having Windows load automatically in 5 seconds is easy: you edit file
/boot/grub/menu.lst
(do not forget to make a backup first!) and after that, run 
sudo update-grub
Syntax of this file is mostly clear, but here is the manual if you need it: 
[http://www.gnu.org/software/grub/manual/html_node/Configuration.html](http://www.gnu.org/software/grub/manual/html_node/Configuration.html)
However, I do not know of a way to load something bypassing grub at the press of a button. How did you configure this button to start PCLin before installing Ubuntu?

---

### Post by bored2k on 2005-06-14
```
wget [http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb) && sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb && grubconf
```
Grubconf is a graphical representation of this.

---

### Post by Nanaki on 2005-06-14
Nice, that solves one of my problems, thanks. :)

As for the other, how it works exactly, I'm not quite sure. This is my current hdd structure:

img removed

That last partition is the Linux-one. And when I hit my play-key when my laptop is off, it launches that partition. Maybe it refers to hdd(0),4 (or however you phrase that). It's weird, as the Ubuntu installer doesn't detect it as an operating system and won't use it in GRUB.

Just as information, Ubuntu comes between partition D: and E: (I'll make D: or E: smaller).

Any other suggestions?

Thanks,

edit= oh, and it's OEM software, so I never configured nor installed it. :/

---

### Post by Nanaki on 2005-06-15
What if I place a partition after the PClin partition, that might work. Then the problem is this; can I place GRUB at the same place where NTLDR is?

---

