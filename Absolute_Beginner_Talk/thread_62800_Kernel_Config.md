---
title: "Kernel Config"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by mog27 on 2005-09-05
I am brand new to Ubuntu.  I come from other Distros like Fedora Core.  I have been following the guide on here on how to compile your own vanilla kernel (the one from kernel.org). I have been following it, but when I boot into the new kernel, it boots ok, but I get some errors and my wireless card isn't detected.  Here is what I do:

For the latest 2.6.13 kernel:
In /usr/src/linux I:
make oldconfig
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image modules_images
dpkg -i kernel_whatever.deb

What I want is to use the same configuration (the .config) of the kernel I installed when installing Ubuntu because that works perfectly.  I just want to update it to the 2.6.13.  And that is what the make oldconfig is supposed to do, right?  I basically want to use the .config of the kernel image I installed and configured Ubuntu with and that isn't working.  In fedora core that works great.  Suggestions?

---

### Post by odin on 2005-09-06
Well I thought the make oldconfig should do that but if you say that it doesnt work try another thing.

Type make menuconfig instead.When the menu comes out then till the end an there is an option saying "Load an Alternate Configuration FIle".Select it and then just type where the old kernel's config file is located (it should be something like /boot/config-2.6.8-2-386 or something it depends on the kernel you had) and load it.

Then review that everything is fine and select any of the new features if you wish.But review it because sometimes there might be differences.I dont know if there are big ones between this two but...

hope that helped a bit.

---

### Post by mog27 on 2005-09-06
This simply does not work.  I tried what you said and loaded the config-2.6.10-5-386  from /boot.  menuconfig still showed NOTHING selected, so it is like it is starting over with no .config file.  And once again, make oldconfig does the same thing.  I cannot use the config from my current kernel in menuconfig.  This is weird.  I never had this problem with other distros. :( And I have followed both kernel guides on this site.  Any other thoughts as to why I am having this issue?

---

### Post by heimo on 2005-09-06
Before running make oldconfig, copy earlier /boot/config* file to /usr/src/linux/.config - now, when you run oldconfig, does it ask some y/n/m questions?

---

### Post by mog27 on 2005-09-06
[QUOTE=heimo]Before running make oldconfig, copy earlier /boot/config* file to /usr/src/linux/.config - now, when you run oldconfig, does it ask some y/n/m questions?[/QUOTE]


Yep I have done that and it *does* ask some Yes/No questions. However, in menuconfig, hardly anything is choosen (not even ext3 or cpu type), so it is like menuconfig is working with a blank or .config file with nothing chosen.  Why is this?

---

### Post by mog27 on 2005-09-07
Noone has any ideas?  I am loving Ubuntu besides this darn kernel compile issue.  It is weird.

---

### Post by tseliot on 2005-09-09
If you use a vanilla kernel you have to recompile ndiswrapper (don't ask me how, I'm still learning). 

My advice is to add Breezy repositories to your /etc/apt/sources.list and download kernel tree in Synaptic (2.6.12-8 ) and to use those sources (the patches will be used automatically when you compile the kernel) to compile your kernel. In this way ndiswrapper will work.

If you want to use 2.6.13 you have to wait for Breezy developers to release it (as they did with 2.6.11 in Hoary).

OR

If you desperately need 2.6.13 I hope someone who's more expert than me can help you with ndiswrapper.

---

### Post by mog27 on 2005-09-09
[QUOTE=tseliot]If you use a vanilla kernel you have to recompile ndiswrapper (don't ask me how, I'm still learning). 

My advice is to add Breezy repositories to your /etc/apt/sources.list and download kernel tree in Synaptic (2.6.12-8 ) and to use those sources (the patches will be used automatically when you compile the kernel) to compile your kernel. In this way ndiswrapper will work.

If you want to use 2.6.13 you have to wait for Breezy developers to release it (as they did with 2.6.11 in Hoary).

OR

If you desperately need 2.6.13 I hope someone who's more expert than me can help you with ndiswrapper.[/QUOTE]

Why does menuconfig show a nearly blank config after make oldconfig and after moving my config from /boot to .config in /usr/src/linux?

---

### Post by tseliot on 2005-09-09
[QUOTE=mog27]Why does menuconfig show a nearly blank config after make oldconfig and after moving my config from /boot to .config in /usr/src/linux?[/QUOTE]
Follow my HOWTO please. You don't have to move any ".config". Make oldconfig copies the config of your current kernel to the new one.

---

### Post by mog27 on 2005-09-09
[QUOTE=tseliot]Follow my HOWTO please. You don't have to move any ".config". Make oldconfig copies the config of your current kernel to the new one.[/QUOTE]

Yes it is supposed to, but it does not for me.  After doing make oldconfig, I go into menuconfig and just about every option is blank.  Even stuff like ext3 and CPU type are completely blank.  I don't get that.

---

### Post by tseliot on 2005-09-09
[QUOTE=mog27]Yes it is supposed to, but it does not for me.  After doing make oldconfig, I go into menuconfig and just about every option is blank.  Even stuff like ext3 and CPU type are completely blank.  I don't get that.[/QUOTE]
filesystem is not specified in Ubuntu kernel (it has to be done for vanilla kernels). Its weird no CPU is set. Are you sure it's really blank? This is not the way Ubuntu Hoary works (you have Hoary, do you?)

---

### Post by mog27 on 2005-09-09
[QUOTE=tseliot]filesystem is not specified in Ubuntu kernel (it has to be done for vanilla kernels). Its weird no CPU is set. Are you sure it's really blank? This is not the way Ubuntu Hoary works (you have Hoary, do you?)[/QUOTE]

I am 99% sure I saw no CPU type picked.  I will check again later.  And ya I am running Hoary.   I even tried compiling using the ubuntu 2.6.10 kernel and again it showed nothing picked.  I may just have to wind up copying and pasting everything I am doing including some kernel configs; maybe I am doing something wrong, but I followed the guide step by step.

---

### Post by tseliot on 2005-09-09
Weird, I had never seen a problem like yours. It is likely to go beyond my knowledge. Try asking here:

[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

---

### Post by mog27 on 2005-09-10
Well, I just switched to Ubuntu from Fedora.  I got to say the one thing I dislike about Ubuntu and like about Fedora (and probably other distros), is the kernel compiling.  It just seems easier and works better when you make oldconfig.  Everything just works (or it did for me) when you use a vanilla (kernel.org) kernel.  Everything else though I like better on Ubuntu (when it comes to desktop distros).

---

