---
title: "Triple boot with Ubuntu"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by Drewkman on 2008-11-24
I've been scouring the web for ages to no avail...

I'm trying to set up my Santa Rosa 15" Macbook Pro for a triple boot with Leopard, Vista and Ubuntu. OS X and Vista are fine, no problems. But I'm too ignorant to install Ubuntu properly.

In the graphic install partitioning window, Ubuntu gives you some choices: install inside another partition on your hard drive, which it seems to pick at random, or basically wipe the whole thing. Or do a manual. I have iPartition and can set up the right partitions I wanted to use, and I suppose my whole problem would be solved someone would just tell me how to tell Ubuntu to install on a specific partition. I've been into the manual option, but suddenly you have to create the swap & EFI boot partitions, as well as specify the mount locations or something (?!?!). This is way beyond me.

I have used other people's methods by using Boot Camp Assistant to make a partition, then install Windows and split the partition in half to install Ubuntu. But when I do so I end up with an annoying and confusing screen when I try to boot Ubuntu (using rEFIt), asking if I want to boot Vista (Longhorn, whatever that is) or Ubuntu. I'd rather not have this. All I want is a computer with a hard drive clearly partitioned between the 3 OSes. No interfering between the, or anything... etc etc...

When I do have Ubuntu up and running, I'm also at a loss on what to do to connect it up to my wireless router. Why does it have to be so complicated? If a Nintendo DS or something can connect to a network with nothing but the security key, why can't a fully functioning Linux computer?

I like Ubuntu (or at least I think I will do; I haven't been able to do anything yet), and I do appreciate that it doesn't have the billion dollar funding that Apple and Microsoft, but I really think that certain aspects of it could be made more user-friendly for the less Linux-literate. :(

Thanks. Can anyone enlighten me?

---

### Post by cyberdork33 on 2008-11-24
> **Drewkman said:**
> I have used other people's methods by using Boot Camp Assistant to make a partition, then install Windows and split the partition in half to install Ubuntu. But when I do so I end up with an annoying and confusing screen when I try to boot Ubuntu (using rEFIt), asking if I want to boot Vista (Longhorn, whatever that is) or Ubuntu. I'd rather not have this. All I want is a computer with a hard drive clearly partitioned between the 3 OSes. No interfering between the, or anything... etc etc...

Let's take things one at a time. What you describe here is how you want to install. The only difference I would make is to make sure to install GRUB to the Ubuntu partition instead of the MBR. This is done on the last window of the installer in the "Advanced" button. Then whichever OS you choose in rEFIt will boot. (You will still have the GRUB screen. It is the Linux bootloader. Just choose the default or let it timeout and you will be in Ubuntu.

---

