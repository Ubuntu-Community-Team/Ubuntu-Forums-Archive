---
title: "Picasa has works or i have to reinstall XP grrr"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-02-08
I have a machine with ubuntu 7.10 i have just installed picasa and get the following errors

/dev/nvidia() or /dev/nvidiactl are not accessable. Picasa will crash
if these files are not accessable.
To fix this, as root, please run:
chmod 666 /dev/nvidia() /dev/nvidiactl
and then restart this program.

My friend doesn't have a nvidia card, i can change the permission but after a reboot this goes back the previous setting! THIS MUST NOT HAPPEN! otherwise i will have 2 go back to XP
chmod 666 /dev/nvidia
chmod 666 /dev/nvidiactl

Does anyone got this message, or have a clue to resolve this problem ?

---

### Post by ibizatunes on 2008-02-08
What is the name for the video group in sys > admin > users & groups > manage

---

### Post by spiderbatdad on 2008-02-08
editted

---

### Post by ibizatunes on 2008-02-08
Solved
If anyone has the issue of the above the fix is
Go to system > admin > users & groups > manage groups > add group > type "video" 
> add user to the group > log out and log back in

Solved

---

