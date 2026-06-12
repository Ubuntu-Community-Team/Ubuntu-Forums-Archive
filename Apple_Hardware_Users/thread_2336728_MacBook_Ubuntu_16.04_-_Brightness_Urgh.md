---
title: "MacBook Ubuntu 16.04 - Brightness Urgh"
date: 2016-09-10
forum: Apple Hardware Users
---

### Post by karnival8 on 2016-09-10
I've been working this issue for days. I've installed 16.04 (Gnome) on a 11.5 MacBook Pro. It's almost perfect except for one thing; the screen brightness. 

I installed the Nvidia drivers which, for the first time, gave me a brightness slider and made it so the hotkeys (F1, F2) respond. When adjusting the brightness in any way, the acutal brightness doesn't change. It's always at 100%, even if the brightness slider is moved to 5%. 

I've been reading a lot of posts and trying different things but nothing is working. 

Here is some general information about what I've done. 

Edited xorg.conf, added:
Option "RegistryDwords" "EnableBrightnessControl=1"

Edited GRUB, tried many variations of:
acpi_osi=, acpi_osi=Linux, acpi_backlight=vendor

Tried to install nvidiabl, but I can't get it to work nor do I know how it should operate. 

/sys/class/backlight contains only one folder - gmux_backlight
echoing brightness levels to /brightness results in permission denied, even as sudo

I'm out of options and hoping for some help. :confused:

---

### Post by deadflowr on 2016-09-10
*Thread moved to **Apple Hardware Users**.*

---

### Post by karnival8 on 2016-09-11
Solved

After days of working on this I found a suggestion to add setpci -v -H1 -s 00:01.00 BRIDGE_CONTROL=0 to /etc/rc.local

I did that, chmod +r +w to be safe, rebooted, and bam! It works perfect. 

I have no idea what this alteration does. If anyone would care to enlighten me I'd appreciate it.

---

### Post by ian.canino on 2016-09-11
[FONT=courier new]setpci[/FONT] is a program that allow you to configure PCI devices where automatic detection may fail (for Apple computers this is often the result of a nonstandard EFI implementation).
[FONT=courier new]-v[/FONT] parameter tells [FONT=&amp]setpci[/FONT] to be verbose as to what happens after execution of [FONT=&quot]setpci[/FONT]
[FONT=courier new]-H1 [/FONT]parameter tells [FONT=&amp]setpci[/FONT]to use a particular method of access to PCI hardware
[FONT=courier new]00.01:00[/FONT] is the full address of the particular hardware function (in this case: bridge control). It is in the form of [FONT=courier new][[[[<domain>]:]<bus>]:][<slot>][.[<func>]][/FONT]

Use [FONT=courier new]man setpci[/FONT] if you want to learn more.

---

### Post by synchronizer2 on 2016-09-17
> **karnival8 said:**
> Solved

After days of working on this I found a suggestion to add setpci -v -H1 -s 00:01.00 BRIDGE_CONTROL=0 to /etc/rc.local

I did that, chmod +r +w to be safe, rebooted, and bam! It works perfect. 

I have no idea what this alteration does. If anyone would care to enlighten me I'd appreciate it.

Hello. I have an old Macbook Pro i7 17" (6,1 I believe) and I am trying to set it to dual-boot Mac OS and Xubuntu 16.04. I am trying Xubuntu using a usb bootloader and unfortunately I am experiencing the same issue that you did, but your solution does not seem to work.

 setpci -v -H1 -s 00:01.00 BRIDGE_CONTROL=0 (as root)

The brightness keys still do nothing.

Then I tried:
 echo 200 > /sys/class/backlight/gmux_backlight/brightness

This adjusts the brightness, but it is not clear what the maximum really should be since the values aren't percents.

Also, for some reason the color calibration is awful--incredibly blue-tinted, and still not quite right even if I use an icc profile from Mac OSX.

Is it possible that Xfce4 is to blame? I read somewhere that it doesn't have much support for brightness, display, and color calibration.

On the other hand, I tried the bootloader on someone's newer 2013 retina macbook pro, and the screen coloration was perfect. Brightness controls worked with no problem whatsoever, and I am stunned. Shouldn't this work?

My GPU is the NVIDIA GeForce 330M (and there are built-in Intel graphics).

This is not very related, but there are also v-sync issues and tearing issues that I cannot seem to solve. I would try Lubuntu instead, but that may have the exact same problems.

Is my hardware just too old?

Do you or does anyone else have any suggestions?

Thank you.

EDIT:

I tried Lubuntu next, which had the same problems, but then I tried Ubuntu-Mate, and it worked without modification! The only issue is that the window-resizing is a bit sluggish/jerky. I will see whether I can replace the window manager.

---

