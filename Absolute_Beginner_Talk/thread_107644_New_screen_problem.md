---
title: "New screen problem"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by xkiddiegrinders on 2005-12-23
Everytime I start linux it tries to set the screen at 1280x1024 @ 75hz and this screen doesnt support that mode, is there I way I can change that without logging into the main GUI?

---

### Post by bscbrit on 2005-12-23
Yes.  In /etc/X11/xorg.conf you will see that each mode and depth is illustrated by a series of settings e.g.

"1280x1024" "1024x768" "800x.....  etc

The first one on each line is the one that the monitor will try to initialise to.  Just remove the settings that it cannot achieve.

You will have to edit this using sudo.

---

### Post by bscbrit on 2005-12-23
I'm not quite sure what you mean about entering the main GUI, I assume you mean that you are working from a command prompt (because X cannot start with the wrong values ..... etc).  Use vim, emacs or whatever other non-graphical editor you usually use.

---

### Post by xkiddiegrinders on 2005-12-23
Well, heres the issue, I cant even get into the login screen so I cant get to the terminal because my monitor gives me a "out of range" error :(  . So I need like a "safe mode" to start up in or some way to change it before the system loads

---

### Post by bscbrit on 2005-12-24
Its called 'recovery mode'.  When you boot the computer you will either see the Grub menu, which will give you the option of booting to your kernel, or booting to your kernel in recovery mode, or you will see a countdown which says something along the lines of 'press Esc to enter menu' - in which case press Escape and then select boot in recovery mode.  In recovery mode you are automatically given root powers so you can edit /etc/X11/xorg.conf using vim, emacs or whatever.  If you don't know either of these editors then there are 2 things to do.  The first is write a reminder to learn one of them - they exist on almost every linux computer and therefore can be relied upon - and secondly you can use nano as your editor.  Nano is preferred by some, particularly ex-Windows users.

NOTE There is NO gui in recovery mode - its all command line.

---

