---
title: "openoffice.org upgrade error"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2008-02-18
I was upgrading and using openoffice at the same time when this happened
```
E: ttf-opensymbol: subprocess post-installation script returned error exit status 49
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured


```

How can I fix it?

---

### Post by smartboyathome on 2008-02-18
Try reinstalling OpenOffice if you can.

---

### Post by tdrusk on 2008-02-18
> **smartboyathome said:**
> Try reinstalling OpenOffice if you can.

I tried to completely remove it and I got another error. (now it says that metapackage is removed but there are still the openoffice programs...

---

### Post by smartboyathome on 2008-02-18
Removing the metapackage won't remove the other pieces. You have to remove every package.

---

### Post by FuturePilot on 2008-02-18
Try reinstalling the ttf-opensymbol. It looks like something went wrong with that and since all those other parts of Open Office depend on ttf-opnsymbol they failed to install since ttf-opensymbol bombed out.

---

### Post by tdrusk on 2008-02-19
1 more problem.

It now looks like crap. The theme doesn't match my Ubuntu Human theme. What should I do?

---

### Post by hw00d on 2008-02-19
I'm having the same problem.

Earlier today I installed some updates and then something went wrong with openoffice.  I get the exact same error as OP.  Any idea on how to fix?  I've tried reinstalling all packages related to openoffice in synaptic, i've tried synaptic > edit > fix broken packages, I've also tried removing/reinstalling through the terminal with no luck.

Thanks in advance for the help.

---

### Post by tdrusk on 2008-02-19
> **hw00d said:**
> I'm having the same problem.

Earlier today I installed some updates and then something went wrong with openoffice.  I get the exact same error as OP.  Any idea on how to fix?  I've tried reinstalling all packages related to openoffice in synaptic, i've tried synaptic > edit > fix broken packages, I've also tried removing/reinstalling through the terminal with no luck.

Thanks in advance for the help.

sudo apt-get autoremove --purge openoffice.org

I still have the openoffice looks like crap problem.

---

### Post by marriedman on 2008-02-26
I don't know if you figured this out, but I just found the fix to this. In Synaptic, search for " openoffice.org-gtk " no quotes of course. This will have OOo drawn with native gtk widgets.:)

---

### Post by tdrusk on 2008-02-27
> **marriedman said:**
> I don't know if you figured this out, but I just found the fix to this. In Synaptic, search for " openoffice.org-gtk " no quotes of course. This will have OOo drawn with native gtk widgets.:)

That's what I thought, but it stunned me that Ubuntu didn't install it when I installed OOo

---

