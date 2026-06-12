---
title: "kernel source - how to get it"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by mathsjunky on 2007-01-16
Hello - new to Ubuntu, but I've been using SuSE for a long while. I'm looking for kernel sources for 2.6.17-10-generic. I've tried searches and google. I've got a vanilla install (mostly) but I've no real idea how the package manager works yet. 

Can anyone point me in the right direction please :)

Thanks
Paul.

---

### Post by taurus on 2007-01-16
[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/)

---

### Post by igknighted on 2007-01-16
You can get the kernel sources from kernel.org, or i believe from the command line you could type:
```
sudo aptitude install linux-sources
```

upon more thought, you might need a more specific file, so try this first:
```
aptitude search linux
```

you will need to enable some repositories in order to this first, I believe.  See this website for more details on that:  [www.psychocats.net](www.psychocats.net)

---

### Post by mathsjunky on 2007-01-16
Wow - that was quick thanks guys.
I really need 2.6.17-10-generic as I need the source that matches the edgy kernel.
I can't seem to find that - I can find the linux-image for this release, but I assume that's the binary.
Any idea what repository I need? Synaptic is totally new to me, as of he last couple of hours :)

---

### Post by igknighted on 2007-01-16
hmm, I'm acutally in SUSE now, but some time tonight I'll try to switch to Ubuntu and check it out for you

---

### Post by hal10000 on 2007-01-16
you don't need additional repositories to add the kernel source, just [COLOR="Red"]sudo aptitude install linux-source[/COLOR]

---

