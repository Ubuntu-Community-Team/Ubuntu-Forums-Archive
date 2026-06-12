---
title: "[Newb] Add/Remove troubles are the servers down?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Resin on 2007-04-29
Hi everyone,  I have just migrated back to ubuntu after a few years (sick of windows load times).  Anyway the problem i'm having is using the add/remove program in the application menu.  I'm trying to install things such as azeurus/amule/games  and i keep getting failures mainly timeouts.  I was wondering if the servers distributing these files are down?

It cant be my connection as everything else is functioning perfectly.

Any ideas?

---

### Post by Nythain on 2007-04-29
sudo apt-get update
sudo apt-get install azureus amule
what does it say???

---

### Post by [S|G] on 2007-04-29
Try to edit your /etc/apt/sources.list and remove the "us." in the servers URLs, or replace them by some other country prefix (br.archive is working well for me right now). It seems that there are indeed some trouble with the servers lately.

---

### Post by Resin on 2007-04-29
> **Nythain said:**
> sudo apt-get update
sudo apt-get install azureus amule
what does it say???

Worked a treat! Your a legend!

Mods can delete thread now =)

---

### Post by Nythain on 2007-04-29
then yeah, it was probably just temporary server issue... if it persists then i would follow the above advice about editing /etc/apt/sources.list and changing the two letter country code...or removing them all together, i've had pretty good luck without using a country code on all the repos

---

