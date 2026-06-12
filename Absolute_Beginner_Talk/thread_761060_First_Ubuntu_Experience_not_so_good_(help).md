---
title: "First Ubuntu Experience not so good (help)"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Utnubuster on 2008-04-20
Ubuntu worked fine yesterday (by the way I'm using Wubi with windows XP wubi-installer.org/). It booted up fine now when I try today I get: 

"Kernal panic - not syncing: vfs : unable to mount root fs on unknown - block (8,3)" 

I have no idea what this means, I could use some help. I'll reply when I get a chance. Thanks

---

### Post by Rocket2DMn on 2008-04-20
That means that the boot sequence does not know where to look for the operating system.  Wubi is not an officially supported method of install, so you should consider setting up a dual boot.  See here - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
It's not really as complicated as it looks.  Essentially you just defrag your windows partition, backup your data in case it screws up (but moreso in case YOU screw up), install Ubuntu from the LiveCD, and now you have you dual boot.
More here: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by amlucent23 on 2008-04-21
I agree.. Wubi is your problem. Also try this for instructions on dual booting [http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot]("http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot")

---

### Post by Paqman on 2008-04-21
> **Rocket2DMn said:**
> Wubi is not an officially supported method of install

Are you sure about that? It's included on the Hardy LiveCD. So if it's not official right now, it will be in a few days time.

---

### Post by Rocket2DMn on 2008-04-21
> **Paqman said:**
> Are you sure about that? It's included on the Hardy LiveCD. So if it's not official right now, it will be in a few days time.

Ah, it would seem that with Hardy it is now official.  Even Wikipedia now says that it was unofficial for Feisty and Gutsy, but is official for Hardy.
> Wubi was born as an independent project, as such 7.04 and 7.10 are unoffical releases. But since 8.04 the code has been merged within Ubuntu and since 8.04 alpha 5, Wubi can also be found in the Ubuntu Live CD [2] and has been included on the new Ubuntu 7.10 Gutsy Gibbon distribution.
- [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

---

### Post by Paqman on 2008-04-21
> **Rocket2DMn said:**
> Ah, it would seem that with Hardy it is now official.  Even Wikipedia now says that it was unofficial for Feisty and Gutsy, but is official for Hardy.

Indeed. I think a LOT of Windows converts will be installing through Wubi from now on, so we'd better get used to providing support for it. I must get around to trying it out myself, actually.

---

### Post by Utnubuster on 2008-04-21
> **amlucent23 said:**
> I agree.. Wubi is your problem. Also try this for instructions on dual booting [http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot]("http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot")

I acctually burnt a live cd a while ago but windows is eating my partition space. I could dual boot but my parents work on this computer (I might be able to back up and dual boot in the summer though. I guess it's Wubi. I dragged the 7.10 iso into wubi. So maybe I'll have more live with 8

---

### Post by ace007 on 2008-04-21
You could set it up so that the default boot is Windows, your parents would be none the wiser

---

### Post by Utnubuster on 2008-04-22
> **ace007 said:**
> You could set it up so that the default boot is Windows, your parents would be none the wiser

They don't know much about computers, so If I backed up and dual booted they would dislike that. I could try though. My next shot'll be Wubi in the new ubuntu 8.04.

Thanks for the help guys. Ubuntu forums are great:)

---

