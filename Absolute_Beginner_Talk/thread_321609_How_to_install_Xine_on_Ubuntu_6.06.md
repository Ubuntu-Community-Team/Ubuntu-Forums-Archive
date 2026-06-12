---
title: "How to install Xine on Ubuntu 6.06"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-12-19
I am having a hell lot of trouble installing Xine on Ubuntu 6.06.

First the xine-lib installation cribbed for zlib. I installed zlib and then I could install xine-lib properly.

But now when I try to install xine-ui, it doesn't go through. It stops in the middle and cribs for xine-lib. But that is already installed. Then why does it crib? It says I need to set the LD_LIBRARY_PATH variable properly. I tried that too, but doesn't work.

Can anyone tell me exactly what should I set LD_LIBRARY_PATH to?

---

### Post by Bachstelze on 2006-12-19
Xine is just an engine, which can be embedded in numerous frontends. If you're using GNOME, you can use Totem as a frontend for Xine. Just install *totem-xine*.

---

### Post by smith.norton on 2006-12-19
> **HymnToLife said:**
> Xine is just an engine, which can be embedded in numerous frontends. If you're using GNOME, you can use Totem as a frontend for Xine. Just install *totem-xine*.

But totem is already present in my Ubuntu by default. Do I still need to install totem-xine? Where can I get totem-xine?

---

### Post by Bachstelze on 2006-12-19
If I remmeber correctly, by default Totem uses the GStreamer backend instead of Xine. To use Totem-Xine, just run :

```
sudo apt-get install totem-xine
```

---

