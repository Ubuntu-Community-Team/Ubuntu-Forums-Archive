---
title: "NetBoot/PXE Boot IntelMac's"
date: 2009-05-06
forum: Apple Hardware Users
---

### Post by jbbjshlws on 2009-05-06
Hello All!,

I have a few questions, firstly i have setup a pc network (nfs pxeboot) boot for ubuntu, and i see that there should be no hassles me booting to IntelMac's with the same setup.

Firsly i would need to get around the issue with mac's not being able to PXE boot, my solution to this would be to boot them off of a cd for the mean time with a pxe rom for the network cards that are in mac's ([http://rom-o-matic.net](http://rom-o-matic.net)) they should then connect to the tftp pxe and dhcp handouts in the existing system. eventually you would setup the boot cd as a netboot image for the mac's where they would boot to a mac server with netboot running, then get passed to the linux server with the ubuntu image.

The alternative is to completely start from scratch and build up an image on a mac that is then dealt out with the mac server.

Any suggestions? not sure what way i should go, i would like to keep everything as clean and simple as possible, so one image would work better for this situation, has anybody done this before?

Cheers,
Joshua

---

### Post by jbbjshlws on 2009-05-09
Still no replies on this one, Bump!

---

