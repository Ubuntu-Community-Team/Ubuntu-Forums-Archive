---
title: "splash screen disappear, unable to play full screen game"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-12-28
the splash screen disappear when during the booting and switching off process. when running full screen game it immediately switches to 640x480 screen and return to the desktop [the desktop becomes 640x480 and has very big icons and font.] the only way is to reboot the computer and it becomes normal again. moreover when i press ctrl+alt+f1 and switch to the terminal screen the font becomes very big and not the whole screen is visible [i think it is 640x480 again?] any idea? thanks

---

### Post by plucky on 2007-12-28
Hi afeasfaerw23231233

Not sure about the game problem,but this link fixed my splash screen problem.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

Hope this helps

Cheers

---

### Post by afeasfaerw23231233 on 2008-01-05
thanks but doesn't work! bump! it shows nothing but a black screen during boot-up and shutting down. bump

---

### Post by pieterjanvu on 2008-01-05
I think this should help
Had the same problem, no boot splash on shutdown and start up
I found this posting by shyron that helped me out setting the resolution of the console and it fixed the problem. [http://ubuntuforums.org/showthread.php?t=618523](http://ubuntuforums.org/showthread.php?t=618523)

Add vesafb and fbcon in /etc/initramfs-tools/modules
then in : /etc/modprobe.d/blacklist-framebuffer , comment vesafb. this means put "#" before vesafb
Finally in /etc/modules, add vesafb

Additionally I added vga=792 in the menu.lst after "kernel ...ro quiet splash"
gedit /boot/menu.lst

and
Changed usplash resolution to xres=1024 and yres=768
sudo gedit /etc/usplash.conf

Finall update usplash
sudo update-initramfs -u -k `uname -r`

---

### Post by afeasfaerw23231233 on 2008-03-21
i have followed the step in of your link but doesn't work [http://ubuntuforums.org/showthread.php?t=618523](http://ubuntuforums.org/showthread.php?t=618523)
> Finally I find the solution :

Add vesafb and fbcon in /etc/initramfs-tools/modules
then : update-initramfs -u
then in : /etc/modprobe.d/blacklist-framebuffer , comment vesafb
Finally in /etc/modules, add vesafb

so i follow your advice: > 
Add vesafb and fbcon in /etc/initramfs-tools/modules
then in : /etc/modprobe.d/blacklist-framebuffer , comment vesafb. this means put "#" before vesafb
Finally in /etc/modules, add vesafb

Additionally I added vga=792 in the menu.lst after "kernel ...ro quiet splash"
gedit /boot/menu.lst

and
Changed usplash resolution to xres=1024 and yres=768
sudo gedit /etc/usplash.conf

Finall update usplash
sudo update-initramfs -u -k `uname -r`
but still doesn't work. but an very annoying problem now appears: everytime it boots up a message appears after the grub screen disappear: the vera mode is unverified. press 'return to show to mode or space bar to skip.
i undo what i did and this annoying message still appear!! what to do? thanks for help!

EDIT: err... that annoying message disappeared after i just reboot it again. but i am still unable to get the splash screen..

EDIT: the problem is that there's nothing shown on the booting or shutting down process. no splash screen or white text on the screen so i don't know what it is doing. sometimes i don't know it is checking disk and thought that it hangs

---

