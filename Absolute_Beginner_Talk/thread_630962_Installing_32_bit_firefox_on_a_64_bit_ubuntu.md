---
title: "Installing 32 bit firefox on a 64 bit ubuntu"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-12-03
Hello all,

Been having all sorts of weird issues lately.  Two days ago, firefox stopped playing any and all embedded media.  I am running a 64 bit ubuntu install and had installed the downgraded version of firefox last year and got everything working a-ok.  I started using the 64 bit version and that has been buggy at best.  Won't work with java, doesn't play all media, and crashes anytime I open more than two windows.  Tried to re-install the 32 bit version using the directions found here:

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

But when I get to step # 5 I get the following:

```
brian@brian-desktop:~$ linux32: /usr/local/firefox32/firefox: Permission denied

[2]-  Exit 1                  firefox32
brian@brian-desktop:~$ 
```

I know when I did this last year I had a bugger of a time getting it to work then too.  Anybody have any suggestions?

Thanks!

-B

---

### Post by p_quarles on 2007-12-07
The "permission denied" message indicates to me that you may have skipped the step that comes directly before running step 5:
```
sudo chmod +x /usr/local/bin/firefox32
```
Is that a possibility?

If that's not it, I would recommend using Kilz's tutorial, which he keeps up-to-date:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

