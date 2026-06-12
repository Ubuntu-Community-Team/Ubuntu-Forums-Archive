---
title: "Windows on PPC Mac"
date: 2009-10-31
forum: Apple Hardware Users
---

### Post by candyiz4kidz on 2009-10-31
I've looked for and failed to find any Windows that will run on a PPC Mac, whether it be, 95, 98, NT 3.51 ,NT 4.0, 2000, XP... etc etc. I've even tried NT 4.0 which specifically says that it is PowerPC compatible on the CD. Of course the problem seems to be that the machine itself would need to be IBM compatible, which Apple computers are not.

So let me get to my point here....

I came across something called Qemu, a free and open source solution to run windows on a PPC Mac, much like vmware or virtualpc. I had this quite possibly retarded idea that maybe someone with a more programming/technical background can answer.

Instead of running an emulation layer, could we not just work Qemu's code into a windows/linux installation? Then THEORETICALLY we wouldn't have to use an emulation layer? Therefore running the system natively. The reason i really ask is, if the emulation is little more than a translation from PPC to x86, why can't we just take the Qemu source code and work it in to the appropriate windowslinux files/folders?  .... over looking of course the whole "legal" issue of re-engineering of windows code. Although it could be made a lot more simple, by only ADDING to the code which is 100% legal, as that is what windows applications do as they install. 

We were fortunate enough to have ubuntu hook up our PPC versions, but not every OS/Distro is so warm and cuddly. I just think it would be a great idea to be able to instead "emulate" run the operating system "natively".... Just a thought, any comments?

---

### Post by rjcalifornia on 2009-11-01
re-engineering windows code? Sounds possible, but that will be a violation of the EULA?

Anyways, I like your thoughts, and I have this crazy project on my head: xPUD. How about recompiling xPUD for the PowerPC Architecture? It is doable. It looks good and doesn't require a lot of resources.....


so?

---

