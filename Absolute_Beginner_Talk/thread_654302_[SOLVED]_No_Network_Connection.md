---
title: "[SOLVED] No Network Connection"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2007-12-30
Last night I updated 7.04 and now when I start up I get a HAL error but everything seems to be fine other than the network status showing that I am not connected when in fact I actually am. can any one help with this?

btw, there was a HAL update file in with the updates.

Oh, one more thing, I have a Wubi install of 7.04. when I logged on after the update I could not get a network connection so I logged out started windows replaced my home.virtual.disk with a previous one that I saved when I uninstalled an reinstalled.

---

### Post by akimatsu123 on 2007-12-31
check to see if you have the latest driver installed. also check your restricted drivers list and see if the necessary ones are enabled. sometimes wireless (if you do wireless) cards are restricted drivers (at least for my computer it is).

try "ifconfig" in the terminal and see if your eth0 (this is for cable connections) has an IP address. if you use PPPoE check to see that that is correctly configured too.

---

### Post by tad1073 on 2007-12-31
I believe I have the latest drivers installed, because I have a connection to the internet, but, the network icon shows a red x on it. I have no wireless card so that is not an issue. I checked ifconfig and as far as I can tell everything is ok. Do you have any ideas on the Hardware Abstraction Layer error?

---

### Post by tad1073 on 2008-01-02
I still have one problem when starting ubuntu, I get a harware abstraction layer hald error 1. can anyone help with that.
E: havp: subprocess post-installation script returned error exit status 1 is the error I get with clamav, I need some help with that also.

---

