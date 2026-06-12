---
title: "Display resolution."
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by Umbra on 2005-07-12
Where do i change the display resolution in KDE?

I reintall ubuntu and now it never ask me for the monitor settings. I went to the Control Center but the setting only allows me to change up to 1024*768 as maximum, my monitor supports higher i was on 1280*1024 before resintaling.

---

### Post by frodon on 2005-07-12
you need to edit you xorg.conf file and add HorizSync and VertRefresh parameter as the specification of your screen. After a xsersver restart you will be able to select higher resolution.
I give you 2 thread links about editing xorg.conf :
 [http://www.ubuntuforums.org/showthread.php?t=45908](http://www.ubuntuforums.org/showthread.php?t=45908)
[http://www.ubuntuforums.org/showthread.php?t=46317](http://www.ubuntuforums.org/showthread.php?t=46317)
For any kind of problems post here your xorg.conf file : ```
sudo kedit /etc/X11/xorg.conf
```
If you're really newbie to linux open a terminal and type  ```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Umbra on 2005-07-12
Thx a lot. It worked.  O:)

---

