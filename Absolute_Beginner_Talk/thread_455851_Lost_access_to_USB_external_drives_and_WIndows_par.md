---
title: "Lost access to USB external drives and WIndows partition after Linux header update.."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by MistahPat on 2007-05-27
Yesterday after boot up I received 3 updates totaling approx 30MB. All I can remember is something about Linux headers. After the update I immediately noticed I lost access to everything attached via USB, which at the moment is primarily external drives. Also, I have lost access to my Windows partition. 

I'm a n00b just getting my feet wet with Linux and don't know the first place to start troubleshooting and would appreciate any guidance.

I'm running Edgy Eft on a Dell Inspiron XPS.

---

### Post by throntax on 2007-05-27
hmm sounds annoying! looks like maybe the headers don't have support for your windows filesystem? do you happen to know what partition it is on? ie. /dev/hda1 or some such device file?

We need to know which sense your windows hard drive is inaccessible.. like can it still be read or is it only un-mounted, or has the new headers done something to the support for its filesystem type... 

Does any other USB stuff work?

---

### Post by MistahPat on 2007-05-27
> **throntax said:**
> hmm sounds annoying! looks like maybe the headers don't have support for your windows filesystem? do you happen to know what partition it is on? ie. /dev/hda1 or some such device file?

We need to know which sense your windows hard drive is inaccessible.. like can it still be read or is it only un-mounted, or has the new headers done something to the support for its filesystem type... 

Does any other USB stuff work?

Windows partition is hda1. Had an "hda1" icon on desktop, but that went away. Had a shortcut on desktop to "My Documents" on Windows partition, and now that has an emblem of an "X". I have a Sandisk multi-card reader attached which used to light up when the laptop powered up.

**STRANGE. As I was writing this, I booted to Windows then booted back to Ubuntu. Seems doing that brought back Windows access and USB support. I had rebooted after the install, but not booted to Windows until just now. I don't understand this, but am happy now. Keeping my fingers crossed.

Thank you.

---

### Post by throntax on 2007-05-27
mysterious, but good! :)

---

