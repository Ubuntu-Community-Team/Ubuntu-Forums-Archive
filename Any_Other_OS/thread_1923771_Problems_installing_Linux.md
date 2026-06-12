---
title: "Problems installing Linux"
date: 2012-02-11
forum: Any Other OS
---

### Post by nef131 on 2012-02-11
I have built a new computer - mostly new, that is. The parts are as follows:

Motherboard: ASUS P8Z68-VLX
CPU: Intel I5 2500K
Hard disk drive: Western Digital WD3200BEVE (which is a SATA type drive)
DVD drive: LG
Memory: Patriot Division 2 VIPER XTREME DDR3 PC3-15000 1866MHz 2x4GB
Video Card: EVGA GTX550Ti

The motherboard has UEFI instead of a traditional BIOS.

The Hard drive originated in a Dell laptop - Inspiron 15R N5010, which I bought in the Summer but which was unfortunately, other than the hard drive, destroyed. It was duel booted, Windows 7 and Mint 11.

Windows 7 works normally in the newly created desktop computer (without requiring a new installation) including being able to install the drivers for the new motherboard and graphics card. Mint 11, already on the computer will not boot at all - not even up to the logon screen. It stops during the initial phase. I tried booting into a live dvd of Pinguy 11.04, Fedora 15 and Mint 12, which would stop near the beginning, after noting what devices it had found.  I also tried with the same Pinguy using Unetbootin, with the same result.

I would very much like to boot into my existing Mint or, barring that, re-install any Linux OS. What should I do? Could there be a problem with my hardware? I note that after all else failed, I tried to remove Grub so that booting into Windows would be easy (since I cannot see my Linux partition in order to edit GRUB to change the boot ordering list; however, the Windows 7 install disk would not allow me to enter the repair program, so I am concerned that I would be unable, if anything happened to Windows - which, to be honest, I do not use but it is better than nothing at the moment -, I would not be able to install any operating system. Hence, my concern may be about the hardware. I am not sure.

---

### Post by Perfect Storm on 2012-02-11
Moved to Other OS/Distro Talk.

---

### Post by wolfen69 on 2012-02-11
I believe you may have to turn off UEFI in the BIOS.

---

### Post by nef131 on 2012-02-12
> I believe you may have to turn off UEFI in the BIOS.

Thanks for the suggestion. Why would UEFI need to be turned off? And, how do you turn off UEFI?

---

### Post by wolfen69 on 2012-02-12
EUFI is there to protect the computer from being messed with. On *my* laptop, I just went into the bios and disabled it. It's probably under the security section, but you'll have to look for it.

---

### Post by nef131 on 2012-02-13
Thanks.

---

