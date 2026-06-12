---
title: "whats &quot;better&quot; right now, the current linux kernel or the snow leopard one?"
date: 2011-01-08
forum: Apple Hardware Users
---

### Post by JuicyCouture on 2011-01-08
i think its XNU "darwin" that the macs use correct?

is there even a way to determine which is better?

i mean obviously the linux kernel gets updated more often so that would lead me to believe - and the fact they're both based roughly on the same unix architecture.

also, who is it thats doing the linux kernel updating? when we see all the distros getting the linux kernel update to 2.56 or whatever across all of them - whos doing that? is it Linus??
:confused:

---

### Post by JuicyCouture on 2011-01-08
also, is the kernel used in ubuntu the same one they use in the servers?

so if i plugged a thousand CPU's into ubuntu it would know what to do with them?

---

### Post by moreati on 2011-01-09
Neither is best, both are best. There isn't a universal measure of 'bestness', just fitness for a particular task or a score against a particular benchmark. 

The people who update the kernel are various programmers around the world who run tests, design and write patches. Linus over sees this with help of 'lieutenants'. Work is discussed and coordinated on The Linux Kernel Mailing List [https://lkml.org/](https://lkml.org/), there's more information at the Kernel Newbies site [http://kernelnewbies.org/](http://kernelnewbies.org/).

In answer to your last question Ubuntu does provide a customized kernel for running on a server. The desktop kernel is provided in linux-image-generic, the server kernel is in linux-image-server. Both are compiled from the same source code, but each is optimized for different work loads. I couldn't find information on the exact limits for an Ubuntu kernel. There differences are documented here [https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html#intro-kernel-diffs](https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html#intro-kernel-diffs)

Regards, Alex

---

### Post by JuicyCouture on 2011-01-09
so Linus makes no money from linux?

sucks

---

### Post by digitalchemystery on 2011-01-09
> **JuicyCouture said:**
> so Linus makes no money from linux?

It is somehow worth his time to be involved; the karmic value alone practically guarantees some form of benefit. It is likely that he has received donations or job offers as a result of his work, so, while ostensibly free, it is still possible to make money.

> **JuicyCouture said:**
> sucks

:D

Send him some money.

---

### Post by digitalchemystery on 2011-01-09
> **JuicyCouture said:**
> also, is the kernel used in ubuntu the same one they use in the servers?

It's possible that they both start life as the same kernel (some version of the Linux kernel), though it's likely that the Ubuntu maintainers maintain patches (shared and/or different) for what ultimately becomes the Ubuntu server and desktop kernels.

> **JuicyCouture said:**
> so if i plugged a thousand CPU's into ubuntu it would know what to do with them?

It would depend upon how you "plugged [in]" your thousand CPUs. A 10x10x10 arrangement would fit all on one machine, so as long as there's driver support for whatever your arrangement is, then, sure, it'll know what to do. If they're nodes in a cluster, then there are probably cloud management frameworks available, though you could always fall back on a scripting language.

Sounds like a nice machine.

---

### Post by digitalchemystery on 2011-01-09
> **JuicyCouture said:**
> i think its XNU "darwin" that the macs use correct?

This turned into something of a tricky question to answer. XNU (another _NU self-referential pun), a fusion of FreeBSD parts and Mach (a microkernel from Cargnegie Mellon), was developed as part of the NeXTSTEP project. NeXT eventually morphed into what is now OS X. There's quite a rich history here of failures and breakthroughs in operating system and kernel design.

> **JuicyCouture said:**
> is there even a way to determine which is better?

Yes and no. It depends upon how you're defining better or what you establish as "the right way" to do something. It depends upon what you want to do.

> **JuicyCouture said:**
> i mean obviously the linux kernel gets updated more often so that would lead me to believe - and the fact they're both based roughly on the same unix architecture.

The world of an application developer or an end-user is different from the world of a power-user or low-level developer.  

> **JuicyCouture said:**
> also, who is it thats doing the linux kernel updating? when we see all the distros getting the linux kernel update to 2.56 or whatever across all of them - whos doing that? is it Linus??:confused:

Distros are separately maintained and independent of Linux kernel development (though they're interrelated in that bugs discovered or features added in distros can find their way to the Linux kernel), so it's very unlikely to ever see *all* of the distros on the same page. With care and luck, however, it should be possible to upgrade one's kernel to a version new than that officially supported by the distro... it's even possible (though some relinking and recompiling will likely be necessary) to start with a base distro and use a completely different kernel... like Mach.

---

### Post by logandzwon on 2011-01-10
The Kernel in OS X is a ton better... for OS X..

The Linux kernel is a ton better... for Ubuntu.

not to nit-pick but OS X is UNIX, Ubuntu/Linux is unix-like.

---

### Post by logandzwon on 2011-01-10
> **JuicyCouture said:**
> also, is the kernel used in ubuntu the same one they use in the servers?

so if i plugged a thousand CPU's into ubuntu it would know what to do with them?

This question kind of hurts my head... all my Ubuntu machines run an Linux kernel, made by Ubuntu.  All my RedHat machines run a Linux kernel, made by RedHat.  My OS X servers, desktops, notebooks, iPhone, iPad, and iPod Touch devices run a kernel based on the same code.  The non-iOS devices which are all on the release (10.6.5) run almost the exact same kernel.

---

### Post by JuicyCouture on 2011-01-10
> **logandzwon said:**
> This question kind of hurts my head... all my Ubuntu machines run an Linux kernel, made by Ubuntu.  All my RedHat machines run a Linux kernel, made by RedHat.  My OS X servers, desktops, notebooks, iPhone, iPad, and iPod Touch devices run a kernel based on the same code.  The non-iOS devices which are all on the release (10.6.5) run almost the exact same kernel.


see this is what i was asking in another thread

the ubuntu linux kernel is different from the arch linux one etc.?

the other guy was saying the kernel was made by a group of guys overseen by linus

i didnt think distro devs worked on the linux kernel

"Distros are separately maintained and independent of Linux kernel development (though they're interrelated in that bugs discovered or features added in distros can find their way to the Linux kernel), so it's very unlikely to ever see *all* of the distros on the same page."

---

### Post by JuicyCouture on 2011-01-10
> **logandzwon said:**
> The Kernel in OS X is a ton better... for OS X..

The Linux kernel is a ton better... for Ubuntu.

not to nit-pick but OS X is UNIX, Ubuntu/Linux is unix-like.

is the windows NT kernel better....for windows?

---

