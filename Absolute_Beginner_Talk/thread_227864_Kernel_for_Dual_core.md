---
title: "Kernel for Dual core"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by IDeus on 2006-08-02
Hi all, I am new to Linux. Over the last week I managed to get Ubuntu kernel 2.6.15-26-386 running with my wireless ipw3945 working.  Though my Wireless is working I get "unknown symbol ieee80211..." messages from dmesg.

When I was browsing around for a fix for this, which I haven't found yet, I read someone mentioning that they wanted to use the 686 kernel because they had a Centrino duo.  I currently have a Core Duo laptop with hopes upgrading to the Core Duo 2 when its available.

So my questions are 

1. Why might I be getting the dmeg unknown symbols

2. Should I be using a different kernel like 686

3. If yes to #2 can I just run an upgrade to 686 from my current kernel of 2.6.15-26-386?


Thank you

---

### Post by Perfect Storm on 2006-08-02
_The first question I can't answer (I have no wireless, so I'm a bit clueless when it comes to that area).

2. If you want take advantages of your dual-core then yes.

3. You automatically use the new kernel after a reboot if it works you can uninstall your previous kernel, to install:

```
sudo apt-get install linux-686-smp
```

---

### Post by ewl1217 on 2006-08-02
1.) I don't use a wireless network, so I can't help with that.

2.) You should use the 686 SMP kernel.

3.) Just use the following command at the terminal to install the new kernel: ```
sudo apt-get install linux-686-smp
``` Reboot and enjoy. Keep the 386 kernel just in case things go wrong. If it works, you can then uninstall the 386 kernel, but you may want to keep it just in case.

**EDIT:** I'm always late... the responses wre near-identical too...

---

### Post by IDeus on 2006-08-02
Originally I had an older subbuild installed, 2.6.15-23-386, and I upgraded.  I would like to keep my current  2.6.15-26-386 and the 686 build but I see no reason to keep the "23" build. How do i remove that? I know I can just remove it from grub so I do not see it but should I remove it?

---

### Post by Perfect Storm on 2006-08-02
In synaptic you can make a search on "386" and then remove it. But make sure first that 686-smp works as it should before removing the previous kernel.

---

### Post by cantormath on 2006-08-02
> **IDeus said:**
> Originally I had an older subbuild installed, 2.6.15-23-386, and I upgraded.  I would like to keep my current  2.6.15-26-386 and the 686 build but I see no reason to keep the "23" build. How do i remove that? I know I can just remove it from grub so I do not see it but should I remove it?

I believe you can do that by going into synaptic and searching for
2.6.15-23.

It will bring up the old kernel.  I believe you can uninstall it through synaptic by right clicking on the package and remove...then when you are done, apply.

---

### Post by IDeus on 2006-08-02
Thanks all!

---

