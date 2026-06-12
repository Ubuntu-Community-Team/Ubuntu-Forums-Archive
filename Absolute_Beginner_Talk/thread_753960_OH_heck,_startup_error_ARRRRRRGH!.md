---
title: "OH heck, startup error ARRRRRRGH!"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-04-13
hi all,

i have been trying to fix a problem with my slow grub load up in the following thread;
[http://ubuntuforums.org/showthread.php?p=4707973#post4707973](http://ubuntuforums.org/showthread.php?p=4707973#post4707973)

as you see, i was directed to this page;
[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

and was instructed in the fifth post to do the following

[B]"1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k <insert results from uname -r here>

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum. This only works if Usplash is what was broken, which sounds right for all of you. Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.
"[/B]



well, i did this and restarted. Just before the splash came up, i got an error:
**[162.451157] Kernel panic - not syncing: no init found. Try passing init = opt to kernel**

it just stays at that message and won't load
i seriously did not (and don't) have a clue what to do, so please help if you can

---

### Post by SnakeHips on 2008-04-13
Boot the machine ,hold down the "esc" key when the grub menu pops up , try "recovery mode" or selecting an earlier kernel version to get you going...

---

### Post by Nick8692 on 2008-04-13
no, recovery mode just brings up exactly the same menu :(

---

### Post by SnakeHips on 2008-04-13
If you cant get past GRUB me thinks that it cannot find the kernel.......unless anyone can offer a better solution I think it's re-install time from the liveCD.

---

### Post by Nick8692 on 2008-04-13
yeah, thats what i feared...
i have everything backed up on my second hard drive, so i guess i will wait for the new release, download and install it.

unless anyone knows a way of reinstalling GRUB?

---

### Post by FrozenFox on 2008-04-13
You can reinstall grub by booting to the livecd, and following these directions.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

