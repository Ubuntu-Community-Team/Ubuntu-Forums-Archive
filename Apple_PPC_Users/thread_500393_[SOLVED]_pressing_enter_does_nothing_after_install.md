---
title: "[SOLVED] pressing enter does nothing after install and removing cd at reboot on G3"
date: 2007-07-13
forum: Apple PPC Users
---

### Post by visible on 2007-07-13
just got a G3 for nothing and went and installed fiesty on it but have encountered a problem.  reformatted the drive and install went well until the end when I go to reboot.  at the point where it ejects the cd and asks you to close the tray and press enter, I press enter and nothing happens.  can anyone help?  I'm not real familiar with macs to begin with.

---

### Post by visible on 2007-07-13
figured it out.  in yaboot I had to type device=hdc partition=3
works great now

---

