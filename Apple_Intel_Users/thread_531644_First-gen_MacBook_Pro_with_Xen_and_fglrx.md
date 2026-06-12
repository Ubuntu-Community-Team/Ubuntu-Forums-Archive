---
title: "First-gen MacBook Pro with Xen and fglrx"
date: 2007-08-21
forum: Apple Intel Users
---

### Post by NCommander on 2007-08-21
Hey all,

I recently installed Xubuntu on my MacBook Pro, with the idea of using Xen. After two days of tinkering, and trying to use the 2.6.19 Xen kernel with pretty much everything breaking. After more fiddling around, I got almost everything working with the 2.6.22 kernel from Gutsy (sound, Xen, etc.). The one problem is fglrx (which is missing in linux-restricted-modules-xen) - without it, the system doesn't properly suspend or hiberate (the 2.6.22 kernel with fglrx works properly in this regard).

I attempted to manually roll my own build of this driver, but the ATi kernel driver causes make to get stuck in a constant loop, and forking about 2000 copies of make (which promptly causes a system crash). My objective here is to either build the fglrx driver by hand, or otherwise getting sleep/hibernate work. I've seen similar issues in this forum, but no one using the Xen kernel. Any help would be most welcome

---

