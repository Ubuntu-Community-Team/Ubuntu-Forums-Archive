---
title: "windows randomly change size to almost maximized"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by quickk on 2008-01-24
Hi!

   I don't know if I'm the only one with this problem, but I've noticed that my windows don't always remember their un-maximized size.  For example, I'll be using firefox with the firefox window maximized.  Then I click the unmaximize window button on the top right and instead of reverting back to the expected unmaximize size, it will stay in the maximized format (with the difference that I can manually reshape the window by clicking and dragging one of its borders).  I'll call this the pseudo-maximized state.

I've even seen windows spontaneously pseudo-maximize,  Just now, I had a gedit window opened, and it, for no apparent reason decided to suddenly fill my whole screen.  

I'm using ubuntu 7.10, but I've noticed this on previous versions also.

Any thoughts on how to fix this?

Thanks!

---

### Post by mattismyname on 2008-01-28
Probably has to do with some weaknesses in the X server running on the mac.  If it were me, I would run a vncserver on the linux box to "hold" all of the apps you want to run there and then just use a vncviewer to login to the linux machine from the mac.

---

