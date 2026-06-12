---
title: "Hello"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by rob7391 on 2007-07-21
I'm sort of not the most skillful person around on the computer but I did know enough to dump the windows os and install Ubuntu.
For all I know this might be obvious to everyone but I get this message when I am logging on now and then something like "dev/hda1 has been mounted 30 times without being checked check forced" then off it goes and runs a check. Now I have found the dev?hda1 which I figure is my hard drive in the system monitor but where do I go to check it?
Also occasionally I get a screen freeze and have to restart to clear it. I know there is a better way to fix this but what is it?
:)

---

### Post by Atomic Dog on 2007-07-21
The disc check runs at startup.  If you want to ever check it manually you need to open up a terminal window and type:  shutdown -F now  This will restart your system and run the disc ckeck.

The screen freeze:  Try pressing <ctrl>+<alt>+<backspace> this will restart X.

---

### Post by lisati on 2007-07-21
Don't sweat it - the message you got is normal for Linux, and has to do with the OS making sure that your computer is in a healthy condition.

---

### Post by bigfox on 2007-07-21
Basically, it is telling you that the drive has been mounted 30 times without being scanned for errors and that the scan is forced to happen.  

Linux knows that it should check the disk for errors every so often (after every 30 reboots)

---

### Post by rob7391 on 2007-07-21
Many thans guys
:)

---

