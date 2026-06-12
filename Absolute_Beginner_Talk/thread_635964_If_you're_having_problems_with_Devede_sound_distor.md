---
title: "If you're having problems with Devede sound distortion...."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-12-09
On Feisty or Gutsy.....try this.. it worked for me.  I had to use an old version of mplayer until I finally found this.  I hope it works for you like it did for me !!  It's an upgraded mplayer and mencoder that hasn't been mentioned for some reason.  This is from a bug report I've been following on this problem.

Go to "System->Administration->Software Sources". It will ask you the password.

Now, in that new tool, go to the tab "Third party software", check the
option "Unsupported updates (gutsy-backports)" and close the window with
the "Close" button (don't use the X in the window bar). It will ask you
to reload the packages list: do it.

Now go to "System->Administration->Synaptic" and install the
Mplayer/Mencoder packages, or you can do all the updates.

When you have finished, you can uncheck the "Unsupported updates
(gusty-backports)" option to avoid the update manager to replace other
packages. Or you can leave it and have your system with the really last
versions of the packages (remember that in Backports are always newer
versions than in the official distribution, but they aren't officially
supported.

---

### Post by MrKlean on 2007-12-09
shove ; )

---

### Post by freesitebuilder on 2007-12-20
I've updated Mencoder, but I'm getting no sound at all on Preview. My test input file is ogg, downloaded from the Ubuntu clips site. The sound is OK when I play the original file - should there be sound on Preview, or only once the disc is finally created?

---

### Post by taenus on 2007-12-22
Great bit of help.  It fixed the problem for me.  I was using a mpg from a ReplayTV 5xxx as the source.

---

