---
title: "Want to show all information during boot"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by taseedorf on 2008-01-14
Hey guys, don't know if this is the right forum, but here goes.

When I boot into Ubuntu, it takes forever.  I see some text, than the screen goes black for what seems like 5 minutes, and than flickers, than boots.  I want to see text the whole time it is booting so I know what's going on.  I have commented out the "quiet" string from menu.lst in grub, is there anything else I should do?


Also, I don't think my computer is shutting the kernel down correctly (is that the right term)?
I shut down, than quickly see some bloated text on the screen, than a black screen.  Doesn't seem right, what logs could I check for errors on shut down?
Thanks.

Tim

---

### Post by articpenguin on 2008-01-14
hey

try bootchart

[https://wiki.ubuntu.com/BootCharting]("https://wiki.ubuntu.com/BootCharting")

[http://www.bootchart.org/index.html]("http://www.bootchart.org/index.html")

---

### Post by JoshuaRL on 2008-01-14
As for the login problem, I think you have the usplash settings wrong.  I had that problem on my laptop.  Check your settings in /etc/usplash.conf and make sure that your supported resolution is in there correctly.  After that you'll have to update the theme:

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by dutchcow on 2008-01-14
If you want to see more output (verbose) during boot-up you can enable verbose mode, this can be done one time by booting up ubuntu, with the recovery option, this will give you very verbose output. If want to keep using the nice graphical bootup but still want to see whats going on (i use this myself) edit "/boot/grub/menu.lst" and find and edit "defoptions" so it looks like this:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash=verbose

```This will give you a nice view of whats loading, and what is failing. Also if the resolution seems to low edit /etc/usplash.conf and set a higher res. Run "sudo update-usplash-theme usplash-theme-ubuntu" after chaging the resolution. This will be permanent until you change the "defoptions" in "/boot/grub/menu.lst" back to its original state.
Good luck!

---

### Post by taseedorf on 2008-01-14
that boot chart is kind of cool, except I don't know which programs I could stop, and which I can't.

On the other hand, I added the verbose information to my grub, and it doesn't change much.  When I shut down now, though, I get a splash screen that scrolls what is being stopped which looks nice.  However, when I boot, it shows some scrolling information for about 5 seconds, than goes to the black screen...... I even changed the res in the usplash (it was a wrong res) to my supported res, which didn't work.  I than changed it to 800x600, and it didn't work.  What gives?  I'm wondering if it has anything to do with modprobe?   I noticed there was an error with something when I booted in recovery mode.........  Also, is there any way I can check ONLY errors in boot ?

---

