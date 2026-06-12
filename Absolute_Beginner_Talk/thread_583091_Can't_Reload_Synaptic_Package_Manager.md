---
title: "Can't Reload Synaptic Package Manager"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by iggyigg on 2007-10-20
I'm using Feisty 7.04 and when I click on the reload button for the Synaptic Package Manager, it jumps to “downloading File 27 (out of 35)” in a second but then gets stuck, moving no further.

This message appears in the dialog box:
[B][http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to fr.archive.ubuntu.com:80 (194.2.0.36), connection timed out

[http://fr.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to fr.archive.ubuntu.com:80 (194.2.0.36), connection timed out[/B]


When I try to add a program from the “Add programs” application, it also gets blocked.

As there seem to be problems with Gutsy and I'm a complete novice, I thought it would be a good idea to let the experts sort out the wrinkles, before upgrading myself!  Is it a problem using Feisty to access Package Manager etc? Or is it perhaps because of everybody trying to upgrade to Gutsy?

:confused: Many thanks for any help!

---

### Post by Kosimo on 2007-10-20
Maybe french servers are down or in maintenance. 

Just change them to the main server or US one witch is always working.


System > Administration > Software sources:

Then: Download from.. And try another one,

---

### Post by Paqman on 2007-10-20
> **iggyigg said:**
> Or is it perhaps because of everybody trying to upgrade to Gutsy?

Thats a pretty good bet, especially if you can normally connect to those two.

---

### Post by Dr Small on 2007-10-20
Yes, the connection is timing out, because the servers are still apparently loaded. We expected this load to drop off in 24 hours, but now it appears there were more people upgrading that what we thought (or downloading).

As Artificial Intelligence stated in his sticky, for upgrading Gutsy, wait at least a month and then upgrade. There will likely be less bugs in it, and the servers would not be as boggled down then.

Dr Small

---

### Post by Pumalite on 2007-10-20
Myself, I'm not using apt-get or Synaptic for a couple of days.

---

### Post by iggyigg on 2007-10-20
Thanks very much for your help, everybody! I'm ASTONISHED by these quick replies! :KS

---

