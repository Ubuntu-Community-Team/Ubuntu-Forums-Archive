---
title: "3 way boot mess"
date: 2007-01-22
forum: Apple PPC Users
---

### Post by Uta on 2007-01-22
I need help having Ubuntu reclaim the booting functions on my computer.
I installed openSUSE PPC on my mac G4 and now I can only boot into SUSE. Yikes.
How do I get Ubuntu and Mac OSX  to be listed in yaboot?

Mac OSX and Ubuntu,6.10 are on my main HD /dev/hda3 and /dev/hda5, SUSE is on /dev/hdb6
Thanks!

---

### Post by mandrakethepenguin on 2007-01-22
This is a more apropiate question for SuSE users in a SuSE Forum

---

### Post by linear on 2007-01-22
My guess is that you'll need to roll your own yaboot.conf. You can start with the info [here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml").

---

### Post by Uta on 2007-01-22
Thank you, your suggestion was helpful--
Yaboot exlained!
-------------------------------------------------------
I reinstalled Edgy and it fixed yaboot. I now have a 3 way boot on my power mac g4. Mac OSX,Edgy and openSuSe PPC 10.2

---

