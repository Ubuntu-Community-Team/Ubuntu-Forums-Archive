---
title: "How to search &amp; remove files..."
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-02
I think (sorry, poor memory) I installed vmplayer via packet manager and then later installed it with automatix (dumb thing to do I know).

I went to install vmserver (following another thread) when trying to install it came up with another version installed. So I went to both packet manager and automatix and removed vmplayer. 

Went back to terminal to install, it's still detecting some files so I can't install server :( 

How can I search for these files and remove?

---

### Post by lamego on 2006-12-02
I am not 100% sure, please check.

Vmware products keep their files at:
/etc/vmware

---

### Post by linuxbun on 2006-12-02
Yes thats there. How do I remove it without logging out?

I've tried sudo rm -d vmware (in /etc) but it always comes back withrm: cannot remove `vmware': Is a directory

Strange, cus that cmd worked in fedora :/

---

