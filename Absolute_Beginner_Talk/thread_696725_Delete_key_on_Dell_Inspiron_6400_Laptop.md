---
title: "Delete key on Dell Inspiron 6400 Laptop"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by OobleCaboodle on 2008-02-14
Hi all.
I've recently installed Gutsy x86 on my slightly modified Dell Inspiron 6400;
160Gb SATA hD
plextor px608AL dvd-writer
ATi mobility x1400 GPU
core2 duo 1.6GHz
2Gig RAM.

Now apart from the known issues, (suspend, java, etc) I* think* I'm having a problem with my keyboard, but, being new to GNOME, it may well be the way it works?

If I select a file in nautilus, and hit Delete, nothing happens.
If I hit delete whilst typing (in any app or terminal window), it does nothing, where I would expect it to delete any following characters.

Is this behaviour normal in GNOME, or have I got something set up wrong?
Thanks for any help.

Erm, also, I suppose they're related in some ways, so I may as well put it here...

How do i remove individual keyboard shortcut mappings from the System->preferences->Keyboard shortcuts app?

---

### Post by OobleCaboodle on 2008-02-14
an update...
xev returns the following when I press the delete key.

```
FocusOut event, serial 28, synthetic NO, window 0x3000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

How do I go about fixing this?
Thanks for any forthcoming help

---

### Post by OobleCaboodle on 2008-02-14
erm, ok, this is weird. Curiously enough, without any intervention, it is now behaving like it should do.:confused:

---

