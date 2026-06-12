---
title: "I have broken Ubuntu"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-10-17
I was doing something innocuous (I thought) - just re-installing ALSA and after a reboot I have a character based monochrome display. It is telling me - Kinit: No resume image, doing normal boot.
I can login to Ubuntu but have no gui.
Any help would be graciously received. Thanks.

---

### Post by Kosimo on 2007-10-17
did you try to type 

startx

---

### Post by linuxforrealpeople on 2007-10-17
I am intrigued now, If I login using startx I seem to have pretty much a fully functional system. What have I broken?

Thanks for reading this.

---

### Post by Keith_Burton on 2007-10-17
One possibility is the login screen/display manager. gdm in Ubuntu, and kdm in Kubuntu.

---

### Post by linuxforrealpeople on 2007-10-17
The solution was:
sudo apt-get install ubuntu-desktop

---

### Post by jc_madden on 2007-10-17
<post deleted>

---

