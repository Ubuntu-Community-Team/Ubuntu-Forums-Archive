---
title: "Getting Firefox to share profiles between os's nicely"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by cellarmation on 2007-01-08
I thought it would be a clever idea to get Firefox and Thunderbird to dual boot between Ubuntu 6.10 and windows xp. It works well but there is a couple of annoying problems:

# Whenever i load Firefox for the first time after using it in the other operating system, it thinks that i have just installed it and shows me a welcome screen. Any way of disabling it?

# The download location is either invalid for Linux or for windows so i have to change it a lot, anyway to store one for each os?

---

### Post by fsando on 2007-01-08
I'm interested in doing the same:
Could you detail how you did it?

---

### Post by cellarmation on 2007-01-08
There is quite a bit of info about on the net for this, luckly its very simple because firefox and thunderbird are great. Basically Linux and windows can both read and edit fat32 partitions, because its an old type. So i have my firefox and thunderbird profiles located in this fat32 partition.

You can then use the profile manager to create a new profile and as you go through the options you can pick a current folder location, pick the folder on the fat32 drive. You can do this for thunderbird and firefox. Try not to have to many addons installed.

---

### Post by fsando on 2007-01-08
Thanks - yes I should have researched that myself as I have long time shuffled my settings from one install to the other with no problems - just the profile manager I wasn't aware of.

Regarding your question, I think you should ask it in the mozilla forums instead - as the same thing happens when you use two different versions of firefox/thunderbird on one platform.
Probably there is some 'unrecommended' hack - like the max version hack.

---

