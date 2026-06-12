---
title: "Need Some Feisty/Dapper Help"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by ItsJRFooZ on 2007-08-04
I use the VMware Player and when I try to open Feisty from the player I get a pop-up window that says

[I]"Not enough physical memory is available to power on this virtual machine.
If you were able to power on this virtual machine on this host computer in the past, try rebooting the host computer. Rebooting may allow you to use slightly more host memory to run virtual machines."[/I]

What should I do or buy to  help me run this?

And if this don't work can someone tell me whats the best thing to use. Beryl/Compiz? XGL? Im pretty much a noob if someone can direct me to a easy user friendly guide to get the best Manager for either Dapper or Edgy Eft because those are the only Ubuntu versions that want to work on my system.

_**My Computer Specs**_
2.26GHz Intel Pentium 4 Processor
512mb DDR SDRAM Memory
80GB Ultra DMA Hard Drive 
NVIDIA GeForce4 MX 420 Graphics Card

**Aim:** ItsJrFo0
***Any help will be greatly appreciated!***

---

### Post by benx009 on 2007-08-04
i'm assuming you are trying to run feisty in windows?  have you tried allocating more memory(RAM) to feisty?

---

### Post by Old Pink on 2007-08-04
No, he needs to allocate less RAM to Feisty, VMWare is complaining there isn't enough available on his system to assign it.

---

### Post by ItsJRFooZ on 2007-08-04
yes i am running on Windows XP Pro but im trying to get a taste of some 3D action lol im trying to use the VMware player but if there is a better/easier why please tell me. And how do i Allocate less RAM to Feisty? And if its to much of a struggle to get feisty i'll juss stick with either Dapper or Edgy those both work fine i juss want to find a easy way to get compiz fusion or one of those cool 3D managers i tried a couple times b4 but it crashes...

---

### Post by Old Pink on 2007-08-04
Chances are VMWare video capabilities won't be enough to/won't have the drivers to see Compiz running. Run ```
glxinfo | grep "direct"
``` in a terminal on Ubuntu to see if you can support direct rendering, first.

To allocate less RAM, change the virtual PC's settings, aim for around 256mb max in your case, maybe dropping to 192mb after install.

---

### Post by ItsJRFooZ on 2007-08-05
My output for glxinfo | grep "direct" in the terminal was..

Direct Rendering: No
OpenGL Rendering String: Mesa GLX Indirect 

sounds bad is ther anyway that i can turn this on? and I dropped allocated the memory to 192mb let me see if feisty works now.Ok feisty now works thanx now is there any wat i can turn on the Direct Rendering? And can someone find me a good guide to get compiz fusion or one of those 3D Managers for either feisty or dapper?

---

### Post by ItsJRFooZ on 2007-08-05
Bump.. help?

---

### Post by ItsJRFooZ on 2007-08-05
need some help here...

---

