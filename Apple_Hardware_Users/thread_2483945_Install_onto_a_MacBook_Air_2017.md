---
title: "Install onto a MacBook Air 2017"
date: 2023-02-13
forum: Apple Hardware Users
---

### Post by makouser on 2023-02-13
I've been a Ubuntu user for well over 10 years on a variety of old PCs, and managed to scrape by searching for support here and elsewhere on the internet. But now I'm a bit confused.


I bought a MacBook Air 2017, 7.2 just because I thought I should, just for the fun! It has been an OK experience, but I'm done with the closed proprietary OS now that support has slipped back to just security fixes not major version updates. So I want to run Ubuntu.


I've done loads of digging and have found every potential config except the one I want. I don't want to dual boot. I don't want to run on some external SDD or SD card.


So what should my config look like?


I'm thinking I should end up with a small APFS with a tiny FAT partition for EFI (maybe just shrink the APFS and leave the existing EFI), and install Ubuntu into the empty space with an EXT4 partition or two (or three). Don't think I need ZFS do I?


Am I anywhere close?


If anyone can point me at a step by step dummy's guide I'd appreciate it.


Thanks

---

### Post by makouser on 2023-02-19
No takers? 

I have found a document that describes a straight forward install, overwriting the 'entire' disk which apart from sounding too easy, flies directly opposite to a number of others that have said that the apple boot manager will only boot from a EFI partition inside an APFS container. 

I suppose the worst I can do is totally trash it, but should be able to recreate a small APFS container from the recovery.

Any thoughts?

---

### Post by DuckHook on 2023-02-19
I have never worked with Apple gear so cannot help you. However, you can *bump* a thread every 12 hrs so that it surfaces from the bottom of the ocean mud. Best not to wait 6 days.

Good luck with that old Mac. I recently did a similar revamp to an old 2015 Dell XPS. Yours looks like an interesting project.

---

### Post by makouser on 2023-02-20
Thanks for the suggestion. Good idea.

---

### Post by 2blue on 2023-02-20
I have installed lubuntu on a 2017 macbook, but I simplified the process maybe a bit too much. I had a new ssd in at the time and let lubuntu take over the entire drive. I had to fiddle a bit with the UEFI to make it boot from USB but I can`t remember exactly what I did (I think I only altered the priority list of boot alternatives). It should be straight forward to partition the internal drive, but as mentioned I didn`t.  You probably have installed by now, but you could just simplify your choice in the Ubuntu installer, or maybe run the partition manager live. Any formatting of partitions could be done later on, and I think Ubuntu will automatically format to ext4 on it`s main partition.

---

### Post by makouser on 2023-02-21
Thanks for that. Sounds positive.

Now I'm going to ask a question that a) I don't really understand what I'm saying, and b) you may well not remember. Here goes!

Did ubuntu totally clear the whole drive - no APFS remained, and put the new UEFI into a fresh Fat32 partition?

Thanks again.

---

### Post by 2blue on 2023-02-21
I had to check on my "former" mac but the online recovery mode is there when I boot and  press CMD and R. I guess the UEFI is there too since it`s on a chip on the motherboard, not stored on the main storage drive. PCs (and non-PCs) are made to be saved, even if the entire storage drive is no longer working. In other words, it looks like it is similar to other computers in this regard.  I hope it answered at least part of your question. When I installed lubuntu, I had replaced the old drive, and there were nothing left of the original macos, yet the recovery mode is still there. So regardless of what you let Ubuntu take over, it does`t alter these basic features.

---

### Post by makouser on 2023-02-21
Thanks again. That's a very comprehensive reply which fills me with confidence that I "can't" really do any harm that I won't be able to roll back from.

Brilliant!

---

