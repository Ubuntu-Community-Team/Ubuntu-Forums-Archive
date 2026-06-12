---
title: "Trying out Kubuntu."
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by thepopasmurf on 2008-01-09
I already have ubuntu but I would like to try Kubuntu.

Is there a way to try out Kubuntu on my current ubuntu and how can I remove it if I don't like it.

---

### Post by taurus on 2008-01-09
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
You can pick which window manager you want to use from the Sessions (bottom left) from the GUI login screen.

And if you want to remove it later, here's how, [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome).

---

### Post by TeraDyne on 2008-01-09
You can get it by opening "Accessories > Terminal" In the Applications menu and typing:

```

sudo apt-get install kubuntu-desktop

```

That will download and install the KDE desktop and the default applications.

To remove it, you can follow the instructions here: [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

Edit: O_O; Holy... How close were the posts?

Edit 2: Just noticed that I forgot the info for switching to the KDE desktop. Whoops. Yeah, follow taurus' post.

---

