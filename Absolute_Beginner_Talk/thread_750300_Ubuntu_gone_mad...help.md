---
title: "Ubuntu gone mad...help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by StOoZ on 2008-04-09
yesterday all was ok, today I came turn on the computer, I noticed that compiz was turn off, no effects, So I turned it on, and restarted the system, after the loading screen, It said "no singnal" to the screen... so I went to safe mode, uninstalled compiz + nvidia driver.
now whenever I let ubuntu to install its own glx nvidia driver, it goes to low graphics mode, whenever I try to install the nvidia drivers using envy (what I did when I first installed ubuntu..and it was OK), it goes back to the "no signal" thing...
the restricted drivers has this two lines:
NVIDIA accelerated graphics driver (latest cards)
Vmware kernel drvier << this is the one in use now.

how can I solve this issue?

---

### Post by bumanie on 2008-04-09
Which nvidia card have you got? Have you uninstalled envy or is it still active. There are many who find envy good, but there are also nearly as many who find it gives nothing but problems.

---

### Post by StOoZ on 2008-04-09
Envy is still installed, but the nvidia drivers that it installed were removed.
until yesterday all was great with envy, I cant come up with any reason to this mess... :(

---

### Post by bumanie on 2008-04-09
I would uninstall envy and start again from scratch. Never having used envy, I can't help with that aspect. Usually the ubuntu driver works well with nvidia cards. You could also use the linux driver from nvidia's website. Personally, I would get rid of everything and go back to the basic vesa driver and start again with configuring the card. Which nvidia card are you running?
Was there any updates that you did? Sometimes they can cause a conflict that was not there before.

---

### Post by StOoZ on 2008-04-09
Im using a 6600GT AGP card.
cant remember any update... \-: 
:(

---

