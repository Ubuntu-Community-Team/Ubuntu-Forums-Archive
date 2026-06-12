---
title: "Touch up a Ubuntu installation on a MacBook."
date: 2007-08-20
forum: Apple Intel Users
---

### Post by Alex&amp;Linux on 2007-08-20
Hello all!

I've just purchased a new macbook, and being a Feisty user since around Christmas, I wanted to share my book with it, however, I find myself continuously booting into OSX (which I enjoy) even when I dont want to use mac specific software.

Ive broken it down to the fact that I really like to be able to close the lid and have it sleep, and conserve energy for long periods of time, and resume instantly.

This is something that doesnt want to work with Ubuntu, as the only item that will is "darken screen" which still causes the unit to drain its battery.

Also, I cant find any way to darken the screen, or cap the processors (as OSX does automatically to help conserve energy)

These are all things that cause me to boot into OSX and leave Ubuntu nearly untouched.

If anyone can offer suggestions regarding how to "touch" up my Ubuntu installation, it would be appreciated!
**Also, though I am a big fan of AWN, Mac's dock is a lot more interesting to me!
I remember something like "kool-dock" being pretty fluid in KDE, but it was spotty in Gnome, and it wasnt "drag 'n drop" like OSX or AWN, any suggestions there?

Oh, also, I really enjoy the way OSX displays options for each app (you know, at the top title bar, depending upon which window is currently selected) as it reduces the volume of space each window needs, and makes navigation more enjoyable and predictable.
I have seen themes that can use this approach, and I want to try it!

---

### Post by kidders on 2007-08-21
Hi there,

OSX really is nice. :-) Although I use Macs quite a bit, I almost never put Linux anywhere near them, for the same kinds of reasons you mention ... stuff often just doesn't quite work as cleanly as it does in MacOS.

> **Alex&Linux said:**
> I really like to be able to close the lid and have it sleep, and conserve energy for long periods of time, and resume instantly.Sleeping & hibernating is a bit of a quagmire, because there is a huge degree of variation in how laptops handle power management, making it tricky for the open source world to keep up. Thankfully, the hardware in Macbooks is pretty standardised, so good solutions are undoubtedly out there somewhere.

> **Alex&Linux said:**
> Also, I cant find any way to darken the screen, or cap the processors (as OSX does automatically to help conserve energy)Again, solutions to these issues should also be readily available. CPU frequency scaling, for instance, is usually trivial ... all you normally need to do is identify the correct /sys file to modify. On my AMD for instance, **echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor** caps my CPU frequency at 1GHz. I presume the approach is somewhat similar on a Macbook.

There is a variety of little daemons around that can handle things like LCD backlight dimming for you. I used to use pbbuttonsd on G4s, every now and then. I wonder if it runs on Intels.

> **Alex&Linux said:**
> I remember something like "kool-dock" being pretty fluid in KDE, but it was spotty in GnomeI've never seen anything that even comes *close* to the OSX dock, in terms of stability & intuitive behaviour. I managed to put up with the Avant window navigator for a while (I threw in the towel eventually), but perhaps you might like to give it a go.

> **Alex&Linux said:**
> Oh, also, I really enjoy the way OSX displays options for each appKDE can do this.

---

### Post by E Gardner on 2007-08-21
Hi-

I can only comment on the sleep mode issue. I am a very new Ubuntu user on an older version of the MacBook Pro (first generation). I set up Ubuntu Studio with the set of macbook installer scripts posted by another user on this forum (Rapido) that installed XGL, Compiz, etc. and found that my machine would go into sleep but would not wake up.

I re-installed Ubuntu (standard version this time, still 7.04) from the alternate install cd and did no special tinkering except for installing the fglrx driver (without which I cannot enter graphical mode), and out of the box I have support for the brightness/volume buttons, bluetooth, wireless, and suspend. It "just works." It seems that support for a lot of mac hardware is included in the 7.04 version of Ubuntu by default.

It seems like not that much could have changed between my hardware and yours (perhaps that is a naive assumption). Perhaps the list of possible problems can be narrowed down this way?

Good luck-

---

### Post by Alex&amp;Linux on 2007-08-21
Thanks to the both of you for your time and suggestions!
I am a firm believer in the availability of a solution for any problem, and your advises are useful.
Thanks again!

(I'll post any useful ideas I encounter in this thread if I can uncover them in the short term)

---

