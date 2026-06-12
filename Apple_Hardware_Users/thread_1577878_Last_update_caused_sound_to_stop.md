---
title: "Last update caused sound to stop"
date: 2010-09-19
forum: Apple Hardware Users
---

### Post by blueridgedog on 2010-09-19
Macbook Pro 7,1 (current model) - sound worked after adjusting as described here:

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound)

Sound stopped after allowing system to update today.

---

### Post by blueridgedog on 2010-09-21
bump...

---

### Post by jamesey on 2010-09-21
what do you see when run alsamixer in terminal? any of the volume levels at 0?

---

### Post by blueridgedog on 2010-09-21
All values are as they were before the update...was the first place I went.

---

### Post by lkjoel on 2010-09-24
> **blueridgedog said:**
> Macbook Pro 7,1 (current model) - sound worked after adjusting as described here:

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound)

Sound stopped after allowing system to update today.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by comgen on 2010-09-25
I have several PPC's ( G4/G5 ), removing / commenting out if present: snd-powermac in /etc/modules ( #snd-powermac ). Resolved sound issues I ran into after (1) upgrade and (2) fresh installs of 10.04 LTS.
Also not related, ejecting the DVD/CDROM was a problem for an end-user ( no eject button and KB key does not map correctly, standard US KB ). Created a simple script and launcher using the " eject cdrom " command.
#!/bin/bash
# Ubuntu 10.04 LTS PPC G4 CD TRAY eject
eject cdrom

---

