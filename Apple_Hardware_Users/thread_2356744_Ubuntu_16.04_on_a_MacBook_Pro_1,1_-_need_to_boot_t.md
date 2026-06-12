---
title: "Ubuntu 16.04 on a MacBook Pro 1,1 - need to boot twice"
date: 2017-03-26
forum: Apple Hardware Users
---

### Post by goo20 on 2017-03-26
Hi everybody,
I have experiencing a strange problem with my good old MacBook Pro 1,1 (CoreDuo, 32bits) on which I have installed Ubuntu 16.04.

Every time I do a cold boot, the process goes normally through the rEFInd screen and then Grub, and then Ubuntu starts. But right before presenting the logon screen, the computer will simply restart on itself (and play the Apple chime). On this second boot; I can go through the same process again and then finally I'm be able to reach the Ubuntu logon screen.

I'm suspecting this has something to do with the amdgpu driver (my MacBook Pro has a built-in Radeon X1600 Mobility). I'm not familiar at all with Xorg settings tweaking, and I have no clue where to look.

I could not find any suspicious traces in the log files.

Appreciate your help !

Thank you.

---

