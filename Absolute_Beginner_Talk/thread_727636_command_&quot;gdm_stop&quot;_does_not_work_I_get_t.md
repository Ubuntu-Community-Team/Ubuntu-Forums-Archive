---
title: "command: &quot;gdm stop&quot; does not work I get the following error:"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-18
I'm trying to stop the GDM so that I can install an NVIDIA driver and whenever I use the command

```
gdm stop
```

I get the following error:

gdm[5339]: WARNING: GDM file gdm-daemon-config.c: line 2121 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2121 (): Cannot run seteuid to 0: Operation not permitted

What the hell?! It worked perfectly fine before! Well, I do suppose that was another computer, but what gives?

---

### Post by Rocket2DMn on 2008-03-18
Try
```
sudo /etc/init.d/gdm stop
```

---

### Post by Neo0351 on 2008-03-18
I log in a virtual terminal as root and use
```
killall gdm
```
or
```
/etc/init.d/gdm stop
```

---

