---
title: "Powerbook G4/500 Low Sound and no battery meter"
date: 2010-06-06
forum: Apple Hardware Users
---

### Post by Semperfive on 2010-06-06
I just updated to Ubuntu 10.04 on my [Powerbook G4]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_500.html").

I have fixed the wifi issue that some people have been having but now I have some other things I need help with.

When playing videos I have very low volume when turned up all the way.

There is no battery meter?

Any help would be greatly appreciated, I'm still new to this.

---

### Post by sha.goyjo on 2010-06-06
> **Semperfive said:**
> I just updated to Ubuntu 10.04 on my [Powerbook G4]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_500.html").

I have fixed the wifi issue that some people have been having but now I have some other things I need help with.

When playing videos I have very low volume when turned up all the way.

There is no battery meter?

Any help would be greatly appreciated, I'm still new to this.

For a battery meter an easy fix is gpmudmon. It's a gnome panel applet that provides excellent battery support for the earlier pmu models.

As for the sound, do a search for snd-hda-intel on the forums and you should find what you need. It's likely a problem which can be solved by editing alsa-base.conf

---

### Post by Semperfive on 2010-06-07
I tried gpmudmon, it looked like it was installing.  There was a key symbol in the upper right and then it went away.  I tried restarting, but no luck.  Any ideas?

---

### Post by linuxopjemac on 2010-06-07
If you are in Gnome, it should work out of the box. The only thing you are missing is the pmu_battery module.
```

sudo modprobe pmu_battery
```

I would add it to the modules at startup, so you have the battery status all the time.

---

### Post by sha.goyjo on 2010-06-07
what linuxopjemac says is correct. To add the module just add the name to the bottom of the /etc/modules file, the name being pmu_battery.

---

### Post by Semperfive on 2010-06-07
Thanks you guys!  That worked :)

Still trying to figure out the sound thing.

Also, my CD drive is present, but I can't access it.  If I boot up with a CD in the drive it shows up on the desk top and I can access it.  It's a weird issue isn't it?

---

### Post by Semperfive on 2010-06-08
I tried alsamixer, the pc speaker was turned all the way down.  Easy fix!

---

