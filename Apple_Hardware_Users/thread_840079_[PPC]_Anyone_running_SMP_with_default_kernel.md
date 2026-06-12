---
title: "[PPC] Anyone running SMP with default kernel?"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by stream303 on 2008-06-25
I was reading the docs about supported PPC hardware with 8.04 LTS, and came across a note at the bottom that might be misleading or out of date, so I'd like to get some verification:

[https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html)

If you read the smp kernel notes at the bottom very quickly, one might be led to believe that you have to recompile the kernel to enable smp.

They reference the "standard kernel", but I don't believe we are running the standard kernel anymore - I think we are **all** running the smp kernel whether you actually have multiple processors or not, and therefore not have to do anything special to get real smp functional on those boxes with multi-processors.

Here is the output of uname -a on my single-processor G5 iMac which shows I am not running the "standard kernel":

```
Linux imac 2.6.24-19-powerpc64-smp #1 SMP Wed Jun 18 15:20:48 UTC 2008 ppc64 GNU/Linux
```

Can anyone who runs a real smp box verify that you did not have to do anything special to get smp?  Top, or especially Htop will show you in an instant how many processors are running.

I think this may be a holdover from the Debian docs, which has generated many of the same concerns, yet found that smp was actually supported out of the box on recent kernels.

---

### Post by stream303 on 2008-07-06
Well, it's confirmed that smp support has been available out-of-the-box for a few releases now without the installer having to do anything special.

Unfortunately the Canonical documentation, based on the Debian installer docs is wrong.  Both Ubuntu and Debian have supported smp right from the initial installation for a long time.

Which goes to show that when it comes to PPC, don't always rely on information that may be *years* out of date. :)

---

