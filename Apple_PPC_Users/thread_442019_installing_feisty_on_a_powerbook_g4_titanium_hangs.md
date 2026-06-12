---
title: "installing feisty on a powerbook g4 titanium hangs"
date: 2007-05-13
forum: Apple PPC Users
---

### Post by deeteesbeard on 2007-05-13
Hi,

It's my first post, I'm new to ubunto and have little experience (although some) of linux in general.
I have an old powerbook g4 titanium that I installed dapper on last night. I then found out that it was possible to download an image of fiesty for ppc.

So I'm trying to boot off the feisty cd (made with the "ubuntu-7.04-desktop-powerpc.iso" image).
It boots ok off the cd and gets to just beyond the ubuntu splash screen with the horizontal panning yellow bar, then as soon as the spalsh screen goes, the screen turns black for a few seconds, then white and I'm left with a mouse pointer (working), but nothing to click. The cd then spins down and the computer sits in this state.

Any ideas what may be going wrong?

Here are my thoughts..

The cd drive in said laptop is a bit ropey, only likes to read discs when the computer is cool, although I just tried an install after the compuer had been left cold for several hours with the same results.

I need to not be booting the "live" image off the cd? If so what should i be using?


And another question. If I have a working install of 6.06.1 dapper on the laptop can I update it to feisty without having to boot off the feisty cd?

Thanks to anyone who takes the time to read this and suggest stuff (probably rtfm ;) )

Doug.

---

### Post by ssam on 2007-05-13
sound is broken on the tibooks in feisty [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

when gnome tries to play the login sound it freezes.

[https://wiki.ubuntu.com/PowerPCFAQ#head-7a2153ba9422054e36f5854cb48feb8c95671b13](https://wiki.ubuntu.com/PowerPCFAQ#head-7a2153ba9422054e36f5854cb48feb8c95671b13) has the work around to get logged in. then you can disable the start up sound.

---

### Post by deeteesbeard on 2007-05-13
Thanks for that. I might try the earlier release then. :)

---

