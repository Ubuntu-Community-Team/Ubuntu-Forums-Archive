---
title: "File Permissions recovery mode"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Tech_Analyst on 2007-04-03
I changed my etc/x11/xorg.conf file and lost my ability to boot. When I browse /ect in recovery mode I can see the x11 folder but it is listed in blue. Why is it blue and why can't I cd to it?

---

### Post by NeoLithium on 2007-04-03
Did you back up your xorg.conf file before you edited it?

---

### Post by Tech_Analyst on 2007-04-03
hehe, of course not.:(

---

### Post by NeoLithium on 2007-04-03
Well, depending on how much you remember about what you changed; you can always type:
```

nano -w /etc/X11/xorg.conf

```
 
If you boot into the computer without the recovery mode (Just into your computer with the CLI) ensure you do **sudo nano -w /etc/X11/xorg.conf**

---

### Post by Zuuswa on 2007-04-03
Try
```
sudo dpkg-reconfigure xserver-xorg
```

---

