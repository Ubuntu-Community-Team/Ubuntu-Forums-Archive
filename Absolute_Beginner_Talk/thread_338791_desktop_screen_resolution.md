---
title: "desktop screen resolution"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by bubun on 2007-01-14
i have installed ubuntu 6.10; the default resolution is 640x480. I want to change it. the 'arrows' for changing the resolution are not working. how to change desktop resolution?:confused:

---

### Post by ardchoille42 on 2007-01-14
> **bubun said:**
> i have installed ubuntu 6.10; the default resolution is 640x480. I want to change it. the 'arrows' for changing the resolution are not working. how to change desktop resolution?:confused:

Open a terminal and do:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

That will take you through a text-based wizard which will allow you to reconfigure xorg for new resolutions. When that is done, restart xorg:

```

sudo /etc/init.d/gdm restart

```

Make sure you've closed all apps before you do this because it will restart your desktop.

---

### Post by bodhi.zazen on 2007-01-14
Depends on your video card and monitor.

Sometimes all you need is:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Otherwise see this thread: [http://www.ubuntuforums.org/showthread.php?&t=269052](http://www.ubuntuforums.org/showthread.php?&t=269052)

---

