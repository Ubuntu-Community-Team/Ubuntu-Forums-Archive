---
title: "glibc"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by effigies on 2005-07-10
Hi, I'm a programmer. I've just moved from Arch because it has some wierd directory placements and navigating takes an inordinate amount of time. Someone suggested Ubuntu as being stable and pretty standard, so I'm trying it. I'm liking it in general.

However, I'm having a bit of a problem. Where is glibc? I've uncommented all of the (appropriate) lines in /etc/apt/sources.list, and have run ```
sudo apt-get update
``` but I still can't find glibc.

Needless to say, this makes compiling rather difficult. (I would have thought it'd be a dependency of gcc, but apparently not.)

Any help?

Thanks,
Chris

---

### Post by Williams477 on 2005-07-10
Got to the Synaptic Package Manager under System>Administration and go to Settings>Repositories. Add all of them and try again using the Package Manager.

---

### Post by effigies on 2005-07-10
Sorry for the trouble. I found the headers I needed in libc6-dev.

---

