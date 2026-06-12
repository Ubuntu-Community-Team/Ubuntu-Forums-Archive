---
title: "Second HD not mounting"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by AutumnPhoenix on 2008-03-02
I receieve an error message when I plugged in my hard disk.  It was set up in windows.

It reads  Cannot Mount Volume:

Choice 1 windows...
Choice 2:
if you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on command line:

mount -t ntfs-3g /dev/sdb1 /media/FlyMouse - o force

or add the option to the relevent row in the /etc/fstab file:
/dev/sdb1 /media/Flymouse ntfs-3g defaults,force 0 0


when I try the first it does nothing.  When I try the second it says permission denied even though I "su"

---

### Post by glennric on 2008-03-02
This is occurring because at some point windows was not shutdown properly.  What it is telling you to do is to boot to windows and shutdown the computer properly, or if you can't do that try the second option at your own risk.  I recommend booting to windows if you can.  You can't select these options at this point.  It is not a menu, but a list of things to do.

---

### Post by AutumnPhoenix on 2008-03-02
I can't boot in windows, my computer is entirely xubuntu

---

### Post by glennric on 2008-03-02
Then you will have to try the second option.  Open a terminal and type
```
sudo mount -t ntfs-3g /dev/sdb1 /media/FlyMouse - o force
```

---

### Post by AutumnPhoenix on 2008-03-02
I did type that before, it just gives me a bunch of mount commands

---

### Post by glennric on 2008-03-02
Did you put "sudo" in front when you tried it before and have to input your password for the command to execute?

---

