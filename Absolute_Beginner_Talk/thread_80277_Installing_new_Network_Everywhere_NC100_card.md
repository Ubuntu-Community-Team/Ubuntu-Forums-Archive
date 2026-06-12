---
title: "Installing new Network Everywhere NC100 card"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by nighttime on 2005-10-21
I just bought a Linksys NC100 NIC but I can't get it to work.

I already tried 

```
sudo modprobe tulip
```

But it doesn't seem to work completely... When I try

```
lsmod | grep tulip
```

I get

```
tulip      46112    0
```

Wich is allright, but on reboot I try to ```
lsmod | grep tulip
```again and it doesn't appear in lsmod. I have the noapic option activated (I'm not sure if that's relevant at all :P), and that's all I know -_-

Any help please?

---

