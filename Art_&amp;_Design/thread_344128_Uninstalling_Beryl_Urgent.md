---
title: "Uninstalling Beryl: Urgent"
date: 2007-01-22
forum: Art &amp; Design
---

### Post by mattmagician on 2007-01-22
i am running this through terminal, as Beryl has made it so that i cant log into any others.
please tell me how i can unistall beryl and its coponents through the terminal
thanks
matt

---

### Post by Sqwishy on 2007-01-22
sudo apt-get --purge remove beryl

beryl shouldn't break gdm, most likely it's a problem with you switching drivers.

---

### Post by mattmagician on 2007-01-22
would running that fix that problem?

---

### Post by jbayone on 2007-01-22
I had a simalar problem and needed to remove Beryl, but afterward X crashed and in the log it said that I didn't have Xserver loaded and needed to reinstall it.

---

### Post by Sqwishy on 2007-01-22
if you changed you're driver in xorg.conf you might need to change it back. usualy when you install your driver it may not work properly so beryl doesn't work. its usualy not beryl's fault

---

