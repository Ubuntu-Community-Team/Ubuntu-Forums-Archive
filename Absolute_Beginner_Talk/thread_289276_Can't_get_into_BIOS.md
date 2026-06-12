---
title: "Can't get into BIOS"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by gn2 on 2006-10-30
I have recently built an AM2 PC. Sadly I can't even get to install Ubuntu or run a live CD. The Ubuntu discs I have are definitely OK....

Caan't get any OS to run installer, Ubuntu, PCLinuxOS, Freespire, W2kPro, XPsp2

The difficulty I'm having is trying to get into the BIOS set-up.

I press "Del" key during boot, and "Entering Set-Up" appears at the bottom of the screen, but goes no further.

The Motherboard is an Asus M2NPV-MX with Award BIOS, which I have succesfully updated/flashed with the supplied utility CD, after some difficulty.

I have been getting 1-2 and 1-3 beep codes, which suggests display adapter RAM problems.

Since I don't have a PCI-e card fitted, the monitor is connected to the on-board graphics, NVIDIA 6150, which uses system memory.

The PC switches on and boots to an ASUS splash screen without any warning beep codes

I haven't been getting memory error beep codes unless I press re-set and hold down "Del" for the Bios Set-Up.

Does this mean my Elixir DDR2 RAM is incompatible?

I'm reluctant to pay out for different RAM if that isn't the problem.

Hopeful that someone can give me a definitive answer, I'm having a hell of a time with this PC, and it isn't even for me...
The first MoBo I had was D.O.A. and had to be returned to on-line retailer.

I've been trying to get this PC sorted for more than two weeks now and it's driving me mad! ](*,)

---

### Post by Charles Hand on 2006-10-30
Boy. That's a toughy. I wish I could be of more help. If it's complaining about the video card, how about investing in some kind of dirt-cheap video card that you can plug in just in order to access the bios?

I had an Asus MB computer where the onboard video died. I have an AGP card in there now. In fact, the computer-building geeks I hang around with used to be impressed by Asus but are now shying away from  Asus because of similar anecdotes of flakeyness.

---

### Post by CatKiller on 2006-10-30
You can test your memory with [memtest86]("http://www.memtest86.com/") if you can get the computer to boot a floppy. Without saying what memory you're using, it's difficult to ascertain whether it's going to work or not - not that I know that much about DDR.

You could also try taking out everything you can - leave in one stick of RAM, but take out any peripherals. You'll also want to reset the BIOS using the jumper on the motherboard after a flash. You've not actually said what the symptoms are other than you can't get into the BIOS. Does it POST?

Personally, I wouldn't have risked a flash with a suspect motherboard - especially if it was the memory that I suspected. A crash or interruption during the flashing process is pretty much unrecoverable, and random changes to the data on the way to the CMOS probably wouldn't be good, either.

Good luck.

---

### Post by gn2 on 2006-10-30
PC powers on and displays an ASUS splash screen.

RAM is 2 sticks of Elixir brand 256mb DDR2.

Screen displays message "Entering Set-up" when I press "Del" for entry to BIOS, but just hangs, and doesn't go to BIOS.

All components are new, and the SATA 2 hard drive has no data on it.

Will try a clear CMOS jumper, hadn't thought of that.....

---

### Post by CatKiller on 2006-10-30
> **gn2 said:**
> RAM is 2 sticks of Elixir brand 256mb DDR2.

Speed?

> Will try a clear CMOS jumper, hadn't thought of that.....

Let us know how you get on.

---

### Post by gn2 on 2006-10-31
Memory is 533mhz

Cleared with jumper, now get flashing cursor in top left of screen, and repeated persistent beeps when pressing "Del" to get into BIOS.

Have arraanged swap of RAM with understanding local shop tomorrow, hope that will cure it.

Should perhaps have got better RAM to start with, but was trying to save a few bob...

False economy methinks now....

---

### Post by CatKiller on 2006-10-31
And you're definitely only running it at 533? That's the lowest that motherboard will go.

It is possible that this board's broken too - I once had a replacement graphics card that was just as broken as the first (I've not used that retailer since). For some reason, it's fairly common to send refurbs as replacements for returned stuff.

Good luck, once more.

---

### Post by gn2 on 2006-11-01
> **CatKiller said:**
> And you're definitely only running it at 533? That's the lowest that motherboard will go.

It is possible that this board's broken too - I once had a replacement graphics card that was just as broken as the first (I've not used that retailer since). For some reason, it's fairly common to send refurbs as replacements for returned stuff.

Good luck, once more.

Not running it at any speed!

Have got RAM from local shop who assure me that it is definitely compatible with that board which they use in their own builds. ASUS M2NPV-MX

No go with MoBo number two. Can get in to BIOS, set up to suit, then try to re-boot to install OS and just get a blank screen.

Total and complete P.I.T.A! Have requested a refund from ebuyer, and will source an MSI or Gigabyte board locally. Anything but ASUS.....

---

### Post by CatKiller on 2006-11-01
Tch. Ah well. Better luck with a different brand, I hope.

---

### Post by gn2 on 2006-11-02
All sorted. Defective board No.2 RMA'd back to ebuyer, and replacement Asus board sourced from very helpful and informative shop, Everest-Tech Aberdeen. Plug Plug.

Having fun (not) installing all the bits and bobs required for a safe W2kPro system, and it's taking ages.

Support your local PC shop. Use it or lose it.

---

### Post by CatKiller on 2006-11-02
Hooray!

Good stuff.

---

