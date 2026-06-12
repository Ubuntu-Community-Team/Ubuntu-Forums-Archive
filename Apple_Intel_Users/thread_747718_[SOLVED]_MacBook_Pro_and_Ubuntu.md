---
title: "[SOLVED] MacBook Pro and Ubuntu"
date: 2008-04-06
forum: Apple Intel Users
---

### Post by wcbardwell on 2008-04-06
I'm considering purchasing a new macbook pro from the apple website in the next couple of months. The deciding factor on whether I get it or not is whether or not ubuntu runs well on the macbook pros. Could anyone give me the rundown on how well ubuntu runs on these machines... does everything work or will I have to sacrifice something? Thanks.

---

### Post by cyberdork33 on 2008-04-06
> **wcbardwell said:**
> I'm considering purchasing a new macbook pro from the apple website in the next couple of months. The deciding factor on whether I get it or not is whether or not ubuntu runs well on the macbook pros. Could anyone give me the rundown on how well ubuntu runs on these machines... does everything work or will I have to sacrifice something? Thanks.
This pretty much says it all:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

Differences on the very latest Macbook Pros (MacbookPro4,1) include the WiFi card (works with ndiswrapper and the XP driver on your restore DVD only) and the touchpad needs some software work to be fully functional, but that is in process: [http://tannewt.org/touch/](http://tannewt.org/touch/)

---

### Post by wcbardwell on 2008-04-06
Thanks a lot... really a big help.

---

### Post by eitan on 2008-04-07
i am writing this reply on a macbook pro 4,1.
yeah it's true the wifi card has changed and now you have to use 
ndiswrapper.  so you can get it to work.

my main issue is no support for the fn key.
the usb id for the internal keyboard has changed.
the linux kernel doesn't reflect this change.
so for now i'm making do without a key for pgup/pgdown/home/end/delete
which is most annoying.

i could compile a custom kernel.  but i have to figure out how
to include the restricted modules in the compilation (so the nvidia
driver is enabled) and so far
have not found a good step-by-step guide for this.

i posted a bug about this on launchpad, along with the fix.  but it 
hasn't even been sorted or assigned to anyone and my hopes are
really low that it will get fixed any time soon.

so if you can live without an fn key, go for it.

/ eitan

---

