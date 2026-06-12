---
title: "[SOLVED] Emergency-WSOD"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-11-18
I'll try to keep this as simple as possible.

Two days ago I fired up Fiesty and was greeted with my desktop for about 3 seconds. Then the screen went solid white. I re-booted several times with the same results. I tried a couple Fkeys on reboot and got a screen with a blinking cursor and had absolutely no idea of what to enter.

Next I tried to boot with the disc in, to reinstall, and it was ignored. My PC Bios are set to boot from CD first and HD second. All I got was grub starting up to the WSOD again.

This is a stand-alone installation on an old Compaq.

Well guys and Dolls, can this be fixed or do I have another paperweight?

Much appreciation,

Jon

---

### Post by oilchangeguy on 2007-11-18
ok, what did you do to it 3 days ago?

---

### Post by Romin-1 on 2007-11-18
In preferences I clicked on a prog that had the Footprint as a logo, can't remember the name now, and it asked me if I wanted to use the effects I had and I clicked yes. Nothing happened then. Two days later I shut down the PC and it sat idle for a few days until I finished learning/customizing Vista on another machine. Then it booted to the white screen.

What gets me is the fact that I cannot boot the machine using the Fiesty CD to make a clean install.

I'll try anything short of re-cycling the box.

Jon

---

### Post by oilchangeguy on 2007-11-18
confirm the cd drive is first in the boot order.

---

### Post by Romin-1 on 2007-11-18
Yessiree. I triple checked that. On Compaq that's F 10 on boot.

Jon

---

### Post by daengbo on 2007-11-19
Boot, hit CTRL-ALT-F1. That should bring you to a login prompt login. Log in and type
 gconftool -s /desktop/gnome/applications/window_manager/current /usr/bin/metacity --type string
all on one line.
That will set your effects to off.
Then type CTRL-ALT-F7 to get back to your WSOD. Hit CTRL-ALT-Backspace to reset the session.
Your login should come back up. If it doesn't, please report back.

---

### Post by Romin-1 on 2007-11-19
I did as you suggested, daengbo, several times as a matter of fact, with no joy.

I did, however, manage to get into bios and force it to boot from disc and thusly, have just now, re-installed the Feisty little Ungulate...

Many thanks,

Jon

---

