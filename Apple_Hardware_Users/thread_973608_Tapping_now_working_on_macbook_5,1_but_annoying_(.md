---
title: "Tapping now working on macbook 5,1 but annoying :("
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by m.musashi on 2008-11-06
After all the trouble getting tapping working (thanks to the mactel folks for that), I'm finding it rather annoying while typing. The cursor wanders everywhere with each incidental tap. Is there a simple way to turn it off and on as wanted/needed? What about a way to have it stop "listening" for taps when typing? How does this work (or not) on the OS X side?

Thanks.

---

### Post by cyberdork33 on 2008-11-07
this used to be accomplished with syndaemon, but I think it will conflict with the new hal / fdi method of setting up the touchpad.

---

### Post by kosumi68 on 2008-11-07
The SHMConfig parameter is required to be TRUE, otherwise it might work.

---

### Post by m.musashi on 2008-11-07
Thanks for the feedback. In the past I used gsynaptics and added the SHMConfig "True" option to be able to disable tapping but it required opeing the touchpad applet each time to turn off and on. A solution but not great.

With the way the touchpad was enabled on the macbook, however, I suspected this path was no longer an option. I recall reading (in the last thread you helped me with) that modifying xorg.conf was not really the way to go now so I assumed the gsynaptics approach wouldn't really work. Is that true? I'm not quite sure I follow what you are suggesting.

It does not seem to be an issue on the OSX side so I'm not sure what they do differently. It doesn't seem to turn off when typing but maybe the tapping is or may the sensitivity changes. I don't know.

Thanks.

---

### Post by cyberdork33 on 2008-11-07
> **m.musashi said:**
> It does not seem to be an issue on the OSX side so I'm not sure what they do differently. It doesn't seem to turn off when typing but maybe the tapping is or may the sensitivity changes. I don't know.
It isn't that it is impossible to do, just that the previous method probably doesn't work, and a new utility needs to made, or the old one modified.

Go ahead and try changing the option, it can't hurt. If it messes things up, just remove the changes you made.

---

