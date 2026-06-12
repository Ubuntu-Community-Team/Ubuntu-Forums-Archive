---
title: "Terminal wont open And Wireless Problems"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by wipeout140 on 2007-04-10
Hi, I recently installed latest daily (April 9th) with all updates and installed but it working perfectly but cant open the terminal it says starting terminal then closes. If you could help me that would be a great help. 

Wireless Sorted - but only at 11mb/s any reason why

Any ideas???
Thanks
Richard

---

### Post by dbbolton on 2007-04-10
are you using gnome, kde, etc ?

---

### Post by gmcle454 on 2007-04-11
I'm having the same problem. Using Gnome.

---

### Post by gmcle454 on 2007-04-11
I found this in another thread. It worked for me. Hope that helps.

add this to your xorg.conf
 #------------------------------------------
 Section "Extensions"
 Option "Composite" "false"
 EndSection
 #------------------------------------------

Here's the WORKAROUND for anyone looking for it
[https://launchpad.net/ubuntu/+source....17/+bug/58232]("https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232")

---

