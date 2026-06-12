---
title: "Fans"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by kob0724 on 2006-08-31
When I got my mobo it came with this cool software I would use to controll my fans. It would automatically dial-up or dial-down the speed of my fans based on the CPU temp (I think thats what it was based on). Is there anything like that for linux out there?

---

### Post by kidders on 2006-09-02
Loads of it! Which ones are best, depends on your specific architecture.

Basic support for Intel/AMD/etc. power management stuff is part of the kernel, so to get started, you'll need to figure out which modules should be loading, and whether you need to load them manually.

Additionally, you need things called "userspace" utilities to issue instructions to the kernel about what you want to have happen. Again, which ones you want depends on exactly what hardware you've got.

One of the more useful tools is "lm_sensors". It doesn't really let you *change* anything per se (like most other utilities do), but it can show you information about CPU temp, fan speed, chassis intrusion, etc. KDE, Gnome and lots of other things can talk to lm_sensors, and have pretty-looking apps and widgets that can show you the current state of your machine.

Other stuff that's commonly available includes the ability to scale your CPU speed (take a look at "cpufreq") up and down on demand, and tinker with your fans. The real beauty of these tools is that they rely on the contents of /sys and /proc to work, which means *you* can play around in there too. With a little research, there's no reason why you couldn't make your computer automatically hibernate when you walk away from it, or wake you up in the morning by turning up all the fans (silly, I know), with tiny little custom-written scripts.

Any help?

---

### Post by kob0724 on 2006-10-31
I have lm_sensors fully working right now. What I was looking for was some kind of program (preferably with a gui) that would slow and speed up my fans as nessecary. I don't need all 4 of them running full throttle when i'm typing up my homework ya know?

---

### Post by gn2 on 2006-10-31
[www.silentpcreview.com](www.silentpcreview.com)

My personal preference is to set things up to run quietly in the first place.

Thermally controlled fans are another option and aren't software dependent

---

