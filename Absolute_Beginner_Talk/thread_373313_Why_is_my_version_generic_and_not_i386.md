---
title: "Why is my version generic and not i386?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by b0ng0 on 2007-03-01
I installed (k)ubuntu yesterday and after many updates restarted. In the GRUB boot menu I now have 2 different kernels of ubuntu, both are called "generic". My friend who also has kubuntu installed says he only has the option to boot a kernel with "i386" in it. Is there a difference between the two? Is generic worse than i386 and should I reinstall? Sorry for noobish questions, I know nothing of kernels. :popcorn: 

Thanks

---

### Post by mahy on 2007-03-01
You know nothing about kernels, we know nothing about your processor. :) How else can we advise you? Tell us something about your machine.

EDIT: Can you please specify your and your friend's version of Ubuntu? I've got the feeling it not the same number.

---

### Post by b0ng0 on 2007-03-01
Sorry forgot to post sys info :).

I am running 6.10 Edgy Eft (as is my friend), I have an AMD Athlon 64 3500+, but i'm running the i386 because I heard of some troubles with the 64 bit version. I might also add, I had previously installed ubuntu around xmas time and it also showed the kernel to be i386 (then my pc went weird so i've had to reinstall). I have multiverse repositries enabled as well.

Thanks

---

### Post by mahy on 2007-03-01
"generic" is for the newest Intel Pentium and Core processors. This is imho also applicable for AMD64 processors, if for whatever reason you chose not use proper AMD64 version.

"i386" is for older (legacy) CPUs by Intel. I wouldn't recommend it.

Tell your friend to fire up Synaptic and install the "generic" kernel version, warts and all, i.e. image, headers and possibly restricted-modules. Provided he's also got a processor applicable for 'generic' kernel!

---

### Post by b0ng0 on 2007-03-01
Ahh, ok that clears things up immensely. 

Just on a side note, would you recommend the 64bit version if it can be used? The only reason i'm using the i386 is because I read on a forum post that it's less stable and things like flash don't work properly :confused: .

---

### Post by picpak on 2007-03-01
He's saying that the generic kernel can work with both 32 and 64-bit.

---

### Post by b0ng0 on 2007-03-01
But don't I need to install the 64bit version of ubuntu to get the benefits of 64bit? I'm a little confused here - does the i386 version of ubuntu do the same thing as the 64bit version if you have a 64bit processor or do you need the 64bit version of ubuntu to get proper 64bit architecture?

---

### Post by picpak on 2007-03-01
i386 is made ONLY for 32bit architecture.
generic can install and run on both architectures, hence its name.

The point of the generic kernel is to avoid confusion between i386, i686, etc. So just install it, reboot into it, and forget about it.

---

### Post by b0ng0 on 2007-03-01
Install 64 or 386? :) 

Thank you for your patience

---

### Post by anaconda on 2007-03-01
well.. actually (32bit) generic is 32 bit. and ofcourse it works with 64-bit processors too, but then they are running 32-bit os in 64-bit processor. Which is what I do. 

I did try the 64-bit ubuntu, but had some problems.. so I moved back to 32-bit. Didn't notice any difference in speed, but have heard that running 64-bit os in 64-bit processor could be 10-14% faster with AMD with intel the difference is smaller..

The "generic" meand that support for many processor types has been combined to one single kernel. So you dont have to install -smp- kernel for dual core processors and dont have to install -k7- kernel for AMD and so on.. Same kernel for all.

I recommend the 32-bit generic kernel..

---

### Post by mahy on 2007-03-01
> **b0ng0 said:**
> Install 64 or 386? :) 

Thank you for your patience

If i were you, i'd install the AMD64 version of Ubuntu. Meaning an entirely separate CD. It probably IS somewhat less stable, but that's the way it is...

---

### Post by bravemosquito on 2007-03-04
First of all sorry for my thread-attack :mrgreen: 

I have almost the same, but opposite problem. After playing 15mins with Synaptic I installed 2.6.17-11-generic kernel, but after reboot only 2.6.17-11-i386 is able to boot in Xorg. Generic only boots in terminal, torturin' it with envy script (first removed old configuration files/driver, w/o restricted modules) for an hour-two there's still no positive result

---

