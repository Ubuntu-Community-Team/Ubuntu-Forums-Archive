---
title: "Installing kernel headers"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by JeffBlouin on 2005-06-08
Hi,

         Im trying to installl DC++ for linux on ubuntu 5.04 and it said in a another message that I have to install the kernel headers...  I dont know the ones i need to install from synaptic?

Im running ubuntu on a AMD athlon 700 with the i386 package (I thing) any way to check that?

Thanks

---

### Post by daveisadork on 2005-06-08
[QUOTE=JeffBlouin]Hi,

         Im trying to installl DC++ for linux on ubuntu 5.04 and it said in a another message that I have to install the kernel headers...  I dont know the ones i need to install from synaptic?

Im running ubuntu on a AMD athlon 700 with the i386 package (I thing) any way to check that?

Thanks[/QUOTE]
You'll need to open up Synaptic and figure out which kernel image you're running, the version number and architecture, and then install the matching kernel headers package. For example, if you've got linux-image-2.6.10-5-386 installed, then you need to get linux-headers-2.6.10-5-386. If you're going to be trying to build kernel modules, there's going to be some other stuff that you need to do after installing the package.

---

### Post by JeffBlouin on 2005-06-08
Thanks,

                but where do i look to know the linux image that is install on my computer...
Im a real beginner!

Thanks

---

### Post by daveisadork on 2005-06-09
[QUOTE=JeffBlouin]Thanks,

                but where do i look to know the linux image that is install on my computer...
Im a real beginner!

Thanks[/QUOTE]

Go to System > Administration > Synaptic and search for linux-image. The one that's installed will be marked.

---

### Post by chileverde on 2005-06-10
[QUOTE=JeffBlouin]Thanks,

                but where do i look to know the linux image that is install on my computer...
Im a real beginner!

Thanks[/QUOTE]

or open a gnome-terminal and type:

> uname -a

---

