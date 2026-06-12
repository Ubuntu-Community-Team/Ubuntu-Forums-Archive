---
title: "Wireless icon gone!?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by crav on 2007-07-31
I seem to have accidentally gotten rid of the wireless notification icon. It's part of the network manager applet. The network manager icon is still there, but i can no longer get the wireless bars icon. Any ideas as to how I can get my icon back?

---

### Post by aysiu on 2007-07-31
Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
killall nm-applet
nm-applet --sm-disable
```

---

### Post by Aholiab on 2007-11-29
I <killall nm-applet>, but Terminal stares at me when I <nm-applet --sm-disable>.

What should I think?

---

### Post by Aholiab on 2007-11-29
Now I notice that the network icon is gone, but there is no Wireless icon. I guess that comes from the second command, but nothing is happening. :confused:

---

### Post by Evil Wayz on 2007-11-29
copy and paste the following from terminal and tell me what it tells you:

nm-applet --sm-disable

---

### Post by Aholiab on 2007-11-29
Absolutely nothing. The Terminal is apparently in the process of executing this command, but it doesn't complete it. Waiting doesn't seem to help. So I Ctrl-C and get out.

---

### Post by Aholiab on 2007-11-29
I was premature.

The network icon has reappeared, but not the wireless icon.

---

