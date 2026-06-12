---
title: "LCD dimming keys not working mbp 5,3"
date: 2010-06-14
forum: Apple Hardware Users
---

### Post by bradrocks on 2010-06-14
On the mbp 5,3 running 10.04, I'm trying to get the screen dimming keys working. Using the tutorial [http://https://help.ubuntu.com/community/MacBookPro5-3/Lucid#Video]("http://https//help.ubuntu.com/community/MacBookPro5-3/Lucid#Video") I followed the instructions for the nvidia-bl-dkms package.
Initially upon configuration, the dimming keys work wonderfully, but after a restart, they don't work at all.
Any thoughts?
Thanks.

---

### Post by ennui. on 2010-06-22
Yargh! I am having the exact same problem. Macbook 5.3, followed the guide listed above, LCD dimming worked until restart :(  any ideas?

---

### Post by alexmurray on 2010-06-22
The macbook pro probably needs nvidia-bl-mbp-dkms not nvidia-bl-dkms - try uninstalling nvidia-bl-dkms and install nvidia-bl-mbp-dkms instead and see if that works better.

---

### Post by Helios747 on 2010-06-25
is "nvidia-bl shift=2" in /etc/modules?

---

