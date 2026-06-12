---
title: "No keyboard/trackpad/external USB input devices on a Macbook Pro 5,1"
date: 2012-07-28
forum: Apple Hardware Users
---

### Post by Niarbeht on 2012-07-28
So, I'm attempting to install 12.04 on a Macbook Pro 5,1.  Just getting to the install screen is a mild hassle, as I have to add nomodeset and noapic to get the install CD to boot.  After X starts and I get to the install environment, however, the keyboard and trackpad (and external keyboard and mouse, if I have them attached) will stop responding.  Yeah, stop responding.  As in they work for a while, and then quit working.

It's quite annoying.  Even ctrl+alt+f1, or fn+ctrl+alt+f1 doesn't work, so I can't even escape to the console.

Anyone have any ideas or know what's messing up?  If not, I'll file a bug report.  I'll also try the server installer in a bit, and then try to transition that to a desktop environment (dirty, but if it works, it works).

Further information: Debian installed fine.

---

### Post by Niarbeht on 2012-07-28
Just found the text-based installer.  About to give that a shot.  I'm thinking that will at least work for getting through the install, though I'm not sure how things will play out after that O.o

---

### Post by Niarbeht on 2012-07-28
Well, the text-based installer has, at the very least, let me get through the install process.  I'm currently using a desktop with a wireless card and NAT (hooray networkmanager for making things easy) until I can install the broadcom wl drivers (or SOMETHING) installed.  I'll document as much of what I do to get things working here as possible.

As a sidenote, I've already noticed one of the problems I saw with the nouveau driver on my old Debian install.  I think the fix starts with adding some lines to the grub entry.

Also, I need to bathe this desktop's keyboard in rubbing alcohol.  The last guy who used it a lot was seriously gross.  O.o

---

### Post by Niarbeht on 2012-07-28
Well, it'll still lock out keyboard/mouse after a certain amount of time.  Booting with nomodeset seems to help, and disabling the nouveau driver seems to have bought me a nearly infinite amount of time.  Of course, I'm also on battery and using wired, rather than wireless.

Hmm.  I'm changing too many variables at once, but SOMETHING about a default 12.04 install _REALLY_ doesn't like this hardware.

Also, it's hard to type on this keyboard.  It requires vengeful viking force.

EDIT:
Aaaaand, there it goes.  It lasted for noticeably longer this time.  I'm going to try upgrading all the packages (but it'll take several passes to get everything to download.  Network seems to cut out at the same time as everything else.).  If that doesn't do it, I'll try the kernel PPAs.  If that doesn't do it, well, back to Debian.

---

### Post by Niarbeht on 2012-07-28
Fixed it.

noapic wasn't necessary after some updates.  Leaving noapic in place causes the symptoms, but by default on an unpatched system I can't seem to boot with it enabled.

Maybe it's just me.

---

