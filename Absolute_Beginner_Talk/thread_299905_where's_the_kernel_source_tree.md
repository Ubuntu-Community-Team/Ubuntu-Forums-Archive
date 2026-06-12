---
title: "where's the kernel source tree?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-11-14
I'm working on installing nvidia drivers for my ubuntu install and so far I've had no problems installing all the dependencies it asks for, but now it said I was missing the kernel source tree for my current kernel. I don't know what packets I need for this. It also said that for instance, red hat needs the kernel-source and kernel-devel RPMs. My question is what packets do I need to download for this?

---

### Post by ciscosurfer on 2006-11-14
In Synaptic you can search for kernel-source or linux-source, depending on what you want.

---

### Post by cshake on 2006-11-17
How would I get the newest kernel source if I'm doing this to get X to start, so I don't have access to Synaptic from the command line?

---

### Post by Bachstelze on 2006-11-17
You don't need the full kernel sources, only the headers matching your current running kernel. To install them, do :

```
sudo apt-get install linux-headers-$(uname -r)
```

You'll also need *build-essential* to build the module so install it too if you haven't already.

---

### Post by cshake on 2006-11-17
Thanks, it works now. I didn't need to do build-essential, but the nvidia installer did throw warnings about xorg being installed from a package and not having the sdl or something.

---

### Post by Bachstelze on 2006-11-17
Yeah, same here but as long as it works, that's all I ask :D

---

