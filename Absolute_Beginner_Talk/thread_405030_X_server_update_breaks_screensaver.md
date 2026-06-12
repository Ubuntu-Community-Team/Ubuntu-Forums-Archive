---
title: "X server update breaks screensaver"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-04-09
Ok it seems that this problem with x server updates continues. I did a x-server update yesterday and thought I had made it this time as I can reboot just fine. Not too fast though! When I went to change screen savers this morning as soon as screensaver option is selected it throughs me right back to the log in screen. So, reinstall x server again? All of these problems are connected to nvidia drivers in some way. Will Feisty have  a cure for this maybe? ANY ideas out there?
Thanks

---

### Post by Perfect Storm on 2007-04-09
You install nvidia driver with envy?

---

### Post by Tucatts on 2007-04-09
yes I did I could never get the drivers to work with synaptic package manager.

---

### Post by Perfect Storm on 2007-04-09
Try with a reinstall of the driver and report back.

---

### Post by Tucatts on 2007-04-09
All fixed. I did alt-ctrl-F1 and put in sudo envy. I got to a blinking line and then did alt-ctrl-F1 again and followed the instructions about x server "yes" to all and then it went back to log in screen and it is fine. I have rebooted no problem, screensaver working ok etc. While this x server update thing  has been an ongoing problem I keep a log of what happens and how I fixed it so I can just go back and try to fix it. So far I have been able to get back to good spec's everytime. Learning. LOL.
Thanks for the interest.

Oh, I burned a Feisty Fawn beta live cd and that looks great. Will the nividia drivers be more stable in Feisty?

---

### Post by Perfect Storm on 2007-04-09
It's nothing about the Nvidia driver, it' when some big things changes in the Xorg then it's a possiblilty that the Video card driver needs to be reinstall or modified if you use drivers outside the repo (like envy or manually installed drivers).
So this can also happen in Feisty or other releases and distros. This can be due to that Nvidia drivers is close source.

---

