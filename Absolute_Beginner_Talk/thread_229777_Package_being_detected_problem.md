---
title: "Package being detected problem"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Cath0de on 2006-08-04
I feel like an idiot right now. I'm trying to install ethereal, so I checked the ubuntu package lists, which lists ethereal, ethereal-common, and ethereal-dev as packages in the repositories. Yet when I apt-get install any of them, it can't find the packages.

I just can't comprehend why it isn't working.

---

### Post by benuski on 2006-08-04
Have you enabled the multiverse and universe repositories?

---

### Post by cantormath on 2006-08-04
> **Cath0de said:**
> I feel like an idiot right now. I'm trying to install ethereal, so I checked the ubuntu package lists, which lists ethereal, ethereal-common, and ethereal-dev as packages in the repositories. Yet when I apt-get install any of them, it can't find the packages.

I just can't comprehend why it isn't working.

open terminal
```
sudo apt-get update
```

```
apt-cache search ethereal
```

you should see
```
scapy - Packet generator/sniffer and network scanner/discovery
ethereal - network traffic analyzer
ethereal-common - network traffic analyser (common files)
```

then
sudo apt-get install ethereal ethereal-common

If that doesnt work you need to add the right repositories.

---

