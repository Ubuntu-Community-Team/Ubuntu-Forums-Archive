---
title: "imac 266 g3 sound not working"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by Bong_Master_Darky on 2007-11-12
ok after taken ages to get ubuntu to boot correctly i now have another problem which is the sound it doesnt work tryed playing a mp3 no sound i got the codecs still no joy i know the soundworks on this mac as i hear the apple chime. im running 7.04 feisty fawn  

thanks :)

---

### Post by Auria on 2007-11-12
can you play e.g. the demo .ogg files that come in the example files?

---

### Post by PaganHippie on 2007-11-12
I had the same problem with my 233MHz iMac at first.  Try going into the sound mixer settings, turning on 'advanced settings,' then turning off 'auto mute.'  For some reason Ubuntu acts as if headphones are plugged in on these machines, and mutes the internal speakers.  Once 'auto mute' is disabled, you should hear all the regular system sounds and be able to play music.

This has been an issue with older iMacs and Ubuntu for well over a year now (since Dapper, possibly longer).  While it's relatively minor, it's probably not ever going to be fixed since PPC isn't a priority for the development teams anymore.  Kind of sad.

---

### Post by Bong_Master_Darky on 2007-11-13
hi  sorry for being total noob here but i cant find the advance mixer setting any where the only setting i can find is sound preferences but cant see anything about auto muting 

help

cheers:)

---

### Post by PaganHippie on 2007-11-13
It took me a while to find the setting; it's kind of weirdly hidden.  Let me look at my own setup again here....

Try this:  double-click on the little speaker icon in the upper right of the screen; this will bring up the mixer panel.  Select *Preferences* from the *Edit* menu.  A window appears asking which features you want to be visible in the mixer panel.  There should be a check box labelled *Auto Mute*.  Check it, and click *Close*.

Now a new tab, *Switches*, appears on the mixer panel.  Select that tab, and uncheck the *Auto Mute* check box that is there.  At this point, you are good to go, although you can go back into Preferences and hide (uncheck) the Show Auto Mute box there to get rid of the Switches tab if you want to.

It's kind of like going around your knee to get to your elbow, but it works.

---

