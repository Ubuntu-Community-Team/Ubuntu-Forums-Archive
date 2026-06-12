---
title: "How do I enable SMP?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by slinga on 2006-01-11
Hey all, 

I've been using Linux (SuSE) for almost one year now. I decided to try out Kubuntu and see what the buzz was. It's snappy, but I'm having some serious issues. First of all I'm on a Dual Intel Xeon 64 Bit w/HT. How do I enable an SMP kernel? In SuSE you can install the kernel via yast same way as you would install an RPM. 

Here is output from uname -a:
Linux ubuntu 2.6.15-8-amd64-generic #1 Tue Dec 13 03:23:06 UTC 2005 x86_64 GNU/Linux

Thanks.

---

### Post by flight_master on 2006-01-11
Hello, and welcome! :D

What you need to do is download the SMP kernel. Open a console session, and type:

```

sudo synaptic

```
Search for 'smp', and install the proper 64bit kernel.

Regards,
Christian A. Herrnboeck

---

### Post by slinga on 2006-01-12
I actually tried that prior to posting this. There was a kernel called amd64-k8-smp which I tried which didn't work (I could boot the kernel but then I couldn't login because there was no keyboard support apparently). It makes sense as I'm on a Xeon, not AMD architecture. I ended up downloading the Ubuntu dvd and installing it from there. The kernel was there and everything worked.

Update uname -a output: Linux ubuntu 2.6.12-9-amd64-xeon #1 SMP Mon Oct 10 13:22:55 BST 2005 x86_64 GNU/Linux Everything's good now.

---

