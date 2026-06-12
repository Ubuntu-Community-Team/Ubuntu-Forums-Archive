---
title: "Reinstalling parts"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-09-26
Is it possible to reinstall parts of the original ubuntu os (the files and verisions that
are on the cd, in my case all graphics related stuff, since I managed to mess up those)?

or if not: Is it possible to reinstall ubuntu but keeping the user accounts, email configs,
downloaded programs etc?

---

### Post by KingBahamut on 2005-09-26
What exactly did you "mess" up?

---

### Post by red_Marvin on 2005-09-26
Before: 3d acceleration worked fairly by default, but lagged when I downloaded fglrx
drivers from synaptic.

Then I tried to upgrade the ATI drivers with help from the howto, but something went
wrong, and now I got no acceleration at all, or at the best a lagging one (synaptic drivers)

P4
Hoary hedgehog
ATI 9200

---

### Post by KingBahamut on 2005-09-26
Ahhhh....ok thats what I wanted to know. 

Ive never had success with installing the synaptic based drivers, to compound it, youve attempted to install ATI's drivers on top of that. Im guessing youll need to remove all the stuff you installed from Synaptic. Then re run the .run installer from ATI. then re run fglrxconfig to correct the issue.

---

### Post by red_Marvin on 2005-09-28
I took the easy way out and backed up /home and did a reinstall instead.
The drivers can wait, I have suficcient performance on bzflag with the original
setup, and I'll perhaps fool around later when I have more linux experience.

-But thanks for the help :)

---

