---
title: "compiling nvidia driver on macbook pro?"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by holr on 2007-10-30
hi,
  i have compiled a custom kernel successfully using vanilla 2.6.23 and applying the relevant mactel patches. I can boot into it fine on a macbook pro santa rosa with nvidia 8600) but cannot get the nvidia driver to install properly.

I disabled everything with nvidia in the .config kernel source file. When the gdm came up I ran /etc/init.d/gdm stop to stop the gui. I ran the latest downloaded nvidia installer from the command line (sudo sh NVIDIA.version.run) and it installed without error. Even ran the nvidia-xconfig too. When i reboot and go back into the new kernel, it keeps coming up with the new ubuntu gutsy monitor / gfx card selector, and when i go through that into gnome, I run nvidia-settings and it tells me the driver isnt installed! "nvidia" is the gfx card in xorg.conf though.

Should I be blacklisting something, or is there anything else im missing?

Thanks!

---

### Post by qhartman on 2007-11-12
I don't own an MBP, so I may be of little help doing specific debugging. However, a couple references that may help:

[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

Is the "official" central point of information running Gutsy on the newest MBP. it seems like the nvidia driver should "just work". However, you mentioned you compiled a custom kernel. Did you do it manually, or use a method that creates updated .deb files which you install like you would the official packages? If you did it by hand, you might want to try "the ubuntu way" which should allow the packages nvidia driver packages to work.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

HTH.

---

