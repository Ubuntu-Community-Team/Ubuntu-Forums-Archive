---
title: "A question on Linux &quot;updates&quot;"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-28
It seems my ATI Radeon 9200SE video card is working fine. I think I start having trouble with it when I install all of those Linux updates. Does anyone know which file it may be that updates this card's video drivers? I would like to "uncheck " it befoe downloading the rest of the update files.
Thanks for any help.
kh

---

### Post by Henry Rayker on 2007-03-28
It may very well be the kernel updates...do you get a new listing on the GRUB menu at boot after these updates?

---

### Post by jem7v on 2007-03-28
I know that NVidia drivers break whenever you install a new kernel or new restricted modules, but all it means is you have to reinstall them.  Maybe there's a similar issue with the ATI cards?

---

### Post by kanha on 2007-03-28
yes reinstall newest driver
i had same problem some time back,reinstalling worked

---

### Post by macogw on 2007-03-28
If you're using drivers that are in linux-restricted-modules and there's a kernel update but l-r-m isn't in yet, they'll break.  If you're using drivers that you had to install separately, they install directly to the kernel and need to be installed on each new kernel.  Every time you get an update that says linux-image-generic or something like that, you'll need to reinstall.

---

### Post by kittyhawk63 on 2007-03-28
> **Henry Rayker said:**
> It may very well be the kernel updates...do you get a new listing on the GRUB menu at boot after these updates?

What do you mean, Do I get a new listing on GRUB? What would I be looking for?

Edit: I reread your thread and it makes sense now. Thank you and to everyone else that had reported in.
kh

---

### Post by kittyhawk63 on 2007-03-28
> **macogw said:**
> If you're using drivers that are in linux-restricted-modules and there's a kernel update but l-r-m isn't in yet, they'll break.  If you're using drivers that you had to install separately, they install directly to the kernel and need to be installed on each new kernel.  Every time you get an update that says linux-image-generic or something like that, you'll need to reinstall.

What do you mean by l-r-m isn't in yet?

---

### Post by kittyhawk63 on 2007-03-28
I'm using the driver that was installed when I installed Ubuntu. I have not installed any drivers myself.
I was installing the Linux-restricted-modules. That is where I think I was having my problems. I did uncomment restricted-modules in apt. I think that is the way that is said.

---

