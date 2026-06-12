---
title: "How can I kill my screensaver?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-27
I play my old Playstation games on a pSX emulator on Kubuntu Gutsy.  For some reason, my screensaver takes over after ten minutes, and I have to move the mouse or press some keys (I use a USB controller) to get rid of it.  It's just a blank, black screensaver, and it's **not** powersave mode (it's a brighter black).

In my System Settings, both my screensaver and my Powersaving options are disabled, so I don't know quite why it's doing this.  :/  Any help would be appreciated.

---

### Post by dips_xe on 2007-11-27
does this happen if you're not using the ps emulator?

---

### Post by sailor2001 on 2007-11-27
in terminal:  pkill <your program>

---

### Post by Sarteck on 2007-11-28
dips_xe: Yeah, it happens even when I'm not running the emulator.  It even happens when I'm watching stuff in Kaffeine.

sailor2001: pkill which program, though?  I'm not (as far as I know, anyway) running any kind of screensaver program.



Some more news, half the time when I'm trying to adjust options in the "System Settings" for Kubuntu, if I try to adjust anything in the "Monitor" section, when I close the System Settings, it restarts my X server, and I have to log back in.  >.<

At first I thought it was Compiz-Fusion, so I uninstalled that.  (That did, actually, solve some of my problems that I think was unrelated, but not the screensaver issue.)

---

### Post by Sarteck on 2007-12-05
Well, my problem went away, but I only have a clue as to -why- it did, so I'm not sure if I should mark this as solved.

I had **xserver-xgl** installed, and when I go rid of it, a lot of my problems went away, including this one.

---

