---
title: "are there something like cpu-z"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2008-01-20
are there some commands or softwares like cpu-z in windows?

---

### Post by Prodromoi on 2008-01-20
In Add/Remove, search for "sysinfo".  This gives some basic information similar to CPU-Z.
Also, if you're using an Nvidia graphics card and the Nvidia driver, the nvidia-settings configuration app gives a bundle of GPU-related info too.

---

### Post by afeasfaerw23231233 on 2008-01-21
thanks. but it doesn't provide the information of fsb, ram frequency, latency.....mobo's chipsets... 
is that Moai Statue on the easter island?

---

### Post by erginemr on 2008-01-21
There is another diagnostics app: hardinfo, though I am not sure whether it will give you the information you desire to the same detail level. I also tried it, but was buggy and crashed on me a several times. Still worth a shot:

```
sudo aptitude install hardinfo
```

---

### Post by Golem XIV on 2008-01-21
You can try cpuid, it's in the repos (use apt-get or Synaptic).

---

### Post by afeasfaerw23231233 on 2008-03-14
> **erginemr said:**
> There is another diagnostics app: hardinfo, though I am not sure whether it will give you the information you desire to the same detail level. I also tried it, but was buggy and crashed on me a several times. Still worth a shot:

```
sudo aptitude install hardinfo
```

hardinfo CRASHES!

---

### Post by afeasfaerw23231233 on 2008-03-14
> **Golem XIV said:**
> You can try cpuid, it's in the repos (use apt-get or Synaptic).

it doesn't show the fsb, ram bandwidth, etc..

---

