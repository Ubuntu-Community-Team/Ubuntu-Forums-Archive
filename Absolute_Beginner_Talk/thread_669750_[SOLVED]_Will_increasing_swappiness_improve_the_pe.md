---
title: "[SOLVED] Will increasing swappiness improve the performance of an old, slow desktop?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by tomsa on 2008-01-16
Hello all,

    I am currently running Ubuntu 7.10 on an old box with an Athlon 800Mhz Proc. and 384 Mb. of RAM.  Honestly, in general, I am very pleased with my Linux experience.  I am planning on building a new computer, but cannot until I am done with an aggressive debt repayment plan a few months off.  Long story short- I've got an old slow computer that does everything I need it to ('cept pretty eye candy like compiz or beryl), and most of the things I want it to do, it's just slow and I'm stuck with it for a while longer.  So my question is: if I increase the swappiness setting, will I get any improvement in performance?  If so, how do I change that setting?  And what are the drawbacks (if any) to doing this?  I currently have a 1 Gb swap partition, and my box is only using about 83 Mb of it with 5 or 6 apps. open and running.  I'd love to see if doing this would give me a small performance boost (or more, but I doubt it will do much) without wrecking my computer.  Thanks for your help!

---

### Post by philinux on 2008-01-16
The answer is no. The settings are fine and the system will sort itself out.

Gutsy is running fine on my old machine by the way. I plan on getting an upgrade base unit soon.

It should be running really well on yours.

---

### Post by glotz on 2008-01-16
You can try it yourself, see [https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e](https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e)

I don't think there are drawbacks, some setting will be faster than others.

I read somewhere that having multiple swap partitions (on different physical disks) with the same priority setting would help the swap performance. Haven't tried it myself. Besides fooling around with swap issues, I suggest you kill any unneeded services (raid, bluetooth, etc) and perhaps try a lighter window manager.

---

### Post by celticbhoy on 2008-01-16
Increasing your physical memory would probably be the only way to get a performance boost.

---

### Post by HermanAB on 2008-01-16
With more RAM and Xubuntu, it will zoom like a new PC.

---

### Post by tomsa on 2008-01-17
> The answer is no. The settings are fine and the system will sort itself out.


That's pretty much what  I figured- I suppose it never hurts to ask, no?

> It should be running really well on yours.

It actually does run really well!  I have no real complaints, beyond a lack of eye candy- My Rage/Fury xpert pro 128 video card just won't do any, as far as I know.  I really don't see why I should necessarily try and gum up an old box with that stuff anyway.  I appreciate your input though!  I think I'm definitely a linux convert at this point!

---

### Post by tomsa on 2008-01-18
> **HermanAB said:**
> With more RAM and Xubuntu, it will zoom like a new PC.

I'm going to give xfce a try this weekend I think.  All I need to do is search for it in synaptic, right?  Adding more physical RAM is probably going to be a waste of my money- have you seen how much PC133 RAM costs now?  Ouch.  I'll wait.  But, from what I've read, xfce's efficiency may help a bit- maybe not zooming like a new PC, but fast enough to tide me over until July or so.  Thanks!

---

