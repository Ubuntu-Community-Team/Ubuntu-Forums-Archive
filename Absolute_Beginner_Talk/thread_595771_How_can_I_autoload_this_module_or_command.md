---
title: "How can I autoload this module or command"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-10-29
Lately I've been forced to use this command everyday.  And it's getting annoying having to do this everytime I reboot the PC.  How can I make this module or command autoload on every single boot?
```
sudo modprobe -r pcspkr
```

---

### Post by nick_h on 2007-10-29
To stop the module loading on boot, add the line
```
blacklist pcspkr
```
to /etc/modprobe.d/blacklist

---

### Post by jingo811 on 2007-10-29
That was some elegant fix thanks.  It crashed with my newly installed Compiz Fusion after the first reboot.  So I had to make a hard reboot with the PC reset button but then things worked just fine.

---

