---
title: "Install/Boot Lockup - Keyboard leds flashing"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ExOniTe on 2007-08-07
Ok, I've been eager for trying Ubuntu for about a year now.
About a year ago I attempted to install Ubuntu 6.06(LTS), on the following specs:

MSI-K8N Neo2 Mainboard
AMD Athlon64 3200+
ATI Radeon X800 Pro 256 MB(AGP)
2 Maxtor 120 GB HD's
1 External Western Digital Mybook(Essential) 250GB
C-Media USB Soundcard

With Windows XP Professional SP2 already installed.

The problem then was a lockup at the brown/reddish screen, first the X appeared, then the loading circle and then the cursor, after about 20 sec(nothing displays, no menus, nothing) I was unable to move the cursor, and so I got a lock-up

The same thing happened when trying the 64-bit version of Ubuntu.
(I also tried Safe Graphics mode)
But that was a year ago...

Since 7.04 came out, I was interested in giving it a shot again, with ofcourse no succes(why make a topic about it then huh ;))

The problem I have now differs slightly from what I had first.

When trying to install the 6.06 version(either 32 or 64-bit) I get the same error.
Now, with the 7.04 version, I get the same lockup as in 6.06, with a minor difference, my keyboard leds start flashing and my monitor goes standby..

So this time, it starts to load again, followed by the cursor(although no colored screen for me this time, just black). And then the screen locks up, goes to standby, and the keyboard leds start flashing.

The same thing occurs when using the Alternate CD(although here I can fully install the system, but I get the same lockup when trying to boot into the actual system).

I saw someone recently posting a thread about this(he had the same videocard as me so I guess it's Graphics related), but since I had problems with this before I thought making a new topic was the best idea.

I hope there is a solution for this since I'm very eager in actually trying Ubuntu after a year .. :(

EDIT: I just noticed I forgot to put that I also tried installing Linux Mint 3.0 (Full), with the same error as with the regular Ubuntu versions.

---

### Post by ddrichardson on 2007-08-24
When you boot, press F6 at the menu and add ```
noapic
``` to the line and press enter.

---

