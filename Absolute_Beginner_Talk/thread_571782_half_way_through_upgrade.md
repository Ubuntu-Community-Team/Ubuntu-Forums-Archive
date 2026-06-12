---
title: "half way through upgrade"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-09
yes half way through error stopped the update manager and has left me in an unstable position.

how do i continue the upgrade?

---

### Post by Paqman on 2007-10-09
How unstable? Can you launch the update manager from the administration menu and complete the upgrade?

---

### Post by skymera on 2007-10-09
yeah i can.

but it says im up to date.

yet it still had lots to do!

ive tried apt-get upgrade
dist-upgrade

i dont wanna restart incase it breaks

---

### Post by Paqman on 2007-10-09
Well, if you're running ok right now you could take the opportunity to back up your data in case it dies after rebooting.

---

### Post by skymera on 2007-10-09
whats to back up?

i have all my sensitive data on windows

pics, music, etc

---

### Post by Whiffle on 2007-10-09
try 

'apt-get upgrade'

w/o the dist upgrade.  The updater has already updated apt to gutsy, so when you run dist up grade it thinks you're already there.  apt-get upgrade should get the rest of the packages

Same thing happened on mine, i ended up running apt-get upgrade and apt-get update a few times and it finally finished up.

---

### Post by skymera on 2007-10-09
they dont do anything.

syas there is none to upgrade.

yet it caused an error when upgrading

---

### Post by Paqman on 2007-10-09
> **skymera said:**
> whats to back up?

i have all my sensitive data on windows

pics, music, etc

Ah well, you're pretty bombproof then. 

The only things i'd worry about backing up are your /home directory (particularly your .gconf settings) and your [ list of installed applications](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by skymera on 2007-10-09
pff if it breaks, it breaks.

it takes minuted to install, plus peop,e say fresh is best

im going to try a restart

---

### Post by Whiffle on 2007-10-09
Whats the error? 

I looked back through my bash history and this is what got me through it:
```

apt-get install pygtk
dpkg --configure -a
apt-get update
apt-get upgrade
apt-get -f install
apt-get update
apt-get upgrade
apt-get update
apt-get upgrade
apt-get -f install
apt-get autoremove
apt-get update
apt-get upgrade

```

:-P

---

### Post by skymera on 2007-10-09
it said it was going to do

dpkg --configure -a

nothing happened, ive restarted, no crashes yet, compiz dosent work.

but still no updates

---

