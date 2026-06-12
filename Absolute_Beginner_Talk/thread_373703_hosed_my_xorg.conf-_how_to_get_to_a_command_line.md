---
title: "hosed my xorg.conf- how to get to a command line"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by lowracer on 2007-03-01
I was following the Twinview How-To, made extensive mods to my xorg.conf file, and after restarting X my system says there's something wrong with my xorg.conf.  It says this in a very strange looking dialog box that is black letters on grey textual and large font and surrounded by what looks like international characters nYE with accents on them, obviously some attempt at rendering text-graphics that didn't work.  Background of screen is blue.

OK so before botching up my xorg.conf, I was smart and backed it up.  Problem is I can't seem to get to a command line to switch back to the backed-up xorg.conf.  How do I get from a fresh boot to a command line?  It keeps wanting to load up that botched xorg.conf file, and giving me that error dialog box.  But when I try to get out of it, I get to a black screen with a cursor, but no matter what I type at that cursor, nothing happens except it shows me what I typed, I figure that no 'command interpreter' is running.

Help!

Thanks in advance...
-mark

---

### Post by Steel Bovine on 2007-03-01
Have you tried trying to boot from the live CD?

---

### Post by invalid on 2007-03-01
Boot into recovery mode from your grub menu. This will skip all X directives and load you into a terminal.

---

### Post by bodhi.zazen on 2007-03-01
Ctrl-Alt-F1 (Ctrl-Alt-F2 ....) will bring you to the command line without rebooting.

Ctrl-Alt-F7 brings you back to the gui.

---

### Post by lowracer on 2007-03-01
Thanks, I got to the command line.  Appreciate the help.

---

