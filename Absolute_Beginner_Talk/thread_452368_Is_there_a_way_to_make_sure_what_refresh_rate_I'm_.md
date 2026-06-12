---
title: "Is there a way to make sure what refresh rate I'm currently using?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by tanelt on 2007-05-23
I have a reason to believe that my monitor's on-screen menu is reporting the currently used refresh rate incorrectly. Well, it works just fine in WinXP, but when I hooked it up to an old Win98SE machine, it reportred to be using 60Hz, but I could tell it was it was actually using a whole lot more, just by looking at it. Well, anyone tell the difference between 60Hz and 100Hz. However telling the difference between 120Hz and 150Hz only with a naked eye is not always that simple.


So, is there perhaps some sort of a terminal command to output the refresh rate that's currently been used?
Some sort of a program that runs on Ubuntu?
Or maybe some other way to make sure what refresh rate the monitor is currently using?

---

### Post by LaRoza on 2007-05-23
Under "System -> Preferences" Look at screen resolution.

---

### Post by tanelt on 2007-05-23
Yeah, that's the method I've always used (I even have the "Screen Resolution" shortcut icon on my desktop), but
I have a feeling it displays the refresh rate incorrectly, i.e. the monitor is _actually_ using a different refresh rate.


Is there some other way?

---

### Post by LaRoza on 2007-05-23
```
gksudo gedit /etc/X11/xorg.conf
```

Don't change anything, unless you back up first.

Screen resolutions and refresh rates are listed under the "screen" subsection.

I'm going to do a search for a command line method, hang on...

```
sudo dpkg-reconfigure xserver-xorg 
```

Found it.

---

### Post by tanelt on 2007-05-23
Heh, as a matter of fact, these 2 commands are the most frequently used commands in my
entire Linux usage history. I think I've probably used them for hundreds of times by now. :D
Thanks for trying to help, though. I appreciate it.


But I'm looking for something that can accurately **detect **and **output **the currently used refresh rate.

Because when I select between like 70Hz and 150Hz from the "Screen Resolution" selection box,
it makes no difference. It's still using 70Hz, because it's fairly easy to tell that with a naked eye.

---

### Post by mtb-cliff on 2007-05-24
try xvidtune.

---

### Post by WiFi Ed on 2007-05-24
Does your monitor have an "Information" button? For example, my ViewSonic LCD has a button that shows actual refresh rate (which is different than that shown by System/Preferences/Screen Resolution). There is a bug somewhere, related to NVIDIA video cards I think, that causes Ubuntu to show incorrect refresh rates.

Ubuntu shows 50Hz, the ViewSonic LCD reports 75Hz.

xvidtune shows 75Hz.

---

### Post by Wim Sturkenboom on 2007-05-24
The only way is through the monitor or using measurement equipment (oscilloscope); the latter is the most reliable way (if calibrated). Graphics cards don't measure their output signal for that purpose; they might however for intenal use to keep it stable.

---

### Post by tanelt on 2007-05-24
[QUOTE=mtb-cliff]try xvidtune.[/QUOTE]
Thanks for the suggestion! I'll be sure to give it a try as soon as I have the chance.

[QUOTE=WiFi Ed]Does your monitor have an "Information" button? For example, my ViewSonic LCD has a button that shows actual refresh rate (which is different than that shown by System/Preferences/Screen Resolution). There is a bug somewhere, related to NVIDIA video cards I think, that causes Ubuntu to show incorrect refresh rates.

Ubuntu shows 50Hz, the ViewSonic LCD reports 75Hz.

xvidtune shows 75Hz.[/QUOTE]
Yeah, my monitor has that button which opens up an on-screen menu that shows the resolution and
refresh rate that it's currently using. However sometimes it reports things incorrectly, so I can't rely on it. :(

[QUOTE=Wim Sturkenboom]The only way is through the monitor or using measurement equipment (oscilloscope); the latter is the most reliable way (if calibrated). Graphics cards don't measure their output signal for that purpose; they might however for intenal use to keep it stable.[/QUOTE]
Heh, yep. Something like that would be great to have. =)

---

