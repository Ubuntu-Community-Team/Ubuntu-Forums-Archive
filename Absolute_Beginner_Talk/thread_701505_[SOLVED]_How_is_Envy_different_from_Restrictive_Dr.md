---
title: "[SOLVED] How is Envy different from Restrictive Drivers?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-19
How is [Envy]("http://albertomilone.com/nvidia_scripts1.html") different from the Restrictive Drivers (see picture below)?

[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_restrictivedrivers.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/restrictivedrivers.jpg)
[size=1]*(Click to see larger)*[/size]

---

### Post by PeterJS on 2008-02-19
The restricted drivers manager pulls the latest *tested* driver from the manufacturer, and includes package management metadata, and then configures it. Envy pulls the latest driver from the manufacturer and then configures it.

You'll get new drivers with Envy, but that's at the cost of testing and proper package management.

---

### Post by BassKozz on 2008-02-19
Thanks PeterJS,

One more quick question for ya...
After I installed Envy, I noticed that I had a new application (NVidia X Server Settings) under:
Applications->System Tools->Nvidia Settings
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_nvidiaxserversettings-1.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/nvidiaxserversettings-1.jpg)
[size=1]*(Click to see larger)*[/size]

Is this a part of Envy's doing, or do I get this with the "*Restrictive Drivers Manager*" also?

---

### Post by Hobo Joe on 2008-02-19
Yes, that's part of the drivers, you will get that with Envy and the restricted driver mananger.

One note on the control panel, the settings WILL NOT get saved unless you open it with this command:
```

gksudo nvidia-settings

```
Make sure to press 'save configuration to X server' before you close.

---

### Post by BassKozz on 2008-02-19
Thanks guys :)

---

