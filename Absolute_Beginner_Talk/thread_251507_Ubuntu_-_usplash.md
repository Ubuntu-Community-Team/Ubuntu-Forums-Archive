---
title: "Ubuntu - usplash"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by oVIXx on 2006-09-05
Got a simple question. Where is the control for changing the usplash images? 

From Synaptic I browsed around and noticed some splash screens from Kubuntu and Edubuntu, decided to try them out, went ahead and installed them. I liked them but since they are not specific to the o/s I decided to remove them, using synaptic again. So the gdm login and start up are back to ubuntu, however when I shutdown the grub image is from kubuntu and the grub boot image is from edubuntu. I searched the 'control panel' and I can't seem to find a setting to change the images and/or frame buffer resolution. Anyone have any clues? :???:  Thanks in advance!

---

### Post by coffeecat on 2006-09-05
Hopefully, [this page]("http://doc.gwos.org/index.php/Different_usplash") should help you change the usplash.

---

### Post by oVIXx on 2006-09-05
Perfect that did it. Got the splashes, both start and shutdown, back to displaying 'Ubuntu'. Thx alot for that post! 

Any suggestions on increasing resolution of the framebuffer? The font and Ubuntu graphic are all choppy and square, so I'm assuming its at 640x480 or 800x600. I'd like to boost it up to 1280x1024 if possible. 

What about adding custome graphics? Is there any kind of control module for changing the boot splashes and login screens?

---

### Post by coffeecat on 2006-09-05
Can't help you with the framebuffer resolution. You can control this in other distros with the vga=whatever in the kernel line of menu.lst, but I see that Ubuntu doesn't have this value.

As far as grub splash images is concerned there are two ways. The easier way is by the use of a splash.xpm.gz image in the /boot directory and a 'splashimage=(hd0,0)/boot/splash.xpm.gz' line near the beginning of menu.lst. (Change hd0,0 as appropriate.) There are limitations to the size and number of colours for the xpm.gz image. Suggest you search the forum for 'grub splash' or similar. I think there have been several threads.

The second way is a bit more complicated and involves using a modified grub as used by SuSE. You can find howtos [here]("http://doc.gwos.org/index.php/GfxBoot") and [here]("http://www.ubuntuforums.org/showthread.php?t=208855"). Happy tweaking. :)

---

### Post by oVIXx on 2006-09-05
Cool, thanks for the links. I'm gonna read them both, see how it turns out. I didn't have any specifics in mind as far as the graphics are concerned. I'll probably have to surf a bit to find some cool ones, and tweak them a little. I'll post back let you know how it turned out.:)

---

