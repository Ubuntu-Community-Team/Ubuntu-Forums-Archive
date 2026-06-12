---
title: "Shutting Down X-server"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by dougmoser on 2007-01-31
When I am installing my nvidia driver it says x-server needs to be closed.  What is the terminal command to do that?

---

### Post by tchoklat on 2007-01-31
easy

[ctr][alt][bsksp]

---

### Post by dougmoser on 2007-01-31
that worked but then x-server started right back up.  i need it to stay closed.  then how do I start it back up again?

---

### Post by bodhi.zazen on 2007-01-31
Ctrrl-Alt-Backspace will restart X.

What you want is;

```
sudo /etc/init.d/gdm stop
```

Go ahead and install the nvidia driver and re-start:

```
sudo /etc/init.d/gdm start
```

Even easier, use the envy script:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dougmoser on 2007-01-31
Thank you so much.  You guys are awesome.

---

