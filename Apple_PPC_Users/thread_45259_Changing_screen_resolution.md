---
title: "Changing screen resolution"
date: 2005-06-29
forum: Apple PPC Users
---

### Post by elpK12_lnx on 2005-06-29
Hi folks

After installing U* on a G3 tower, and trying to reset the resolution via Screen Resolution, I am in need of some assistance as to a way of configuring a P70 IBM monitor (!) - 800x400 just doesn't cut it...
Thanks

---

### Post by frodon on 2005-06-29
ok

Don't forget to post your xorg.conf file for screen resolution problems. Post it in this thread
```
gedit /etc/xorg.conf
```

If you want to reconfigure your xorg.cong :
```
sudo dpkg-reconfigure xserver-xorg
```

---

