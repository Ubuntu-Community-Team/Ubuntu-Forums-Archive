---
title: "XServer won't start"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-21
I just ran the updater to 7.10 and followed all the steps but now it won't fully boot up- says XServer is configured wrong and then I get stuck at this DOS prompt like thingy. How can I fix it please?

GeForce 2 ultra graphics card so it was using Legacy NVidia drivers - is this the problem?

---

### Post by marko_4454 on 2007-04-21
> **swey said:**
> I just ran the updater to 7.10 and followed all the steps but now it won't fully boot up- says XServer is configured wrong and then I get stuck at this DOS prompt like thingy. How can I fix it please?

GeForce 2 ultra graphics card so it was using Legacy NVidia drivers - is this the problem?

You can try this command:
```
sudo dpkg-reconfigure xserver-xorg
```

after that ...
```
startx
```

---

### Post by Cauda_Draconis on 2007-05-02
I screwed up on the xserver-xorg conifiguration, and now xserver won't start.
I have a GeForce 256, so I'm assuming it uses the Legacy drivers. Anyone know what I have to call it in xorg.conf, or know where I can find out? Cuz nvidia GeForce 256 isn't it.

---

