---
title: "[SOLVED] Resuming an Rsync Transfer"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by azurepancake on 2008-04-12
I've recently bought a computer to use as a server for all my media. I have a good amount of media on my main computer that I wish to transfer over to it. So I read about Rsync and its fancy copy algorithms and decided to download it and give it a shot. 

Rsync works amazingly well at blazing speeds, but there is just one problem.. I am using a wireless network and its very common for the computers connected to the network to lose there connections - thus halting my transfers. 

I can't seem to find a way to resume my transfers after reconnecting the dropped computer. I'd imagine there has to be some way to resume. Perhaps using the daemon instead of direct SSH? If anyone can help me out here, I'd greatly appreciate it. Let me know if you need anymore information.

Thanks!

---

### Post by mattismyname on 2008-04-13
Should just work automatically next time you run rsync.  If it has transferred a file and that file has not changed on the source computer then rsync will not transfer it again.

---

### Post by azurepancake on 2008-04-14
Yep, that seems to do the trick. Thanks a lot.

And awesome avatar! Classical.

---

