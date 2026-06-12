---
title: "Nvidia drivers"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-19
I do not know how to install Nvidia drivers in Ubuntu Feisty. I've looked at Envy, but the only release that supports Feisty is unstable, and I'd rather play it safe.

 How can I install Nvidia drivers in Feisty?

---

### Post by eyelessfade on 2007-04-19
apt-get install nvidia-glx

but you should find out what kind of nvidia card you have first, since there is three nvidia-glx packages.

nvidia-glx-legacy, nvidia-glx and nvidia-glx-new
This problem is with nvidia since they don't support old cards on the newest releases.

---

### Post by kpkeerthi on 2007-04-19
```
sudo aptitude install nvidia-glx nvidia-kernel-common
```

---

### Post by Awperator on 2007-04-19
> **ZeroWing said:**
> I do not know how to install Nvidia drivers in Ubuntu Feisty. I've looked at Envy, but the only release that supports Feisty is unstable, and I'd rather play it safe.

 How can I install Nvidia drivers in Feisty?

I have an 8800gts and enabling the restricted driver didnt work. It actually crashed X for me. Use this method, it worked fine:

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

---

