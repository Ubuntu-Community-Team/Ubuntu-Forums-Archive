---
title: "DVD Playback"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Miakehl on 2006-03-10
I try to use apt-get to enable DVD playback, but for some reason it dosent work. Anyone have any way to install it?

_Mia

---

### Post by Jason_25 on 2006-03-10
This is a working procedure.
```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

---

### Post by mstlyevil on 2006-03-10
[QUOTE=Miakehl]I try to use apt-get to enable DVD playback, but for some reason it dosent work. Anyone have any way to install it?

_Mia[/QUOTE]

You also have to uncomment your universe and multiverse repositories. You do that by editing your sources list. To do that open the terminal and type

```
sudo gedit /etc/apt/sources.list
```

Now you want to delete the # from in front of the multiverse and universe sources. This will be located in front of the lines that start with deb. Now save the file and update your sources by typing

```
sudo apt-get update
```

After that you should be able to install the libdvdread file.

---

