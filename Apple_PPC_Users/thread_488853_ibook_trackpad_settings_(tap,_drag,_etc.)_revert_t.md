---
title: "ibook trackpad settings (tap, drag, etc.) revert to original after reboot?"
date: 2007-06-30
forum: Apple PPC Users
---

### Post by TonySmash on 2007-06-30
when using the trackpad function through the terminal to enable clicking and dragging, it always reverts back to the original "notap" and "nodrag" settings after i reboot. so, every time i boot and want to use these trackpad functions, i have to go through the "sudo trackpad tap" and "sudo trackpad drag" commands. kind of a pain. any ideas why these keep going away upon reboot?

---

### Post by kugn on 2007-11-01
go to /etc/pbbuttonsd.conf, and change the 'notap' to 'drag'

---

