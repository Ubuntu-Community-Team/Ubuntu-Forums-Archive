---
title: "The Quest for Sound..."
date: 2008-08-17
forum: Apple Hardware Users
---

### Post by ericks13 on 2008-08-17
Now that I'm back to using Ubuntu, I'm faced with the same issue that caused me to leave it in the first place: I have no sound.  I feel like I have read every thread and every sticky and tried every, "fix", all to no avail.  ALSA drivers didn't work, manually editing files didn't work, nothing.  I'm running a 20" Aluminum iMac with the standard audio setup.  I'd just like to know exactly what is the best fix for Hardy, as of right now (forum stickies refer to an outdated ALSA driver).

---

### Post by cyberdork33 on 2008-08-17
I assume this is an aluminum iMac?

Did you try adding the module option shown here:
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

---

### Post by ericks13 on 2008-08-18
Adding the options line didn't help and nicfagn's patch calls for the adjustment: "sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko", but this file doesn't exist in my system and I don't know what to do from here.  Also, alsa-driver1.0.17 is out, so is that patch altogether outdated?

---

### Post by ericks13 on 2008-08-18
Okay, I followed [this]("http://ubuntuforums.org/showthread.php?t=831314") thread and have very poor sound when I added "snd-hda-intel model=mbp3" to the end of alsa-base and options (in /etc/modprobe.d).  On full volume it sounds like sound is being blasted out of headphones 2 feet away from me: low, but strained.  Anyone else ever get this?

---

### Post by shyo310 on 2008-08-21
I have iMac Aluminium and I tried EVERYTHING (model=mbp3, position_fix=1, probe_mask=1) but in the end I get really poor sound. My guess is that alsa driver still does not recognize something in the iMac sound system but I do not know what. Hope someone will know how to fix this someday.

---

### Post by Paindistributor on 2008-08-24
I installed ubuntu on my 20" iMac too. At the moment it's not a good idea to expect a good sound quality from the drivers. I got sound but... even the cheapest sound system would sound better than this. Has anyone tried the latest alsa driver? Perhaps it's a good idea to connect external speakers or at least headphones.

---

