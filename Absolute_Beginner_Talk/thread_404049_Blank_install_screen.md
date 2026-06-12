---
title: "Blank install screen"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by drbob07 on 2007-04-07
Alright, I boot up into the Live CD

it has a menu with all the choices. I have tried both Start or Install and the Safe-Graphics mode. I have also messed with the F4 (VGA Settings) Menu. Still nothing...


It comes up with the scrolling Ubuntu progress bar. Then blinks a white cursor for a while.

It mentions that PnPBios failed, I may need to update my BIOS for safe operation, or boot with pnpbios=off for stability.

Then it continues for a little while longer. Then it goes to a blank screen. The harddrive / CD Drive do spin for a while, but eventually both go silent.

I tried booting with the pnpbios=off flag. The pnpbios error disappeared, but its still a blank screen.


=Specs=
HP Pavillion 8756c
Phoenix BIOS 4.0 (no updates avail.)
384mb RAM
Pentium3 (Coppermine) @ 866mhz
Nvidia GeForce FX 5200 PCI
On-board grahpics -- (the ones that come with Intel 810i Motherboard)


I have checked hardware compat / incompat lists. My hardware doesn't seem to have any problems with Ubuntu.

My BIOS has no option to disable the Onboard graphics.
I plugged a monitor into the onboard graphics. There are multi-colored lines along the entire screen.  You can kind of see a cursor moving, but there is no possible way I can install.


I guess theres always the alternative CD, but I'd really like to get the Live CD working if at all possible. (Don't want to spend any more time downloading CD's :-\)


(Since the installer appears to be booting to my ONBOARD graphics. Is there a way to tell the installer which graphics card it should be using in the advanced boot options?)

---

### Post by mac.ryan on 2007-04-07
Bob, there is a knows issue in Edgy, that prevent "safe mode" to be safe for real: have a look [here]("https://wiki.ubuntu.com/EdgyKnownIssues/59618").

You might wish to try to boot that way, and see if this get you past your problem... (no guarantee it will work, though!).

---

### Post by peteskeeterman on 2007-04-07
> Alright, I boot up into the Live CD

it has a menu with all the choices. I have tried both Start or Install and the Safe-Graphics mode. I have also messed with the F4 (VGA Settings) Menu. Still nothing...

It comes up with the scrolling Ubuntu progress bar. Then blinks a white cursor for a while.

You did better than I did drbob. The blinking cursor took me straight to a  blank screen :confused: 

It's a shame something so promising is like a rubics cube to install, makes me wonder if every step will be as long :(

---

