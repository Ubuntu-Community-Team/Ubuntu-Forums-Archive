---
title: "No eth0 network by default on nForce4 - FIX!"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by six on 2006-07-20
I've just re-installed Ubuntu on my SN25P (nForce4). Just like the last time I installed it, the eth0 network connection wasn't enabled by default. The icon wasn't present in the top right notification area, either. The automatic-updater didn't work, because it couldn't find the repositories.

This time I made a note of how to fix it:

1. Go into System -> Administration -> Networking
2. On the Connections tab, click on the Properties button.
3. Switch (temporarily) from DHCP to Static IP
4. Switch back to DHCP, press OK

(a message "activating eth0" should appear)

5. Make sure eth0 is showing against Default Gateway Device:

Launch Firefox and check the ubuntu.com site comes up.

You should now be able to carry on with the automatic-updater, although you'll probably have to add the network icon manually.

Note: You might have to repeat this a time or two, for example when rebooting after installing a new kernel. It should start "remembering it" after a while... ;)

EDIT: Interestingly, although Ubuntu 32-bit doesn't seem to like nForce4 boards (at least to start with), there is no such problem with the Ubuntu 64-bit I'm currently installing. Synaptic and Firefox both worked straight away. One for the developers to wrap their heads around, perhaps? :p

---

