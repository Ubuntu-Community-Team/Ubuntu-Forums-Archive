---
title: "Monitor in wrong mode at boot, will not work!"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by johncontrane on 2008-05-14
Hi,
Just installed 7.2 on an old Powermac. My monitor is a 
SGI 1600SW and will only work in 60 HRZ mode, no other
mode works.

When I boot ubuntu I initially get a black screen with white
letters, then a white screen with black letters. Then it
wants to change again and that's where I get an error on
the monitor which requests input mode needs to be changed.

Terrific, how does one do that without a monitor.

I had read you can try pressing alt, control and tab - and
Tab + during boot up but it did not seem to have any effect.
System stops, or at least I can't tell what the system does since
the monitor is frozen

Any suggestions?

Thanks

---

### Post by nicedude on 2008-05-14
You said 7.2 but I assume you meant 7.10 Gutsy is what you were trying? While it may not be what you want to hear you might try downloading the current Ubuntu Hardy 8.04 live install and see if it will boot up your system  with monitor support or not. At least if you use the live disk you should be able to see if it will work before you install it.

Hope you find a resolution.

---

### Post by FredSambo on 2008-05-14
Try this:

Do: ctrl-option-F1

Then Do: sudo nano /etc/X11/xorg.conf

In the Monitor section, change "HorizSync" to 58-62 and "VertRefresh" to 75-117. (These are the settings for a typical G3 (bombshell) monitor, so yours may be different, you may have to google to find the proper settings for your monitor.)

Disable DRI. In the Module section. If there is no Module section, make one:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

Save the file, go back to the command line and do:

sudo /etc/init.d/gdm restart

Good luck!

---

### Post by FredSambo on 2008-05-14
It may take a couple trys to get ctrl-option-F1 to work, but it WILL work!  ;)

---

### Post by FredSambo on 2008-05-14
Here you go:

```
Section "Monitor"
    Identifier  "SGI MultiLink"
    Option      "DPMS"
    HorizSync   28-64
    VertRefresh 43-60
    UseModes    "SGI Multilink Modes"
EndSection
```

---

### Post by johncontrane on 2008-05-14
Fred,
Thanks for all the suggestions. Unfortunately, they won't work.
I get pause the boot up, but when I try bring up the file
at the command line I get the message:
"No such file or director". Additonally, the first left
hand character of the text is missing which makes me suspect
a driver problem.

I'm using a Multilink with this monitor, so as long as you feed
it 60hrz refresh, it does not mattter much what it is attached to. 

Starting to think either I find another monitor to try and find
something I can load of the cd and go find that find and manually
change it

---

### Post by johncontrane on 2008-05-14
Well, I solved part of my problem. I borrowed a CRT. But
there are more problems. System hangs. I then hit alt + F1.
I get message" system loading"
Then the following:

Check root = bootag cat /proc/cmdline
or missing modules, devies,: cat /proc/modules 1s /dev
Altert! /dev/mapper/host-root does not exist. Dropping to shell!

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter help

(initramfs)

Makes Windows looks like child's play!

Any further suggestions much appreciated. I hate loosing to
machines.

---

### Post by avtolle on 2008-05-14
If you are using 7.10, at the intrafms prompt, type ```
modprobe ide-core
``` then when the intrafms prompt reappears, type ```
exit
``` and see if the boot process continues. If it does, then this may be made permanent (I'll need to look this up, as I'm not where my notes are right now).

EDIT: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) will help you, if the above works, to make the change permanent.

---

### Post by johncontrane on 2008-05-14
Avotolle,

Thanks for help. Tried what you suggested. Most commands
including modeprobe get the same response "not found".

For some reason I don't think the system is seeing the
hard drive.

---

