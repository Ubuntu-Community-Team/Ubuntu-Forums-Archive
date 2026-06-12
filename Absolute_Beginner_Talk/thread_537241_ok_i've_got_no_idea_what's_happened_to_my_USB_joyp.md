---
title: "ok i've got no idea what's happened to my USB joypad"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-08-28
ok, i'll try and give you as much info as possible because it's just bizarre ..

up until probably yesterday my generic USB joypad worked fine when I ran Project 64 under Wine.

it recognised it as a "DragonRise Generic USB Joystick" and worked fine.

While I was working in Konsole yesterday, i thought i'd do a "apt-get update" to get the latest lot of updates, as I knew there was a new version of Wine available.

Since then, it seems as if someone has battered my Joypad around the head with a large stick because it just doesn't want to work.

If i ran Project 64 with the usual Joypad plugin I was using, it loaded up the ROM I had and died completely.  I tried installing 1964, again under Wine, and i selected the "N-Rage's Direct-Input8 V2 1.83" input plugin - which I had been using on Project 64 and clicked "input" to try and configure it, and it didn't work.  I clicked it again and it did - and confirmed my original set up profile from when the Joypad worked.

I doubled clicked on a Rom to start the emulation and 1964 crashed with "A4000060: Exception in emulation thread" error.

Ok, so I installed the joystick calibration tool and ran it, and it recognised my joypad correctly as a DragonRise Generic, and when I clicked "calibrate", all the buttons were correctly recognised.

Apart from the D-Pad which had the up and down controls reversed for some bizarre reason.

And also the left analog stick - left and right are fine, but up and down are reversed.

The only logical conclusion I can think of is that it is the Joypad itself, but with what i've given you here, does anyone have any ideas ??

should i "apt-get autoremove" ?

or do a bit of a cleanup just in case there's any conflicts anywhere ?

the only think i've done different is the "apt-get update", which updated Wine.

Oh, and i've run "winecfg" and added both emulators as applications in "windows XP" mode as well, but that makes no difference.

i'm really stumped here !!

oh, and i've also tried creating the symbolic link for the input device as well, as suggested in another thread, but to no avail ..

---

### Post by jasonwatkins on 2007-08-28
and i should point out as well that I installed mupen64 and tried running a rom, only to be told I had no controller inserted.

ALL the emulators work fine if I select keyboard input.

---

### Post by jasonwatkins on 2007-08-28
just out of interest, i downloaded and installed a sega genesis emulator.

i ran "Gens32Surreal" under Wine and installed "dgen" from synaptic.

On Gens32, I got a "IDirectInput:Create device FAILED" error when I selected the "joypad" option, and on dgen, when I ran it from the command line with the flag "-j" for use joystick if detected, it returned a "bad patch" error.

but then the joypad is still detected in the calibration program ...

---

