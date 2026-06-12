---
title: "Installation problems"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by gumbybacca on 2006-03-25
Installed Ubuntu on 20gb hd and had no problems with installation, went to 100% complete, but then instantly my monitor goes blank with colored lines.  I rebooted, splash screen comes up, everything says ok, then when going in gui screen does same thing.

Im guessing video driver problem?  I have a Nvidia 6600gt? ](*,)

---

### Post by trent dillman on 2006-03-25
Once you get to the garbled gui screen, press CTRL+ALT+F2, and you will see a "login:" prompt. Login. Then enter this command to stop your gui:

For Ubuntu:
```
sudo /etc/init.d/gdm stop
```
For Kubuntu:
```
sudo /etc/init.d/kdm stop
```

Then

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Finally,
For Ubuntu:
```
sudo /etc/init.d/gdm start
```
For Kubuntu:
```
sudo /etc/init.d/kdm start
```

---

### Post by gumbybacca on 2006-03-28
thanks ! appreciate the help.  I will try that this evening.  I tried using lynx to get the drivers and install them, but it kept telling me that there was a module problem

---

