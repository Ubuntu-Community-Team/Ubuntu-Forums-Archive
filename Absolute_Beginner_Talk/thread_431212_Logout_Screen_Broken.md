---
title: "Logout Screen Broken"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-05-02
I installed a pretty neat login screen from [http://www.gnome-look.org]("http://www.gnome-look.org"), the fingerprint one. I installed it correctly using the usplash program. i followed the directions and changed the resolution for the login (and logout) screens to 768. i got tired of this one and found a different one that required it be installed using usplash and i think i messed it up. the logins screen is the same but the logout screen doesn't work anymore. can someone help me please? i thank you in advance.

---

### Post by xopher on 2007-05-03
If nothing else helps, you can try switching back to the ubuntu one:

```
 sudo update-alternatives --config usplash-artwork.so
```

Select the original one..

Then do a:

```
sudo update-initramfs -u
```

---

