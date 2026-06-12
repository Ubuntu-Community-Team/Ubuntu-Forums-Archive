---
title: "No direct rendering after kernel upgrade"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-11-21
Hi.

I'm running Dapper on Celeron M.I've just upgraded from 2.6.15-23-386 to 2.6.15-26-686 kernel. I have linux-dri-modules for both kernel installed. When I clean boot Ubuntu, the kernel 386 uses about 180 of RAM while 686 only uses about 100 of RAM. I think 686 kernel has a performance boost. But when I tried to start compiz/beryl the GDM restarted. So I checked the 

```
glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

But I had dri-modules for the kernel installed. What did I miss?

---

### Post by kosmic on 2006-11-21
Is your Graphic Card Nvidia ? or ATI ?
Do you have the binary drivers installed ??

If it is an ATI card, do you have this line in xorg.conf :

```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

---

### Post by echo $USER on 2006-11-21
After compiling/installing a new kernel, you must reinstall the video drivers under the new kernel.

---

### Post by TheTux on 2006-11-21
Mine is Intel 915. I also had several versions of 386 kernel and direct rendering just works there. Only 686 kernel doesn't have. Is this the case with the kernel?

And another question : My video RAM is 128MB. Ho do I check this in Ubuntu?

---

### Post by TheTux on 2006-11-23
Anyone please..

---

### Post by TheTux on 2006-11-25
Ok. I've installed the 2.6.15-_**23**_-686 kernel and direct rendering works there even thought it is slower than the 386 kernel . I guess maybe the dri-modules for 2.6.15-_**26**_-686 is broken. If anyone having the same problem, please let me know. Thank you.

---

