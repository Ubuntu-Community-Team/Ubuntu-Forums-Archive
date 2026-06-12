---
title: "What directory is the linux kernel source in?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by scratched on 2006-04-11
I'm installing a cisco vpn client on my laptop so I can connect to my school's VPN, and there is a prompt that asks:

```
Directory containing linux kernel source code []
```

I have no idea where that directory is. Could anyone tell me?

---

### Post by trent dillman on 2006-04-11
it should be /usr/src/linux

note that 'linux' will probably be a symlink to the real source directory...

---

### Post by gnu2tux on 2006-04-11
just a tip: make sure you have actually installed the kernel source via apt-get first, or else you won't have much in the /usr/src/linux folder!

Al.

---

### Post by az on 2006-04-11
[QUOTE=gnu2tux]just a tip: make sure you have actually installed the kernel source via apt-get first, or else you won't have much in the /usr/src/linux folder!

Al.[/QUOTE]

Actually, just install the linux-headers package for your kernel.   You want to compile an extra module for the running kernel, not recompile the kernel.

See what version of linux-image you have and install the corresponding linux-headers package and you are good to go.

---

