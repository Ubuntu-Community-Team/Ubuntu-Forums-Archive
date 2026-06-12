---
title: "I Don't Understand Automounting - Part 2"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-02-08
First, thank you for the replies on mounting USB thumb drives. I have abandoned my attempts to install autofs and now have a couple of questions I haven't found the answers to:

An icon for any USB flash drive that has been automatically mounted remains in /media even after I have unmounted/removed it. Is there a way to prevent the drive from being displayed when it is not connected? I have about five USB flash drives I connect from time to time and I would prefer not to see them all displayed when I open up /media in office.

Secondly, I don't seem to have to option to unmount the drive by right clicking the drive icon - it is not listed in the menu. How can I get that option to show up?

Third, the various USB drives show up in nautilus differently. They variously show up at sda, sda1, or some with the name assigned in properties. How can I standardize things so they always either show up as /dev/sda1  (or whatever) or by the name assigned to them in 'properties'?

I don't have any flash drives listed in fstab. Are there any advantages or disadvantages to doing so?

Thanks.

---

### Post by Magnes on 2007-02-08
Maybe this will help: [https://blueprints.launchpad.net/ubuntu/+spec/gnome-mount](https://blueprints.launchpad.net/ubuntu/+spec/gnome-mount) - it will be (is already?) in Feisty Fawn (Ubuntu 7.04).

---

### Post by drs305 on 2007-02-08
Magnes, thank you for the link. It may help in Feisty but I can't make heads or tails of the link. I didn't see where I could install it in Edgy, and in truth, didn't completely understand what it would allow me to do if I could. But then, I'm just dense.

---

