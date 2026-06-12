---
title: "Nvidia go 7300 driver problems"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ryancpratt on 2008-03-30
I broke the number one rule : if it isn't broke, don't fix it!

I decided I wanted to update my Nvidia drivers using Envy. Bad Idea! It gave me an error message when trying to install them, so I clicked uninstall, which it did successfully. Then I went to try to reinstall and it gave the the same errors as before. So i reinstalled my nvidia_glx drivers from the synaptic package manager. I noticed that desktop effects were disabled, so I went into restricted drivers and reinabled them. Restarted. And I got an error message when loading saying something like kinit: cannot find resume image, normal boot now. Then it brought me to a black screen where my cursor turned to an X, and it told me to continue in a low graphics boot. I cannot reinable my desktop effects now, and my resolution will not got over 800x600. Help please!

---

### Post by smurphy_it on 2008-03-30
You could try rebooting, going into rescue mode (hit esc on grub boot menu) and once you are logging into linux type dpkg-reconfigure xserver-xorg

---

