---
title: "Ubuntu runs faster online than offline?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-06-12
Ubuntu runs faster online than offline for me! For example, if I click a shortcut to my home folder, it takes about 15 seconds to display when I'm offline. When I'm online, it's instant! 

I've tried stopping applications like gaim and checkgmail, but it still slow.

Not THAT much of an issue for me, but I'm pretty curious as to why!

---

### Post by muximus on 2007-06-12
now this is pretty curious..... could be bcoz of your networking components ... if anything. how do you connect to the internet/intranet?/

---

### Post by Stickymaddness on 2007-06-12
Connect using a dsl router...

Also, I don't have this problem with my laptop, it runs the same both online and offline

---

### Post by Motoxrdude on 2007-06-12
When offline, take a look at your running applications and see if there is a program using more CPU resources them normaly.

---

### Post by Najand on 2007-06-12
Maybe there are some processes trying to connect to the internet while there is no internet available. So they use some of your memory.

---

### Post by Stickymaddness on 2007-06-12
I'm pretty sure it is some application trying to go online, but the only process I could see that was out of the ordinary was checkgmail, which was using 96mb, I tried killing it, but it didn't make much of a difference....

---

### Post by tgalati4 on 2007-06-12
If you have a SAMBA file or printer share, then Linux will check to see if they are still available.  When you lose the network, several processes that use the network will slow down as they wait for a timeout response.  You can change these timeout settings and network persistancy settings and that should speed up your system when offline.  It would also mean that clicking on a network share folder may take longer bring up because it won't be refreshed as often.

Also, Linux and the kernel depend heavily on the network being up.  So if you boot without the networking modules (for a portable or embedded device) then it's not a problem but for a PC, Linux expects a network to be there and most apps use the network in some fashion.

Compare your process lists (ps -ef) between the slow computer and the normal one and see what the differences are.  It could be one process that's slowing your system down.  If you have CUPS set up for printers (as most systems will) then it uses the network and it could be searching for a printer that disappeared.

---

### Post by Stickymaddness on 2007-06-12
Ah, thank you! This is the information that I was looking for! I'll check, but I'm pretty sure that SAMBA's to blame! I suspected that Ubuntu relied on the network being up, just wanted to check that it wasn't anything foreign...

Thanks for help everyone! :)

---

