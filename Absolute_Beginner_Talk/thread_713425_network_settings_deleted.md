---
title: "network settings deleted"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by enetic on 2008-03-02
2 days ago, i was using my laptop like some other random day. i decided to turn it off and go to bed. the next day, the driver for the networkcard was deleted. 


i cant figure out whats wrong.. the driver just dissapeared! :confused:

When i installed ubuntu on it the drivers was detected automaticly, so i dont know what to do...


can someone give me suggestions ? 


thanks //enetic

---

### Post by PapaNerd on 2008-03-03
It would be unusual for a driver to simply disappear.  Checking basic (layer 2) connectivity would be a place to start, just in case the driver doesn't load properly if the hardware can't see an active link.  Questions that might help others trying to assist you on this:
What is the make/model of the laptop?
Are you seeing link lights, either at the connector on the laptop or on the hub/switch to which you are connected?
What does the "network" section from the "lshw" command reveal?
From a terminal window, what is the output from the "ping localhost" command?
What is the content of the "/etc/network/interfaces" file?

---

### Post by enetic on 2008-03-04
the brand is Hewlet packard. DV6000. the laptop light is red now because its not working. when working it should be blue. when im doing a "ping localhost" im getting replys. 


when i go to system - administration - restricted drivers manager the network card is gone.

---

### Post by PapaNerd on 2008-03-05
Short of having a manual, or calling HP (and speaking to someone in India), I cannot help on the indicator lights.  What I can say, however, is that I have a machine that has two NIC's, and neither one shows up in the "restricted drivers" list even when they are operating correctly, so this could be something specific to your laptop.  Perhaps someone with an HP DV6000 can step in here and assist you.  It would be nice to be able to divide the problem in half and (A) determine whether or not there is an underlying physical hardware problem that causes the driver not to load, and/or (B) can supply you with a copy of their driver (if needed).

---

