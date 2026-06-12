---
title: "Zimbra Desktop Install"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by mora2828 on 2008-04-20
I just downloaded Zimbra Desktop and I need to learn how to install it.  It will not automatically install with Synaptic Manager.  I can I install this application?  The download file is named "zdesktop_0_84_build_1119_linux_i686_sh".  I am thinking that you can go into the "terminal window" and install it from them, but I have not been successful.  Any help would be very much appreciated.

Thanks

---

### Post by joshrobinson on 2008-04-20
> **mora2828 said:**
> I just downloaded Zimbra Desktop and I need to learn how to install it.  It will not automatically install with Synaptic Manager.  I can I install this application?  The download file is named "zdesktop_0_84_build_1119_linux_i686_sh".  I am thinking that you can go into the "terminal window" and install it from them, but I have not been successful.  Any help would be very much appreciated.

Thanks


is it on your desktop?
```
cd Desktop
```
```
chmod +x zdesktop_0_84_build_1119_linux_i686.sh
```
```
sudo ./zdesktop_0_84_build_1119_linux_i686.sh
```
if the last command does nothing try
```
sudo sh zdesktop_0_84_build_1119_linux_i686.sh
```

---

### Post by mora2828 on 2008-04-20
Great ... it worked .. now it is installed in root.  How do I get to launch the application.

---

