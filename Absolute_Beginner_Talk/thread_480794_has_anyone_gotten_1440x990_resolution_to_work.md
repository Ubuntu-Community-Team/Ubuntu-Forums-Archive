---
title: "has anyone gotten 1440x990 resolution to work"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-06-21
as stated above has anyone gotten that resolution to work with intel integrated graphics onboard

if so please post im about to give up ive tried everything i dont want to go back to windows

---

### Post by Mostlyharmless42 on 2007-06-21
i have the same problem w/ an NVIDIA graphics card.

---

### Post by mikewhatever on 2007-06-21
Try 1440x900 instead of 1440x990.

---

### Post by Clay_Banger on 2007-06-21
try this:
open the terminal and type this in:
```
sudo apt-get install xserver-xorg-video-intel
```
restart you computer.

Then go to System>Preferences>Screen Resolution and it should be there.

---

### Post by k0001 on 2007-06-21
first install intel drivers, as Clay_Banger stated (i guess, i'm not an intel vga user), then edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```

and under **Section "Screen"** look for **Subsection "Display"** and were it says **Depth 24** add as the very first option to **Modes** ... "1440x900"


you  should have something like this:

```

Section "Screen"

        # ....
        # ....

	SubSection "Display"
		Depth	24
		Modes   "1440x900"
	EndSubSection
EndSection

```

then you should be able to change resolution to 1440x900 in System_>Preferences_>Screen Resolution

---

### Post by p_quarles on 2007-06-21
Try the synaptic package called "915resolution". That will make most widescreens work with Intel drivers. It did for my widescreen laptop, at least.

---

