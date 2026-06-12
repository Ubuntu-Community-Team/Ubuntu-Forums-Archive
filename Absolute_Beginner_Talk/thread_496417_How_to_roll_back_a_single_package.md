---
title: "How to roll back a single package?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by oliveri on 2007-07-09
Is it possible to roll back a single package using the package manager, apt-get, or similar? Something like the FreeBSD portdowngrade?

I ask because: after the most recent upgrade of gimp I can't open JPEGs from my Olympus camera.  It turns out that there is a bug in libexif  that had previous to the upgrade been stripping the exif information and now just returns an error when I try to open a JPEG with gimp. 

If I can just go back one version to the way gimp/libexif I had before, I could at least still use gimp.  However, the choices available in "force version" in Synaptic only offer the current version and an "insecure" version of the current version. Synaptic also seems to be rigged so that dependencies are rigidly assigned by version (which would be fine if stuff like libexif worked! But now the idiot-proofing is working against me).

Thanks!

---

### Post by Keen101 on 2007-07-09
should be possible. open synaptic. find your file (libexif or whatever) then right click on it and there should be some menu option like "force downgrade" or something. haven't done it in awhile, so not exactly sure what it say's.

good luck :)

-keen101

---

### Post by Keen101 on 2007-07-09
I just replied to your other post. "force version" should work given that you actually have an older version to downgrade to. Try adding an older cd to your repository.


good luck :)

=keen101

---

### Post by anemon on 2007-08-11
I have the exact same problem with my new Olympus camera, but I don't have an old Ubuntu CD -- and it just seems a bit awkward to download an old CD image and burn it to a disc just to get my hands on an older version of libexif! Isn't there a version history somewhere on the Internet where you could find it? (No luck with the Sourceforge site, I'm afraid...) Or perhaps the Ubuntu team could make it available?

---

### Post by Keen101 on 2007-08-13
Not that I know of.   Maybe someone else does though.

Make sure you report this bug on launchpad... otherwise it may never get fixed.

You could try to find an older version either with an older cd or with the goog.

(an older cd does seem a bit out of the way, but if it solves your problem..... then hey.)


Otherwise, just wait for a newer fixed version.

Sorry I can't be of any other help.


-keen101

---

