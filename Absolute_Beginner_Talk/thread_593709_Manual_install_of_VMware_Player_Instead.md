---
title: "Manual install of VMware Player Instead?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2007-10-27
Since VMware Player is disabled from being installed automagically in Ubuntu 7.10 from "Add/Remove Programs", is it still possible to download the player directly from their website for a manual install, or will that also not work in 7.10?

---

### Post by nelson.bolanos on 2007-10-27
Actually, the best way to install it is manually, you just install the build essential package with apt
> sudo apt-get install build-essential
And download the player from vmware.com,  when you install it it tells you there isn't a pre compiled kernel header for your kernel, and it creates the one it needs.

(at least that happened with the server version)

---

### Post by luckylucky on 2007-10-28
thanks Nelson!

---

