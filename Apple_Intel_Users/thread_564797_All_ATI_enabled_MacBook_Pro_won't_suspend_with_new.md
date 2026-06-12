---
title: "All ATI enabled MacBook Pro won't suspend with new kernel."
date: 2007-10-01
forum: Apple Intel Users
---

### Post by mcdull2k on 2007-10-01
I have another thread opened wants to figure out the reason of failing of suspend and hibernate but later on I found the reason and would like to draw attention of all MBP holder (those with ATI X1600).

It has been confirmed that the ATI driver breaks the new kernel >= 2.6.22-10 and the machine will not suspend properly.

see this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126214](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126214)
and this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653)
 
So, you can either switch back to older kernel or compile your own to fix this problem.

---

### Post by E Gardner on 2007-10-01
Hi, thanks for posting this. Do you have information about how one would compile a kernel to get suspend working on this kind of hardware (MBP w/ATI x1600)? Is this very difficult to do?

---

### Post by cyberdork33 on 2007-10-01
> **E Gardner said:**
> Hi, thanks for posting this. Do you have information about how one would compile a kernel to get suspend working on this kind of hardware (MBP w/ATI x1600)? Is this very difficult to do?
There is a link in the stickied FAQ. Just make sure you use the kernel source less than 2.6.22-10

---

### Post by mcdull2k on 2007-10-01
> **cyberdork33 said:**
> There is a link in the stickied FAQ. Just make sure you use the kernel source less than 2.6.22-10

For 2.6.22-9 or below, the generic kernel works just fine, you don't need to compile your own kernel.

According to this post.

Emanuel  wrote on 2007-09-03:  (permalink)
Had the same problems, custom compiled a kernel utilizing SLAB instead of SLUB , and can now suspend / resume fine again on a Thinkpad z61p with ATI x1600

BTW, I do not recommend to revert to SLAB. As someone found the system unstable after wake with this modification.

---

### Post by E Gardner on 2007-10-02
So, assuming that I figured out how to replace the default gutsy kernel with 2.6.22-9 (is there a version of this in the Ubuntu repositories, or would I have to get it from elsewhere?), could I still run Gutsy, or would I have to revert to 7.04?

I would love to be able to use a recent enough kernel to enable things like PowerTOP.

Last time I played around with changing from the default kernel (in 7.04), I screwed up my X server settings really badly and could not figure how to reconfigure them - apparently the fglrx driver I had was no longer compatible with the kernel I was using. Any suggestions on how to avoid this?

---

### Post by ronocdh on 2007-10-02
> **E Gardner said:**
> So, assuming that I figured out how to replace the default gutsy kernel with 2.6.22-9 (is there a version of this in the Ubuntu repositories, or would I have to get it from elsewhere?), could I still run Gutsy, or would I have to revert to 7.04?

I would love to be able to use a recent enough kernel to enable things like PowerTOP.

Last time I played around with changing from the default kernel (in 7.04), I screwed up my X server settings really badly and could not figure how to reconfigure them - apparently the fglrx driver I had was no longer compatible with the kernel I was using. Any suggestions on how to avoid this?
I believe PowerTOP runs an any 2.6.22 kernel, so .9 or .10 won't lose you support. I'm pleased someone posted about this issue, but I never did get suspend working reliably in Feisty, anyway. ;)

---

### Post by cyberdork33 on 2007-10-02
> **E Gardner said:**
> Last time I played around with changing from the default kernel (in 7.04), I screwed up my X server settings really badly and could not figure how to reconfigure them - apparently the fglrx driver I had was no longer compatible with the kernel I was using. Any suggestions on how to avoid this?You have to compile the fglrx module against the kernel you use it with. So you have to recompile it each time you change your kernel. (This is not an issue with the default ubuntu kernels as all the modules and kernels in the repos go together.)

---

### Post by WaySensei on 2007-12-28
What would be the disadvantages of switching to an older pre-2.6.22-10 kernel? I run Ubuntu on a first-gen Macbook Pro, and need suspend to RAM to work properly, but am wondering what features I would lose by switching kernels.

---

