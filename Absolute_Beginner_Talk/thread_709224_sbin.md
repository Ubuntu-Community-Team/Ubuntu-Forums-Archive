---
title: "/sbin"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by hmoralez on 2008-02-27
Hi,

I am a beginner to Ubuntu, feisty fawn. I had one question if anyone can help. Is it an appropriate appropriate location  to install Netscape in /sbin? Why/Why not

---

### Post by taurus on 2008-02-27
I personally would install it to /opt since /sbin is for some special system binaries.

---

### Post by chris.a.barker on 2008-02-27
It's generally a good rule of thumb to install addon software (ie not through Synaptic or Aptitude) within your home directory. This is good for a few reasons. 

1. Permissions will be correct for usage.
2. Ease of troubleshooting.
3. Easy to backup your information.

My 2 cents.

---

### Post by derbouka on 2008-02-27
No, because all files that you put in the "/sbin" directory will be in your PATH and only executable files should be there.
You should install it in "/opt" or home directory or install it from the repositorie.

If your starting on Ubuntu, watch [this Introducing presentation]("http://www.slideshare.net/anandvaidya/linux-introduction-commands") and on slide 16 they explain the "Linux Filesystem structure".

best regards

---

### Post by hmoralez on 2008-02-27
Thanks for all the comments on my post. Very helpful

---

