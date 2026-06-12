---
title: "No x aftering changing file for ati driver"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by rfurman24 on 2007-06-06
I was trying to change some settings in the ?etc/X11/xorg.conf for the ati drivers and rebooted with no x. I had made a backup before the changes. I boot in with the live cd and copied the original back and rebooted still nothing. I booted back into live cd and did the rebuild command in the xorg.conf file and still nothing. Any suggestions?

---

### Post by Ek0nomik on 2007-06-06
Can you boot into a command prompt?  (No X, just a terminal basically)

If so, try backing it up that way.

```
sudo cp */etc/X11.xorg.conf.whatever.the.backup.is.called* /etc/X11/xorg.conf
```

Or you can run this command at the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rfurman24 on 2007-06-07
After numerous attempts I finally was able to get the command to work to get x back. Now I just have to retry to get a driver installed that will work with Beryl. Thanks for the reply.

---

