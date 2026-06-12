---
title: "&lt;SOLVED&gt; How to force Ubuntu on PowerMac to boot into shell"
date: 2017-02-10
forum: Apple Hardware Users
---

### Post by kaynemo2 on 2017-02-10
Don't know if this is useful, but it took me a while to figure it out. Thanks to user k1l from IRC channel. In order to force your machine (ubuntu, powerpc, yaboot) to boot to shell mode and not gui:

1. Enter in terminal:

```
sudo systemctl set-default multi-user.target
```

2. Reboot

Voila !

If you need to reverse this:

1. Enter in terminal:

```
sudo systemctl set-default graphical.target
```

2. Reboot.

Thanks k1l !!

---

