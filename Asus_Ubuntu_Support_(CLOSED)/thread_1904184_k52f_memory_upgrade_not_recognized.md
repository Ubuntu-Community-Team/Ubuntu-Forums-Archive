---
title: "k52f memory upgrade not recognized?"
date: 2012-01-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by match417 on 2012-01-04
I have an Asus k52f 32bit running 10.04 LTS and server 08. I just upgraded my RAM from 3gigs to 8gigs and it still shows that I only have 3 gigs installed. Server 08 recognizes the 8 gigs, but not ubuntu. Anyone have any idea why this is? It's not only seeing one stick of RAM because each stick is 4 gigs, plus server 08 sees the 8 gigs. Seems like its a software issue.

I've been thinking about switching over to Debian 6 because of some other issues with my headphone jack and laptop lid switch/hibernation mode not working properly. Maybe they would work in debian and it would see my 8 gigs of RAM, if not then Mandriva or Opensuse. I like the Ubuntu support though.

---

### Post by 2F4U on 2012-01-04
Is your installation 32 bit or 64 bit? 32 bit, per default, only recognizes up to 4 GB of RAM. Subtract some amount of RAM dedicated to I/O and shared graphics card and you end up with approximately 3 GB of remaining RAM. You can stick with 32 bit and still get your 8 GB recognized if you install a PAE kernel.

---

### Post by match417 on 2012-01-04
I'm running a 32 bit OS and the laptop is 32 bit.

I went into the 10.04 synaptic package manager and there are tons of pae kernels, I don't know which one to choose. I didn't see the pae kernel specifically for lucid, only for maveric, natty, and oneric. Those were at the very top of the list of packages. I upgraded to 10.10 and now neither of the three packages I mentioned above are listed, only the insanely long list of packages containing "pae". there is a list of backports, modules, images, input, media, net, compat, wireless, alsa, and lbm...then combinations of each one. Obviously I pick the one that is for my kernel, but what happens when I install updates and the kernel gets updated? The pae will be for my old kernel but the kernel will be newer.

---

