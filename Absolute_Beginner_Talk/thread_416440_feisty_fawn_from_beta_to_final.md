---
title: "feisty fawn from beta to final"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by stijngysemans on 2007-04-21
One week ago, my computer refused to boot:
/dev/hda2 contains a file system with error, check forced it said on boot.
/dev/hda2 failed, unexpected inconsistency, try to run.... to fix the problem. (i don't remember the name exactly).
It then asked to fix file inodes. I said "y" a couple of times and my computer just booted fine.

But (and maybe this is another problem, i don't know it's related in any kind!) one week after the beta release or so, my update manager said that there was a broken package. I didn't mind it so much but since then, a lot of programs refuse to work.
ie: I can't run update-manager, only sudo apt-get upgrade/update command via the console.
look
```

stijn@stijn-desktop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
ImportError: No module named gobject


```

Other problems
-the applet enable desktop effects just crashes after enabling the effects (I need to force a logout with ctrl+alt+backspace)
-send crash report application crashes :lolflag: 

thanks for the help!

---

### Post by gilgongo on 2007-04-21
I doubt the two issues are connected, but even if they are, you should a) back up all your data NOW and b) check your hard disk to see if it's producing any more low-level errors. 

Check the disk by booting from a rescue CD and copying the affected partition(s) to /dev/null. This won't do anythig to the drive, but will force every sector to be read - so if there there are any errors they will come up in the copying process. in your case it will be:

dd if=/dev/hda2 of=/dev/null

If it is producing errors, I would highly reccomend buying a new disk. 

PS: You can use fdisk to check for errors but this is simpler and quicker in my experience.

---

### Post by stijngysemans on 2007-04-21
And why are non of my python (i think maybe this is the source of the second problem) programs working

for instance Nicotine
```

stijn@stijn-desktop:~$ nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at http://sourceforge.net/projects/psyco/
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 151, in <module>
    result = checkenv()
  File "/usr/bin/nicotine", line 73, in checkenv
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
ImportError: No module named gobject


```

---

