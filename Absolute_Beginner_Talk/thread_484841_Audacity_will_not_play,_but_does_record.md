---
title: "Audacity will not play, but does record"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by SamMessing on 2007-06-26
Hello,

I tried to search for an answer to this problem, but couldn't find one for this particular error message. Audacity seems to be recording sound fine, but when I got to play back what I just recorded, I get this error message:

Error while opening sound device. Please check the output device settings and the project sample rate.

Does anyone know what I should do to fix this? Or where to look for a solution?

Thanks!

---

### Post by ramjet_1953 on 2007-06-26
If you don't already have it installed, use the Synaptic package manager to download [COLOR="Blue"]alsa-oss[/COLOR].

Next, in a terminal, start Audacity with the command [COLOR="Red"]aoss audacity[/COLOR].

The reason for this is because Audacity is basically an OSS package and the latest versions of Linux use ALSA for sound.

If this fix works, just change the startup command for Audacity in [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and right click on  Audacity and choose properties.

You should also have a look at your settings in your mixer, by right clicking on the [COLOR="Blue"]speaker icon[/COLOR] in the top panel and selecting [COLOR="Blue"]Open Volume Control[/COLOR].

Choose[COLOR="Blue"] Edit Preferences[/COLOR] and make sure that most options are ticked, except maybe things like video, external amplifier.

Next, click on the [COLOR="Blue"]Recording Tab[/COLOR] and make sure that the sliders are maximum, or close to it and also make sure that there are no red X's on the two icons below the slider.

Next, click on the [COLOR="Blue"]Switches Tab[/COLOR] and select your input source.

Hope that this helps.

Regards,
Roger :cool:

---

### Post by Benjcrowe on 2007-07-06
Thanks for the info. Audacity suddenly went south for no reason I could see.

The OSS/ALSA explanation did the trick.

It's always something.

By the bye - the mixer is labled as an ALSA mixer using the Intel ICH-4device. Audacity is using the OSS one. Doesn't seem to matter. Does it?

---

