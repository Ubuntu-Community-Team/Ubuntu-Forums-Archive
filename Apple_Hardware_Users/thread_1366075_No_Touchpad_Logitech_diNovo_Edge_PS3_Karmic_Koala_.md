---
title: "No Touchpad Logitech diNovo Edge PS3 Karmic Koala 9.10"
date: 2009-12-28
forum: Apple Hardware Users
---

### Post by n3IVI0 on 2009-12-28
[Moved from Hardware and Laptops section]

[http://ubuntuforums.org/showthread.php?p=8517445#post8517445]("http://ubuntuforums.org/showthread.php?p=8517445#post8517445")

This question has already been asked, but so far, the solutions are either old or ineffective. Here's the deal. I'm running Xubuntu 9.10 on my PS3. So far, it's been great with only one caveat - my Logitech diNovo Edge keyboard/mouse doesn't work. Now, I have already figured out that getting this thing to work with the built in bluetooth is pointless. It won't work, and nothing anybody has tried is ever going to get it to work. So, plan B - the USB dongle. Now, this worked perfectly on 9.04 Jaunty, as others have noted - plug it in, sync it, instant keyboard/mouse function. In this latest iteration of xubuntu, it even syncs and maintains connectivity through reboots, only the touchpad does not work. It worked without a hitch on Jaunty, and now, this upgrade has broken it.

The closest thing to a solution I've been able to find is here. Sounds great. Modify xorg.conf, and your touchpad will magically work again. BUT WAIT! 9.10 has no xorg.conf. Brilliant. Break my touchpad, and then deny me the only method of fixing it. Alright. So I do Ctrl-Alt-F1 to get to the CLI, and stop gdm with the command sudo service gdm stop. So far so good. My searches indicate that you can either use the command Xorg -configure (doesn't work. You have to chmod /usr/bin/Xorg to 777, which makes the command work finally, but then it tells you there's nothing to configure) or create it manually. Alright. So let's create the xorg.conf file manually in /etc/X11 and add these lines to it:

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Device" "/dev/input/mice"
Option "Protocol" "Auto"
EndSection

Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Here's the catch. EVEN WHEN YOU ROLL YOUR OWN, if an xorg.conf file is present, xubuntu will NOT BOOT. X crashes to the command line every time. You can't start gdm, and if you reboot with the file present, it's the same deal.

I'm not some random noob asking a question that's already been answered because I couldn't be bothered to search. I've been to Google, this forum, the forum over at PSUbuntu.com, and Logitech's forum, and NOBODY has any idea how to fix this problem. I intend to keep using xubuntu 9.10 because it is blistering fast, even before you enable GPU vram swap. It runs every MAME game I throw at it fullscreen and full speed. Plus it looks cool. YellowDog 6.2 (where I could sync my keyboard/mouse and my Sixaxis controllers with the native bluetooth without a hitch) is kludgy, ugly, and slow, even running XFCE for the desktop. I REALLY don't want to have to go back to Yellowdog just to get my expensive wireless keyboard/mouse working properly. Isn't there anybody who knows how to solve this problem!? Thanks!

---

