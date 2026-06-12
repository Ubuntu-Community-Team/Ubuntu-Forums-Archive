---
title: "ubuntu and standby"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by jhamer9 on 2006-01-08
This is a multipart question in regards to ubuntu and standby on a Compaq M700 laptop (or any laptop for that matter).

When I closed the lid of my laptop it went into  standby mode, or something that resembled it anyway.  After I opened the laptop I only had a blinking cursor at the upper left hand side of my screen.

I couldn't get out of it, so I pressed the power button and ubuntu went into it's shutdown sequence.

Now, the laptop will startup and take me into a command line prompt instead of the GUI.  Now for the questions:

1. how do I get back into the GUI (both KDE, and startx would not work as a command)?

2.  how do I get ubuntu to boot into the GUI as the default?

3.  how do I get the laptop out of standby if this happens again?

4. how do I stop the laptop from going into standby when the lid closes on the laptop?

Thanks for listening.

---

### Post by d1337 on 2006-01-08
[http://ubuntuforums.org/showthread.php?t=113178](http://ubuntuforums.org/showthread.php?t=113178)
for starters.  Laptop mfgs seem to use many different standars for power management.  I am running Ubuntu on an E-Machines M6805 and installed it on a  Compaq laptop for a salesperson that works for me.  In both instances, however, I don't rely on just shutting the lid...I always Sys-->LogOut-->Hibernate.  Haven't even tried.  Sorry I couldn't be of more help, but the Hardware --> Laptop Support section is a great place to learn a bit about acpi and whatnot.

d1337

---

### Post by jhamer9 on 2006-01-09
Thanks for the pointer.  Although I'm still not able to startup the GUI after login. I only see:

kubuntu login:

then,

*username@machine:~$*

maybe i'm missing something obvious, but what is the command for launching into the initial startup screen of the GUI?

---

### Post by jhamer9 on 2006-01-09
forgot to mention, when i type ```
startx
``` i receive the following error:

```
/usr/bin/X11: error while loading shared libraries: 
libz.so.1: cannot open shared object file: Input/output error
xinit: Server error.
```

Thought that might be of some help. thanks.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=jhamer9]
maybe i'm missing something obvious, but what is the command for launching into the initial startup screen of the GUI?[/QUOTE]

You need this command:

```
startx
```

Learn it and love it.

---

### Post by d1337 on 2006-01-10
If startx is generating that error, it sounds to me as if you may have an xorg.conf error (or some nature of display issues).  But your issues could also lie within /etc/init.d in regards to GDM/KDM as default boot.  This is way over my head and I'm sorry I couldn't be of more help.

Regarding your laptop lid issue, the lid event is defined in /etc/acpi/lid.sh
The other files in this directory dictate resume, sleep, hibernate etc.  I would think that commenting out certain calls within lid.sh would disable the event, but I wouldn't delete the file as that may pose some other issues.

How did you install KDE?  There is a [thread]("http://www.ubuntuforums.org/showthread.php?t=96048&highlight=kubuntu-desktop") regarding how to uninstall ubuntu-desktop entirely, likewise kubuntu-desktop.  Aysiu has done a few tests and has posted his steps.  It is possible that you could uninstall your kubuntu-desktop and attempt a reinstall if things go downhill from here.  Your files (read /home) should not be affected with the possible exception of certain settings (theme, panels, desklets, browser extensions/bookmarks etc), but that scenario might beat the heck out of a clean install or the frustrations that could come about while trying to fix.  I would definately try the fix first, though.

d1337

---

### Post by jhamer9 on 2006-01-10
I think this is definetly something with X.  I don't know if it's corruption or a disk on the way out or those damn gremlins again, but I've been having some really strange problems lately.

If I don't get this to work I'll most likely try a new install on a new HDD, and do some searching on how to restore my currently saved data (i.e., configs and data).

Thanks for the link, I'll give it a shot and post the results.  It can't get much worse than it is... (famous last words...)

---

### Post by jhamer9 on 2006-01-12
Well, I uncovered more corruption/missing files and the HDD was starting to make clicking noises as well, so I copied the config files I needed, replaced the HDD, and installed ubuntu (I was previously running kubuntu, so I figured I'd give gnome a try).

Thanks for the help.

---

