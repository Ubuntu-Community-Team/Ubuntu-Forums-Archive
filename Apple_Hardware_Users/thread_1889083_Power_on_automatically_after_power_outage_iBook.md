---
title: "Power on automatically after power outage iBook"
date: 2011-11-30
forum: Apple Hardware Users
---

### Post by cep3431 on 2011-11-30
I have ubuntu installed on my ibook 3g. Is set up as a server. When the power goes out the ibook runs on battery for a few hours, then it shuts off. Is there a way for it to start up again after the power comes back on. Im not always where my ibok is and I want to be able to access my server when the power returns without pushing the power button. Thanks!

---

### Post by jjex22 on 2011-12-01
The original osx had a power failure feature where it would basically hibernate until power was restored if I remeber, but this isn't ideal....

For you're instance, I'm thinking a hardware mod - using a relay switch powered by a mains adapter - such that when the power comes on, a capacitor delays the relay for a second so that your laptop is ready, then the relay connects the power button circuit to start the laptop.

You'd have to use a non-latching relay, and either one that only acts once or configure the circuit such that triggering the pc breaks it's own circuit - you don't want it hammering on and off like car indicators!

I know this is very easy to do - I remember doing it at school... just can't remember how - hopefully someone else will help convert my ramblings into a circuit diagram!

Edit: you'd also want a push button switch along the pc loop so you can still turn it on and off!

---

### Post by rsavage on 2011-12-02
> **cep3431 said:**
> I have ubuntu installed on my ibook 3g. Is set up as a server. When the power goes out the ibook runs on battery for a few hours, then it shuts off. Is there a way for it to start up again after the power comes back on. Im not always where my ibok is and I want to be able to access my server when the power returns without pushing the power button. Thanks!
 
Yeah, maybe possible. The gentoo documentation mentions something about this [http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml#wakeon](http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml#wakeon) :
 
> 
The Power Management Unit (PMU) in most Macs has the ability to turn the Mac on again after a power loss. This feature is controlled by the PMU options found in /proc. To enable this feature, set server_mode to 1, to disable it, set server_mode to 0.
 
# echo "server_mode=1" > /proc/pmu/options
 
Unfortunately, this setting is turned off again after the machine restarts. To ensure that your system always starts with power on after power failure enabled, add the line above to /etc/conf.d/local.start.

 
 
Whether it applies to the ibook g3 with a battery I have no idea.
 
EDIT: a bit more research on this.... there should be a command "autoboot" in the package powerpc-utils that does this. It's amazing what features you can do when you look!!!

---

### Post by curly_nostrill on 2012-04-08
I was just looking to solve this issue for a server I have running Debian Squeeze on a G4 tower (AGP, sawtooth or something).

As rsavage said, it was as simple as ```
(sudo)autoboot -v on
```.
> powerpc-utils - Various utilities for Linux/PowerPC

Utilities for Linux on PowerPC hardware. 

mousemode - tell an ADB mouse to use a given device handler ID.
nvsetenv - change/view Open Firmware environment variables.
nvsetvol - set Open Firmware stored volume setting.
clock - Hardware clock program for Power Macs.
trackpad - modify PowerBook trackpad behavior (tap/drag mode).
fblevel - control LCD/TFT display backlight brightness.
fnset - set PowerBook keyboard function keys mode.
lsprop - list OF device tree in human readable format
autoboot - set autoboot (server mode) flag on CUDA PowerMacs
bootsched - set automatic power up time on CUDA PowerMacs

---

