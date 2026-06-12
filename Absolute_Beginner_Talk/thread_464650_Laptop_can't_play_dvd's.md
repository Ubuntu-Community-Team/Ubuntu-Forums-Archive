---
title: "Laptop can't play dvd's"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-06-04
I installed all the codecs, libdvdcss and dev, and it still tells me I'm trying to play an encrypted dvd... do I have libdvdcss installed.  Yes, I do ... and still can't play dvd's on my lapyop.. any thots ?
Thanks

---

### Post by RomeReactor on 2007-06-04
Hi. If you're using Totem to view DVDs, make sure it's **totem-xine** instead of **totem-gstreamer**; use Synaptic to search for it, and install all xine-related packages also. Or, form the terminal:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by MrKlean on 2007-06-05
Thanks, but that didn't work :(   I still get ...The source seems encrypted,and can't be read. Are you trying to play an encrypted DVD without libdvdcss?   BUt I have all that plus codecs installed.  Using feisty fawn on an Acer laptop.

---

### Post by MrKlean on 2007-06-05
I read where the region code might not be set, sooooo I tried that. Still get the same error ; ( Help appreciated !

---

### Post by RomeReactor on 2007-06-05
Do a search for **libdvd** in Synaptic and make sure every package is installed (except the development packages); or, from the terminal:
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3
```

---

### Post by minj on 2007-06-06
Something funny going on with totem in feisty. When I use totem-xine everything is ok, but with totem-gstreamer if you chose to play dvd from totem's menu, error message (plugins requered) is displayed. However, if I explicitly direct totem-gstreamer to dvd:///dev/hdc (my DVD-ROM device) it plays fine :o

Edit: the same goes for ubuntu's autoplay feature in gnome-volume-properties. Totem is again directed with comand totem %m, so I'm guessing it's only the menu that's not working.

---

### Post by Cheese Sandwich on 2007-06-12
I'm also having this problem.

---

### Post by Cheese Sandwich on 2007-06-12
Bug #117820??

---

