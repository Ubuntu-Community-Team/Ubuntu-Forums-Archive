---
title: "adept_notifier always on"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ulriks on 2006-11-14
Hi all,

My adept_notifier is always on and always tells me that 1 updated package is available. 

How do I make it behave normally again?

Thanks
Ulrik

---

### Post by mblinux on 2006-11-14
Maybe for some reason the update fails to install so it is always there as available. Check if it is effectively gets installed. 

You could also try to install synaptic and do the updates from it (and see if there are trully available updates) or update from the command line.

---

### Post by ulriks on 2006-11-14
It is not the update that fails. 

If I start the updater by clicking on the Nofifier, it turns out that there are no packages (or more than one, depending on whats available) to be updated. Also if I update from the commandline, the packages are installed (if there are any), but the notifier still tells me that "1 updated package is available".

---

### Post by mblinux on 2006-11-14
Just in case...and please forgive me for my stupid answer: Quit the notifier then reboot. Do you still see the notifier saying 1 update available?

---

### Post by mblinux on 2006-11-14
Maybe these could help:

sudo apt-get update
sudo apt-get clean

---

### Post by ulriks on 2006-11-14
None of it helped :-D

Just ran the Adept Updater, with the result 'Nothing to Update' and still the same old message form Adept Notifier...

---

