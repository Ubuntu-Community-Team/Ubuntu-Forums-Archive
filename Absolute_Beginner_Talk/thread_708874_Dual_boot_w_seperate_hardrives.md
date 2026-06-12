---
title: "Dual boot w/ seperate hardrives?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-26
So I gotz me a hardrive with windows and another hardrive with ubuntu on it. (They are both installed through the same computer)

So far if I want to switch between the two I have to physically switch out the hardrives.

Can I hook them into the same computer at once thought and just choose which one I want to boot when needed?

How can I tell if my computer can support more than one hardrives? (I have an Emachines T1090)
and how would I cofigure the hardrives? Would they both be masters on Seperate IDE cables?

Thanks for any help you can give me.

---

### Post by glennric on 2008-02-26
> **Xarok said:**
> 
Can I hook them into the same computer at once thought and just choose which one I want to boot when needed?
Yes.  Just install grub to the one that your bios selects to boot from.  Usually the primary on the first ide port.

> 
How can I tell if my computer can support more than one hardrives? (I have an Emachines T1090)
and how would I cofigure the hardrives? Would they both be masters on Seperate IDE cables?

Thanks for any help you can give me.
Most likely your computer supports more than one drive.  It doesn't matter how you configure them.  If you have two ide cables that would be easiest.  If not then put them both on the same cable.

---

### Post by shadowbw on 2008-02-26
If grub is installed on the drive that you installed Ubuntu (which it should have installed by default), then you should be able to use that as your master drive and your windows as your slave drive and grub should recoginize the windows partition.  I've never experienced that myself, but I think that it should still work.

---

### Post by glennric on 2008-02-26
Since you didn't have windows installed when you installed ubuntu you are probably going to have to modify your grub configuration to be able to boot to windows.

---

### Post by Xarok on 2008-02-26
> **glennric said:**
> Since you didn't have windows installed when you installed ubuntu you are probably going to have to modify your grub configuration to be able to boot to windows.

I will re-install anyways when 8.04 comes out...
If I have the primary HHD hooked up for the Ununtu installation along with the Windows HDD slave, will new installion CD be able to detect and set up what I want?

---

### Post by shadowbw on 2008-02-26
yes it will

---

### Post by Xarok on 2008-02-26
Well I both hooked um in right now, ubuntu as master, and windows as slave, and I could just select either for boot from the BIOS

sweet,

thanks guys

---

