---
title: "sound doesn't work on hoary"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by viZ_5 on 2005-09-22
hi!  I've just installed ubuntu and it works great except that sound doesn't work.  I've got a Yamaha XG soundcard on a P3.  Can someone help please? O:)

---

### Post by holiday on 2005-09-22
[QUOTE=viZ_5]hi!  I've just installed ubuntu and it works great except that sound doesn't work.  I've got a Yamaha XG soundcard on a P3.  Can someone help please? O:)[/QUOTE]
 Have you checked System.Preferences.Sound?
You may have to select in your sound card. 

If you don't recognize it, check Device manager to see what he thinks he's looking at.

---

### Post by Kapre on 2005-09-22
[QUOTE=viZ_5]hi!  I've just installed ubuntu and it works great except that sound doesn't work.  I've got a Yamaha XG soundcard on a P3.  Can someone help please? O:)[/QUOTE]
 viZ_5 - Go to your Multimedia Systems Selector and play with your sound settings. This is If you already followed holiday's suggestion 1st.

K

---

### Post by viZ_5 on 2005-09-25
I checked System.Preferences.Sound, and on the version of Ubuntu that I have, I'm only given options on what sounds to play (.wav) files, rather than sound cards.  I had a look at Device Manager... holiday, could you tell me what I should be looking out for?

Kapre, I played with Multimedia Selector, and ALSA, ESD and OSS all came up with "Failed to construct test pipeline".

---

### Post by tehwa on 2005-09-25
I once spent 40 odd minutes trying to get sound working on an Ubuntu box without realising i hadn't plugged the speakers int the sound card. Make sure you triple check :).

Then check your volume levels for both your speakers, and through Applications > Sound and Video > Volume Control.

Then browse to [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly), which I find usually does the trick.

edit: System > Preferences > Sound will only affect things like sound events, it wont allow you to adjust your sound settings.

---

