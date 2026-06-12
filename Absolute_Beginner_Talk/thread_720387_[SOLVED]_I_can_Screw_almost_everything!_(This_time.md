---
title: "[SOLVED] I can Screw almost everything! (This time its Kubuntu GUI)"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-10
Hi,

This started when I restarted the xserver from the login screen menu. The screen went completely blank (not Command prompt). I hard booted and then got into the recovery mode and typed this:
```

sudo /etc/init.d/kdm stop 
sudo /etc/init.d/kdm start

```
It again went to the same black screen with nothing on it.

I got this code by searching this forum. I am a n00b...

Anything else I can do before going for a reinstall ?

Thanks

---

### Post by MaximusTG on 2008-03-10
Boot in recovery mode, and type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I think there's something wrong with your xorg.conf.

---

### Post by taurus on 2008-03-10
> **MaximusTG said:**
> Boot in recovery mode, and type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I think there's something wrong with your xorg.conf.

If you are in the recovery mode, no need to put sudo in front since you are technically logged in as root.

---

### Post by hyper_ch on 2008-03-10
and you start the gui then with

```

startx

```

---

### Post by Google Spider on 2008-03-10
Thanks. You guys rock!

---

