---
title: "booting help ( 2 computers 1 ubuntu )"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by skyzthalimit on 2007-11-07
I`ve looked this up but couldn`t find a suitable answer.. here is my problem..

I have 2 hdd`s on hd0 is windows on hd1 is ubuntu they both boot fine using Grub, but recently I need to take my linux hdd with me, and use it on another computer that has only windows on it. How can i make this possible? I want both of the computers to boot windows without the ubuntu hdd on, and when I put the ubuntu hdd to use it without problems? cand i do this without removing grub? and if I have to remove grub how do I do it?

---

### Post by oilchangeguy on 2007-11-07
> **skyzthalimit said:**
> I`ve looked this up but couldn`t find a suitable answer.. here is my problem..

I have 2 hdd`s on hd0 is windows on hd1 is ubuntu they both boot fine using Grub, but recently I need to take my linux hdd with me, and use it on another computer that has only windows on it. How can i make this possible? I want both of the computers to boot windows without the ubuntu hdd on, and when I put the ubuntu hdd to use it without problems? cand i do this without removing grub? and if I have to remove grub how do I do it?

are you needing to use windows on this other computer? if not either take out, or unplug the drive. because if you don't ubuntu will overwrite the windows master boot record, with grub.

---

### Post by skyzthalimit on 2007-11-07
I want the windows on both computers to work.. and when I need ubuntu to plug the hdd in on either of the computers and use it, then remove the hdd, and windows to still work..

---

