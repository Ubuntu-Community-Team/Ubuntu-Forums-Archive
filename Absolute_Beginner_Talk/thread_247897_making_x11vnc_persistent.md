---
title: "making x11vnc persistent?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by shimrah on 2006-08-31
Hi,

I'm pretty new to Ubuntu (and Linux in general), so you'll have to speak slowly...

I've tried using TightVNC and the Remote Desktop client in Ubuntu; for some reason, neither of them lets me see what is happening inside terminal windows.

Then I tried x11vnc, and it worked great! The only problem is that when I disconnect, the service stops! Is there a way to run x11vnc so that it persists or re-launches when I disconnect?

Many thanks in advance! :D

---

### Post by cquick01 on 2006-11-21
Try using the switch -forever. This should keep x11vnc running. Additionally, use -bg to make it run in the background.

---

