---
title: "ye olde black screen of &quot;linux hates you&quot;"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by colinhayes on 2009-01-21
well, after having a nice stable installation of 7.10, I decided to try and upgrade my tri-booting powermac G5 2GHz with an ATI Radeon 9600.  I recall in the upgrade from the previous version, I ran into the black screen of death (instead of a login screen.... X failing to boot), and had to work through it.  I THOUGHT that the option "NoInt10" "true" addition to my xorg.conf file is what fixed it.

Apparently I am wrong.  I am using the same xorg.conf file, and I am still getting the black screen.  I get the feeling that it might have to do with the xserver-xorg-video-ati driver.  working version was 1:6.6.3-2ubuntu6, and I downloaded the binary of this and attempted to install it via a ctrl+alt+f1 terminal, and it gives conflicts, essentially saying that it is way too old to work with the core x system installed.

am I barking up the wrong tree with the ati driver? I know there are problems with it working with older cards like mine...

what can I do?  any ideas?  I will only point out my limitation of not having a wired internet connection (please don't ask me to lug the 50lb computer into another room and set it up on the rolly chair next to the only cable outlet in my house)

---

### Post by avtolle on 2009-01-22
What I had to do was select fdbev as the driver (different video card, though, although still ATI). I get a message about running in low graphics mode on start, but once the system is up, I get the desired resolution from my hand-edited xorg.conf file. 

Note: I have two G4 cubes, not a G5, but as this is a video problem, thought I'd offer the above.

---

### Post by colinhayes on 2009-01-22
would I simply edit my xorg.conf to read fbdev instead of ati, or does it require any further modification?

---

### Post by avtolle on 2009-01-22
That's what I'd try first. If that doesn't help, then perhaps others will have some ideas.

---

