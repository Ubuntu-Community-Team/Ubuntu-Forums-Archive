---
title: "isight tools error on install"
date: 2011-05-01
forum: Apple Hardware Users
---

### Post by clenny on 2011-05-01
Hello everyone. I recently installed Ubuntu 10.04 on a Macbook 7.1 and was able to get everything to work except for the isight camera. I visited a lot of forums and tried a number of fixes but failed to get it to work. I just upgraded to 11.04 and in the course of the install the following error was generated:

Could not install '/var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb

Then:

subprocess new post-removal script returned error exit status

I'm curious if others who are running Ubuntu on a Macbook are experiencing the same error. I hope someone can suggest a fix for it also. I probably should mention that I overwrote the entire drive so the Apple drives aren't in a partition on the HD and I had downloaded the isight tools that I tried to install on 10.04 from a link provided in an Ubuntu forum.

Thank you in advance.

---

### Post by Hatsune Miku on 2011-05-02
> **clenny said:**
> Hello everyone. I recently installed Ubuntu 10.04 on a Macbook 7.1 and was able to get everything to work except for the isight camera. I visited a lot of forums and tried a number of fixes but failed to get it to work. I just upgraded to 11.04 and in the course of the install the following error was generated:

Could not install '/var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb

Then:

subprocess new post-removal script returned error exit status

I'm curious if others who are running Ubuntu on a Macbook are experiencing the same error. I hope someone can suggest a fix for it also. I probably should mention that I overwrote the entire drive so the Apple drives aren't in a partition on the HD and I had downloaded the isight tools that I tried to install on 10.04 from a link provided in an Ubuntu forum.

Thank you in advance.

The isight firmware tools gets the driver from the kext on an apple partition... you need a Mac OS X install to use the firmware tools... sorry.

---

### Post by clenny on 2011-05-08
I guess that's that then. Until someone comes up with a workaround....

Today, an iSight tools package appeared in my update list but I was unable to download and install it. Perhaps for the reasons stated in Hatsune's post above?

---

