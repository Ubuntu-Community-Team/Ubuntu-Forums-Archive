---
title: "No system sounds or any sounds for that matter"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by madbeader on 2008-03-22
I'm still new to Ubuntu, but I'm gaining on it, one issue at a time.
I'm getting no sound at all.  When I go to System/pref/sounds and check "sound events/autodetect" I get nothing when I test.  I select "usb audio" I get sound through my usb speakers at a very loud level that the volume control does not adjust.  When I test a system sound I get nothing.  What am I missing?
Thanks

---

### Post by Darganot on 2008-03-22
For starters:

Try double clicking the speaker for the volume control.  You should get a series of volume levels.  First click file and make sure you're using the right device.  This could be your problem if you have more than one sound card.

Then make sure none of the levels are muted and they are all at least above bottom.  Listen to a song or watch a youtube video.  Whichever changes the volume is what you want to set to the default mixer in the sound prefs you mentioned to make your keyboard volume keys work.

If this doesn't work post back with your sound card info.

---

### Post by Darganot on 2008-03-22
One more thing, check the prefs under volume controls to make sure all of the levels available are showing up.

---

### Post by madbeader on 2008-03-24
Thanks for your help on this issue.  My sound card is built-in to the MB and is being detected as HDA NVidia (Alsa mixer).  The speakers I'm using are Bose usb speakers which also show up as a mixing device option "Bose USB Audio (Alsa mixer"  I've tried this also and still no sound .  As I said I get a loud tone if I choose usb audio as the device but I still don't get any sound when I try to listen audio, cd or youtube.
What should I try next.  Up to this point I've been able to get everything else working.
Thanks again

---

### Post by sg1 on 2008-03-24
I'm also having sound issues since updating to Gutsy!!
I have noticed that this seems to be a "bug" at the moment in Gutsy and it only seems to effect Ubuntu.

---

### Post by ex-navy on 2008-03-24
Same problem here, with NVidia.

Probably a driver issue and only in Gutsy. I upgraded and lost the sound.

---

### Post by Darganot on 2008-03-24
This sounds like an ALSA issue that is beyond what I'm able to help you with.  Search around on these forums and the internet.  You can also check your hardware compatibility with Linux here:

[http://hardware4linux.info/](http://hardware4linux.info/)

---

### Post by madbeader on 2008-03-24
Thanks for the help.  I've restarted the computer numerous times in the last several days and the last time now I have sound without a change.  I hope it lasts.
Thanks again

---

### Post by sg1 on 2008-03-26
be nice to know what your original problem was though :(

I however am STILL having sound issues with my machine since upgrading to Gutsy!!
I'm using onboard sound from my [**_AsRock Alive NF5-SLI_**](http://www.asrock.com/mb/overview.asp?Model=ALiveNF5-eSATA2%2b%20R3.0) But can't seem to get anything out of changing all the sound settings in every possible variation I can see !!   HELP!!!

I will see if the Mobo's website has any answers:)

---

### Post by sg1 on 2008-03-26
I've had an idea to install a sound card into my PC rather than using the onboard sound to see if GUTSY detects that instead:)

   Maybe my onboard sound just isn't supported in this Ubuntu release, although it worked in 7.04 it may have been amongst the "deleted obselete packages" during the upgrade to 7.10??

I will let you know if i'm successfull:)

---

### Post by sg1 on 2008-03-26
**[SIZE="3"]I now have full sound!!! [/SIZE]**

I put in a Mercury(C-Media) card and now I have more WATTS than I know what to do with :)

I guess that my AsRock NF5 SLI-1394 mobo's onboard sound isn't supported yet in Gutsy !!

I hope this helps people in a similar situation:)

---

