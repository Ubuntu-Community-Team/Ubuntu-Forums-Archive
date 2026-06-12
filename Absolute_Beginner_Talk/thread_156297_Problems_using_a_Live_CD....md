---
title: "Problems using a Live CD..."
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Perigon on 2006-04-06
So, last night I was going to give Linux a try with a Live CD of Ubuntu. After it did it's little pseudo-installation thing (where you select your keyboard layout, resolution... etc) it seemed like it would try to boot up, but I'd just get a scrambled screen: [img]http://static.flickr.com/46/124387383_74efb63005_o.jpg[/img]

I found that picture on a forum where someone else was having the same problem, unfortunetly they didn't seem to have a solution either. After failing to get Ubuntu up and running, I tried Gnoppix, which as it turns out is just a modified version of Ubuntu. It ran into the same problem. 

Here are my specs, if it matters:

AMD64 3200+
Nvidia Geforce 6800GS
1GB RAM
[My mobo]("http://www.newegg.com/Product/Product.asp?Item=N82E16813138253")

---

### Post by Jason_25 on 2006-04-06
ctrl-alt-f1 , login

```

sudo nano /etc/X11/xorg.conf

```
change driver from "nv" to "vesa", ctrl-o, enter, ctrl-z
```

sudo /etc/init.d/gdm restart

```

---

### Post by taurus on 2006-04-06
Hey, that is a nice background!  It sounds to me like there is a minor problem with your video card!  At the boot screen, what if you type "linux noapci" (or even some other options) to see if it boots fine!!!

---

### Post by Perigon on 2006-04-06
[QUOTE=Jason_25]ctrl-alt-f1 , login

```

sudo nano /etc/X11/xorg.conf

```
change driver from "nv" to "vesa", ctrl-o, enter, ctrl-z
```

sudo /etc/init.d/gdm restart

```[/QUOTE]

w00t! It worked, thank you very much!

---

### Post by Perigon on 2006-04-06
Ok, I made a new partition and installed Ubuntu, but now I'm running into the same problem and the solution isn't working. When I open that conf file it's just blank. Can someone assist?

EDIT: Figured out the problem. X11 has to have the X in caps.

---

### Post by taurus on 2006-04-06
What is the output of this command from a terminal then?
```

ls -la /etc/X11 <-- capital X, not x!!!

```

---

