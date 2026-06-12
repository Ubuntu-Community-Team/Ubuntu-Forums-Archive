---
title: "PowerBook G3 Pismo [aka FireWire/2000] sleep problems"
date: 2010-01-17
forum: Apple Hardware Users
---

### Post by Firepowerforfreedom on 2010-01-17
I've been using Linux on and off on my laptop for over several months, and the main issue on my hardware is suspend-to-ram. It just doesn't work the way it's supposed to.
  First off, here's my hardware:
[B]—PowerBook G3 Pismo (PowerBook3, 1)
—500 MHz PowerPC 750 (G3)
   —L2 Cache: 1 MB
   —Bus Speed: 100 MHz
—512 MB 100MHz SO-DIMM RAM on two 256 MB cards
—ATI Rage Mobility M3 (part of the Rage 128 series)
   —8 MB VRAM
   —14.1" TFT flatscreen display
—The PRAM battery is dead and unplugged[/B]
  Secondly, here are the symptoms of my problem:
  [B]#1: Laptop does not suspend:
  [/B]Screen goes black, backlight does not turn off; system unresponsive and must be restarted
  **#2: Laptop attempts to suspend:**
  Screen goes black, backlight turns off, hard drive does not spin down; same outcome
  **#3: Laptop almost suspends:**
  Screen goes black, backlight turns off, hard drive spins down, faint squeal emanates from inside case somewhere; same outcome
  **Here's what it has done when suspend does work:**
  Screen goes black, backlight turns off, hard drive activity for a second, then spins down; sleep light glows momentarily, then oscillates (glows bright and dim—you should know).
  If it suspends, it usually doesn't have a problem resuming, so the key is to get it to suspend every time. 
  I've used Hardy, Jaunty, and Karmic for Kubuntu, Xubuntu, and Ubuntu (except for Karmic on this one). The only one that gave me consistent results was Kubuntu Jaunty, but it runs slowly and the panel colors were inverted (except for white—strange…). Additionally, I've never been able to suspend-to-disk, even though every power manager that I've used says it's technically possible. Either it doesn't suspend, or when resuming it kills the backlight and seems to become unresponsive (Xubuntu gave me the best hopes with this one; it would tell me that it was resuming from disk when the splash screen showed up).
  
  I'm to my wit's end! I want a Karmic install (I can't wait for Lucid), but I just can't get it to suspend. Has anyone else with a PowerPC had these problems? If so, please tell me how you fixed it!

---

### Post by linuxopjemac on 2010-01-17
Maybe it's not what you want to hear but I have a Pismo too, with Debian Lenny. It suspends fine due to pbbuttonsd.

---

### Post by Firepowerforfreedom on 2010-01-17
Thanks. I used Debian at one point, but it seemed to have the same problems.
I have to manually set up my xorg.conf file, so I wonder if the issue is in there.
By the way, I just tried Xubuntu Jaunty, and it suspended fine several times in a row. I then proceeded to upgrade to Karmic, and the problems returned.

What are your Pismo's specs? I have pbbuttonsd already, so I don't think that is it (unless the version was upgraded during my upgrade to Karmic). Another thing: does Debian kill your volume in ALSA when you boot up/resume?

I really need to find a pattern here.

---

### Post by linuxopjemac on 2010-01-18
I have a Pismo 400 MHz (there was a 400 and a 500 MHz version I think). For me, everything except wireless internet works after suspend. I have to manually remove and modprobe the wireless module. I think that pbbuttonsd does not work well with gnome-powermanager, which is used standard in Ubuntu Intel, so also in ppc. Maybe if you remove that daemon, it'll work better. But don't expect it to work in Lucid, as they will deprecate Hal completely then. Hal is needed for pbbuttonsd if I'm correct.

If you install Debian Lenny, you can have my Xorg.conf file. It will give you all the working functions. Pismo's are all the same. [Here ]("http://mac.linux.be/content/g3-powerbook-pismo-modelines")you go.

---

