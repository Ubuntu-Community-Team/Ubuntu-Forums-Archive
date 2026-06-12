---
title: "Direct Rendering Problem"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-12-09
Ok So this is what has happened, I have just done a fresh install an got everything working. I wanted to install a game ET so I was following a how to and like the fist step is to check Direct Rendering so that is what I did and I got this: 

paulvolk@LinuxPC:~$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

So I thought that was weird and decided to try glxgears and got this: 

paulvolk@LinuxPC:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x4b
drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)
paulvolk@LinuxPC:~$ 

I have looked around and this seems to be a common problem with ATI video cards. Considering I have the radeon 9250. I just can't find how to fix it. Is it possible to fix it and if so could someone point me to a HowTo or tell me how I could?

Thanks for the help.

---

### Post by kane77 on 2006-12-09
have you tried this: [http://doc.gwos.org/index.php/Install_ATI_driver]("http://doc.gwos.org/index.php/Install_ATI_driver")??


Unfortunately I have nVidia so I can't tell you if that worked for me... Hope it works for you

---

### Post by mrv on 2006-12-16
> **kane77 said:**
> have you tried this: [http://doc.gwos.org/index.php/Install_ATI_driver]("http://doc.gwos.org/index.php/Install_ATI_driver")??


Unfortunately that's a closed source ATI driver that does not support his card anymore.

As for the problem itself, it is fixed in Kernel 2.6.19, but that is only currently available in the Ubuntu 7.04 (feisty) development branch.

So the problem is/was known, and is fixed now, but not in Ubuntu 6.10, alas.

---

