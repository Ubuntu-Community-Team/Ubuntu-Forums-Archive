---
title: "As a desktop user, do I need CPU frequency scaling?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by bharathan100 on 2007-08-05
I use an Intel core2 Duo @ 1.86 Ghz .. I saw Ubuntu say CPU frequency scaling not supported when it booted up. I thought frequency scaling is a power saving tool for laptops. Is this a cause for concern?

---

### Post by splintercellguy on 2007-08-05
No, it's just saying your desktop computer doesn't have a feature that's found in laptops :).

---

### Post by syadnom on 2008-02-14
That is actually untrue, the desktop model core2 processors fully support frequency scaling.  I am having trouble getting frequency scaling to work on my e8400 on MSI NEO2-FR.  I know the hardware supports it, it just wont work.

---

### Post by khensucat on 2008-02-14
Frequency scaling (Speedstep) is a feature of *all* Core2 chips.

However, some BIOS's disable this feature automatically, and may (or may not, in my case) let you turn it on or off in BIOS.

---

### Post by stevejesus on 2008-02-14
Well, if you can get it working on a desktop, I say DO IT!  Anyway that you can save power in ANYTHING that you do, you should take full advantage of it.

---

### Post by rasty on 2008-02-14
You do need it and you can do it using the cpufrequtils a package to do do stuff like setting your scaling scheme or inform you of your settings . Two commands cpufreq-info(displays info) cpufreq-set (sets scheme) You have to install it cause I don't think it's preinstalled! And of course you must activate scaling through your BIOS. Try it it's easy and if you google it you'll find more information over the subject. There is even a configuration file for these things(as with everything else) but I don't remeber the name. search for it!

---

### Post by dcstar on 2008-02-14
> **bharathan100 said:**
> I use an Intel core2 Duo @ 1.86 Ghz .. I saw Ubuntu say CPU frequency scaling not supported when it booted up. I thought frequency scaling is a power saving tool for laptops. Is this a cause for concern?

It is a concern not having it working - it will reduce the power your PC consumes and also allow it to run cooler (therefore extending the life of the hardware).

When you have is set up correctly your Ubuntu system can automatically switch between power saving and faster clock speeds as required - so you don't experience any loss in performance but your system runs as efficiently as possible.

---

