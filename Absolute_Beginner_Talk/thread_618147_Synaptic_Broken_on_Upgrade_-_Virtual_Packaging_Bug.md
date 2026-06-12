---
title: "Synaptic Broken on Upgrade - Virtual Packaging Bug?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by clubsoda on 2007-11-20
On upgrading synaptic from Gutsy Alpha to Gutsy ((0.60ubuntu3) to 0.60ubuntu5) I was left with a broken synaptic.  It would download packages but wouldn't install them, just sitting in limbo with the progress bar cycling around.

With some further investigation, two virtual packages were missing [libapt-inst-libc6.6-6-1.1 and libapt-pkg-libc6.6-6-4.5] which are supposed to be provided by packages apt and apt-utils.  I guess these should have been updated at the same time as synaptic(?)  Is this a missing dependency or a bug in the virtual packaging system?  Perhaps the earlier version of synaptic wasn't aware of the virtual dependency?

---

### Post by Anicka on 2007-11-20
Can you run the command ```
sudo apt-get update && sudo apt-get upgrade
```and post the messages you get?

---

### Post by clubsoda on 2007-11-20
Thanks Anicka for your suggestion.

Once I found out about the virtual packages, I used synaptic to download apt and apt-utils and then went back to the command line with gdebi to install them from /var/cache/apt/archives.  After that I was back in business.

Still not 100% sure why this happened though.  Is the virtual package concept new, such that synaptic_0.60ubuntu3 would have made a mistake?

---

