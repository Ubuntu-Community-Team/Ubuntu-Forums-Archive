---
title: "can't play cd in xmms/audacious"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-03-12
i'm using e17 on edgy. a cd will play, without issue, using xine-ui, but not with either xmms or audacious. i have the cd read plugin for xmms installed and all the audacious plugins installed as well. when i click on 'play cd', i get an error saying "no playable cd found".

solved: preferences>plugins>cd audio plugin (click preferences) - switch play mode from analog to digital audio extraction

i think i had to do that the first time i ever used xmms.

---

### Post by raym0nd on 2008-01-04
> **fuscia said:**
> 
solved: preferences>plugins>cd audio plugin (click preferences) - switch play mode from analog to digital audio extraction
.
I have solved a similar problem by changing Device>Directory> from /mnt/cdrom to /media/cdrom
in  preferences>plugins>cd audio plugin (click preferences).
Thanks for pointing out how to find the "CD Audio Plugin " preferences in Audacious.

---

### Post by studo77 on 2008-05-01
Had problem playing CDs also. Using Audacious 1.5.0, what did the trick for me was not to ask CDDB for info. (plugin pref. remove CDDB check)

---

