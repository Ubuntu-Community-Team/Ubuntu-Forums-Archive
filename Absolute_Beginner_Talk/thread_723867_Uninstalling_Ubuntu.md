---
title: "Uninstalling Ubuntu"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by EnergySamus on 2008-03-13
Hi!

I want to uninstall Ubuntu from my laptop. It is a dual boot: Vista and Ubuntu 7.10. Don't worry... I still have ubuntu on a desktop PC, and I will still be using these forums!!! :lolflag:

1. How do I uninstall ubuntu?
2. How do I get rid of GRUB? 

I have 2 Ubuntu partitons... Do I just get rid of those?


EnergySamus

---

### Post by sandysandy on 2008-03-13
> **EnergySamus said:**
> Hi!

I want to uninstall Ubuntu from my laptop. It is a dual boot: Vista and Ubuntu 7.10. Don't worry... I still have ubuntu on a desktop PC, and I will still be using these forums!!! :lolflag:

1. How do I uninstall ubuntu?
2. How do I get rid of GRUB? 

I have 2 Ubuntu partitons... Do I just get rid of those?


EnergySamus


here is a link to uninstall ubuntu

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

regards

---

### Post by EnergySamus on 2008-03-14
thanks!!!:lolflag::lolflag::KS

---

### Post by EnergySamus on 2008-03-14
OK, to make sure that I am doing this right (using Sandy's Guide):

1.Install Easy BCD (I have Vista, so this is the best choice for me)
2. Choose "ReInstall Vista MBR", and let it work.
3. After it is done Delete the 2 Ubuntu partitions (Swap partition, and Main partition)
4. Reboot to see if it worked.

.... Is that it?

EnergySamus

---

### Post by ugm6hr on 2008-03-14
> **EnergySamus said:**
> .... Is that it?

Yes.

If you want to be sure it will be OK, just reboot after installing EasyBCD - it should have over-written GRUB.

Once confirmed, just delete the Linux partitions.

---

### Post by EnergySamus on 2008-03-14
> **ugm6hr said:**
> Yes.

If you want to be sure it will be OK, just reboot after installing EasyBCD - it should have over-written GRUB.

Once confirmed, just delete the Linux partitions.


Ok... Sorry that I am a little slow on this. :lolflag:

So what you are telling me is to install EasyBCD, reinstall the MBR, restart my PC, and if it automatically boots in to Windows: I did it right. And then delete the Swap/Main Ubuntu partitions.

Is it really that easy?!?! 

EnergySamus

---

### Post by ugm6hr on 2008-03-14
> **EnergySamus said:**
> Is it really that easy?!?! 

Yes.

Good luck :popcorn:

---

### Post by EnergySamus on 2008-03-14
Thanks!!!!!!
I will do it in the exact order that I said, and I will update in the afternoon!

Thank you guys!
EnergySamus

---

### Post by EnergySamus on 2008-03-14
It worked. Thanks!!! I am keeping the two Ubuntu partitions just in case I want to go back!

EnergySamus

---

### Post by Computer Guru on 2008-03-15
If you *do* choose to go back, it's as easy as using EasyBCD to add an Ubuntu entry once more :)

---

