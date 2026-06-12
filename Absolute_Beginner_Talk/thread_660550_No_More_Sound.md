---
title: "No More Sound"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-01-06
Hey everyone. About 10 minutes ago, I came onto my Ubuntu box, which was in a sleep more. I pulled it out of it, but my speakers no longer worked. I did a reboot, but still no sound. Does anyone know why this is and how I can fix it? Thanks.

---

### Post by PetePete on 2008-01-07
try this, has worked for me before

sudo apt-get remote alsa-base alsa-utils

sudo apt-get install alsa-base alsa-utils

reboot...(for good luck!)

---

### Post by ubername on 2008-01-07
> **PetePete said:**
> try this, has worked for me before

sudo apt-get remote alsa-base alsa-utils

sudo apt-get install alsa-base alsa-utils

reboot...(for good luck!)

When you've done that run 'alsamixer' from a terminal and check that none of your main output channels are muted (MM appears beneath the bar showing the vollume of each output.)

Use M to toggle mute on or off.

---

### Post by olejorgen on 2008-01-07
If you dualboot, try booting windows and make sure everything is unmuted. The *shutdown* windows, and boot linux. My toshiba's sound was suddenly gone. Turned out I had muted it in windows and this strangely enough killed it in ubuntu.

---

### Post by drndrw on 2008-01-09
I tried these options and still nothing :(. I had this problem with Feisty, and it was never solved. THen I upgarded o GUsty and it worked fine up until a few days ago. How do you think this could have happened?

---

