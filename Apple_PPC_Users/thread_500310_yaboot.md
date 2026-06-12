---
title: "yaboot"
date: 2007-07-13
forum: Apple PPC Users
---

### Post by pbarthelemy on 2007-07-13
Hello,

I guess I did something stupid, I installed Ubuntu after a failed installation of Fedora...
The issue is that yaboot was installed by FC.
So when I select linux from the yaboot menu, it does not manage to boot ubuntu.

How can I find where yaboot is to correct its configuration ?
I've found doc on the internet about changing the yaboot configuration, but they assume a clean install. I am not sure it applies when the yaboot was not installed by the linux I'll run ybin from, for instance


TIA

p

---

### Post by pxwpxw on 2007-07-14
Hi,
Could you give more specific info on what you have there - ubuntu or other linux version (and/or other system) you have got installed, the computer, and what you are able to boot. If you completed an install there should have been some message about the yaboot installation and where it went. If you can find /etc/yaboot.conf and post the text that will be a good start.

---

### Post by pbarthelemy on 2007-07-14
This is kind of the root of my issue.
the fedora-then-ubuntu install left me without a clue as to where is yaboot...

FC is replaced by ubuntu on the linux partition.
yet at boot-time, I get the yaboot installed by my previous FC install.

How can I know which partition is booted from ?
How should I reconfigure yaboot from ubuntu, erasing the old yaboot...

--P

---

### Post by pxwpxw on 2007-07-14
Yes but what can you actually boot?

---

### Post by pbarthelemy on 2007-07-15
Hello,

Was I can actually boot, pressing 'alt' at start-up to select a boot partition.
anyway, I solved by issue by trial and errors.
I booted under ubuntu, and run ybin,  changing the partition numbers in yaboot.conf until it worked...
I spotted a couple of dead partitions  ( the fedora swap and boot ones, I guess) but I won't risk messing my xhole set-up eo reclaim a few GB....

thanks for helping
--p

---

