---
title: "Network doesn't stay working"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Ian Spence on 2006-03-19
I've tried everything to solve my problems before coming here, so please bear with me.

I had been having trouble getting my onboard nic installed, but this morning I finally found a few tutorials that became a working nic card.

I built the driver
I then did `sudo modprobe ipg`
Then I `sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0`
I go into System > Administration > Networking, and see my card.

I configure it, and once it finishes activating, my internet is working.

However, when I restart, the automatic time syncing fails, and it's as if the driver was never installed.  I need to repeat what I've described every time I start up ubuntu.

Does anyone know what I'm doing wrong?

---

### Post by fimbulvetr on 2006-03-19
Make sure "ipg" is in your /etc/modules file.

---

### Post by Ian Spence on 2006-03-19
I knew I had to be doing something stupid. Thank you very much.

---

