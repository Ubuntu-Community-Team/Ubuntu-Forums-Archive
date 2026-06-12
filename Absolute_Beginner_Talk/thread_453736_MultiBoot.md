---
title: "MultiBoot"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by limapapa on 2007-05-24
I have a Dell 4600 with single 80G HD.
I had XP and Vista (Beta) set up to dual boot.I then installed Ubuntu 7.04...it's working great;however,during boot up I'm given the option of selecting Ubuntu or Vista. When I select Vista I'm then given the option of XP or Vista;Xp boots ok but if I select Vista I get an error msg and it won't boot.From what I've read Vista doesn't like Ubuntu resizing the partition.Since the Vista authorization expires the end of June I'd just as soon get rid of it now.
What I would like is advice on removing Vista without messing-up my Ubuntu/Xp dual boot.
Thank you in advance.

---

### Post by rsambuca on 2007-05-24
It is going to be a pain to do it.  Right now, the Vista bootloader is controlling your boot into XP and Vista, so basically the easiest thing to do would be:

1.  Reformat the Vista partition into whatever you want.
2.  Use your XP installation disk to boot into recovery mode and type in "fixmbr"
3.  Boot an ubuntu liveCD and reinstall grub to the mbr.

I am in the same boat right now with Vista RC2, but I haven't bothered to get rid of it yet because I have 3 Hard drives with ample space.

---

### Post by Happy_Man on 2007-05-24
Hmmm..... I would say delete the partition...... that shouldn't affect GRUB, but it may affect NTLDR.... on second thought, don't listen to me.

---

### Post by rsambuca on 2007-05-24
> **Happy_Man said:**
> Hmmm..... I would say delete the partition...... that shouldn't affect GRUB, but it may affect NTLDR.... on second thought, don't listen to me.

Deleting the partition won't work because the Vista loader will be lost, and hence there will be no way to get into XP.  I think I agree with your second thought on this one;)

---

### Post by Happy_Man on 2007-05-24
Yeah, I realized that as I was typing. :D

---

### Post by gn2 on 2007-05-24
> **rsambuca said:**
> Deleting the partition won't work because the Vista loader will be lost, and hence there will be no way to get into XP.  I think I agree with your second thought on this one;)

Surely if you delete the Vista partition and bootloader, an installation of Grub should detect XP and make it bootable without having to do a fixmbr first?

---

### Post by Happy_Man on 2007-05-24
Yeah, but I think first Windows has to be able to boot itself before GRUB can boot the Windows bootloader which boots Windows... hence fixmbr.

---

### Post by gn2 on 2007-05-25
Academic really, as a fixmbr only takes a few minutes.

---

