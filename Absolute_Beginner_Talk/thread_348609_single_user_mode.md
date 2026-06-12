---
title: "single user mode"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by goucho29 on 2007-01-29
trying to find how to enter single user mode on my new Edgy install... for some reason the usual technique (type e at grub menu, add s to kernal line, then type b) doesnt work. What gives ? Tried searching this forum to no avail, tried searching built in help to no avail. TIA

---

### Post by yabbadabbadont on 2007-01-29
You might try typing out the entire word, "single", and see if it makes any difference.  You might also try adding the digit '1'.  I've seen both work with various kernels in the past.  You might even try adding "initrc=/bin/bash" so that you just drop into a shell on startup.

---

### Post by dad311 on 2007-01-29
I believe the command "sudo init 1"  will take you to single user mode.

---

### Post by goucho29 on 2007-01-29
thanks for the ideas. Tried single and 1 (separately of course) - neither worked.
As for the third idea- which file does that get edited into ? Thanks again for your assistance !

---

### Post by goucho29 on 2007-01-29
> **dad311 said:**
> I believe the command "sudo init 1"  will take you to single user mode.

cool - blacks out the whole screen... like Nina Meyers got to it :)  Seriously, thanks for the sugg - no harm done - just rebooted and all is fine. Prolly a line in my windowing conf file needs a tweak.

---

### Post by goucho29 on 2007-01-29
> **yabbadabbadont said:**
> You might try typing out the entire word, "single", and see if it makes any difference.  You might also try adding the digit '1'.  I've seen both work with various kernels in the past.  You might even try adding "initrc=/bin/bash" so that you just drop into a shell on startup.


Im guessing you mean add another line to my GRUB menu ?

---

### Post by yabbadabbadont on 2007-01-29
> **goucho29 said:**
> Im guessing you mean add another line to my GRUB menu ?

No, you just append "initrc=/bin/bash" to the end of your kernel line in grub when you hit the 'e' key to edit that entry.  Using, "single", *should* work though...  hmmm.
```
/home/bubba $ grep single /boot/grub/menu.lst
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single
kernel          /vmlinuz-2.6.15-27-k7 root=/dev/hda7 ro single

```

---

### Post by goucho29 on 2007-01-29
that didnt seem to change aything - my box just boots right into Kubuntu (where I can then choose to boot up GNOME or do some other things) no matter what. At least its reliable. 
Unfortunately, my other computers do single user mode reliably and their help systems even document how this is done. With Ubuntu - there is no mention of this in its built in help system...

---

### Post by frisket on 2007-10-07
Ubuntu is seriously broken in this regard.

Adding 'single' or single 1' to the kernel line in grub will enter recovery mode where it will prompt for the root password. 

Note to developers: this is NOT single-user mode. Single-user mode does not ask for the root password, which is probably why you've either disabled it or hidden it in some undocumented corner. Very laudable, but A Bad Idea. 

There appears to be no way that you can boot an Ubuntu Edgy system into single-user mode unless you know the root password -- which is not useful if the reason you want single-user mode is that you've forgotten the root password.

---

