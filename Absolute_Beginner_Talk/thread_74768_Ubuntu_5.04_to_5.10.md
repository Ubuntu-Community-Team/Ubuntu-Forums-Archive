---
title: "Ubuntu 5.04 to 5.10"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by davidjneff on 2005-10-12
I'm very new to Ubuntu, but not new to Linux.  Used to run/own an ISP based on Linux.  At home, I've tried Mepis and Fedora, and a co-worker gave me a Ubuntu CD because Fedora was a pig on an old low memory Celeron PC.

I am very impressed.  Have put it on all 3 of my very different PCs, and have had zero problems -- everything, sound, video, networking, worked right off the bat.   On two of the three I had to download some extras and tweak xorg.conf to get accellerated video, but thats it.

Anyway, I installed 5.04 on all my PCs, have taken the updates.  As long as I take the Ubunutu updates, will my system be virtually identical as 5.10 when it is released, or is there any reason to re-install?  I poked around the site to get the answer to this and its probably somewhere, but I couldn't find it.

---

### Post by bored2k on 2005-10-12
[http://ubuntuguide.org/#upgradehoarytobreezy](http://ubuntuguide.org/#upgradehoarytobreezy)

That is all that's needed to upgrade to Breezy.
Tip: make sure ubuntu-desktop is installed before upgrading.

---

### Post by invalid on 2005-10-12
To turn 5.04 into 5.10, you will need to change your update sources.
Open /etc/apt/sources.list and change all occurances of "hoary" to "breezy"

Hope this answers your question
Cheers,
Cb

---

