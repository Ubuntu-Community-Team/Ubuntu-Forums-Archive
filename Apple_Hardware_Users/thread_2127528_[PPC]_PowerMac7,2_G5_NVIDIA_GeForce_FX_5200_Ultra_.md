---
title: "[PPC] PowerMac7,2 G5 NVIDIA GeForce FX 5200 Ultra framebuffer working Ubuntu 12.04"
date: 2013-03-20
forum: Apple Hardware Users
---

### Post by chatuser on 2013-03-20
I had working Ubuntu 10.0http://mintppc.org/forums/viewtopic.php?f=15&t=810&sid=31612fe8c1f3406afaadd758cabdab29&start=204 on my PowerMac G5 dual 1.8 GHz and I did a clean installation of Ubuntu 12.04, but the video card doesn't work.

My former solution [http://ubuntuforums.org/showthread.php?t=1769801]("http://ubuntuforums.org/showthread.php?t=1769801") doesn't yet work because the nVidia propietary driver xserver-xorg-video-nv is no longer included in Ubuntu 12.04.

There are lots of documentation about the free driver xserver-xorg-video-nouveau but nothing works with my video card.

After reading some references I have found a way to make work my graphic card in framebuffer mode:

1. install Ubuntu using the alternate CD and the option install_powerpc64 at "boot:" prompt

2. at the next boot, a blank screen appears

3. reboot (you must force switch off with the power button) and at the "boot:" prompt type Linux nomodeset

4. your computer will boot showing a screen with corrupted colors, like "psychodelic" colors

5. press ctrl+alt+F1 and log in

6. update the entire system using these commands (please be patient):
sudo aptitude update
sudo aptitude safe-upgrade

7. edit yaboot.conf using this command: sudo nano /etc/yaboot.conf

8. add a new line in the header section or in your specific boot image section, in my case it looks like this:

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        #append "quiet splash"
        append="nouveau.modeset=1 video=nvidiafb:1280x1024-24@85 video=DVI-I-1:d video=TV-1:d"

Notes:
- try using different frequencies, try @60, @75, @85 and choose the frequency that displays better quality.
- if your monitor doesn't support 1280x1024, try 1024x768
- you can use these options at the "boot:" prompt without editting yaboot.conf, for example write this text at the "boot:" prompt:
Linux nouveau.modeset=1 video=nvidiafb:1280x1024-24@85 video=DVI-I-1:d video=TV-1:d
- the reason to edit yaboot.conf is to make these changes permanent and my keyboard has spanish characters, so it's difficult for me to find some symbols
- these video outputs are disabled: DVI-I-1, TV-1. If you video card has different outputs find their names by this command: ls -l /sys/class/drm

9. run sudo ybin -v, reboot (sudo reboot) and the graphic session will now work !

10. I recommend to use Ubuntu 2D or any other session without 3D effects to avoid image corruption. In my case I installed Gnome Shell:
sudo aptitude install gnome-shell gnome-tweak-tool

I log in using "Gnome Classic(No effects)" and I used gnome-tweak-tool to properly customize Gnome Shell

Pros: it's the only way I have found to make Ubuntu 12.04 work in graphical mode
Cons: no graphic acceleration and some bugs like not refreshing lower screen areas randomly
Advice: if you need a more reliable system, use Ubuntu 10.04 or Debian 6.0.7 that include the nVidia propietary driver xserver-xorg-video-nv

References:
[https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics]("https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics")
[http://mintppc.org/forums/viewtopic.php?f=15&t=810&sid=31612fe8c1f3406afaadd758cabdab29&start=20]("http://mintppc.org/forums/viewtopic.php?f=15&t=810&sid=31612fe8c1f3406afaadd758cabdab29&start=20")

The key is to make work the new free driver xserver-xorg-video-nouveau, if you achieve it please tell how to do it

Comments are welcome.

---

### Post by mörgæs on 2013-03-20
Thanks for posting your advice. 

I have an FX 5200 and I would not recommend running Ubuntu on it, not even after modifications. Lubuntu (and on a good day Xubuntu) are better choices.

---

