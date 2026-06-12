---
title: "can I restore my system"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Azzozhsn.NET on 2006-06-02
Hellow, I tried to upgrade some softwre form dapper repository in my brazy system, then I reboot machine the X server does not start, just command line.
The question is how can I restore my system like last time works good.

thank you.

---

### Post by %hMa@?b&lt;C on 2006-06-02
your Xserver is broken.
```
sudo dpkg-reconfigure xserver-xorg
```
and then
```
startx
```
will reconfigure it

---

### Post by catlett on 2006-06-02
enter ```
startx
``` Hopefully this will get you into gnome again.
IF you get in change your repository list back. Then see if aptitude can clear up the problem ```
sudo aptitude upgrade
```

P.S. What happens when happens when you boot to "recovery mode". Does it boot. If it does you can at least reconfigure x so it wil start if the earlier startx didn't work. So if you get to a command line in recovery mode enter ```
sudo dpkg-reconfigure xserver-xorg
```

---

