---
title: "Ubuntu mouse cursor idea, pics attached."
date: 2006-05-06
forum: Art &amp; Design
---

### Post by graigsmith on 2006-05-06
Hi i had this ubuntu mouse cursor idea, and so i went ahead and did it in inkscape. does anyone like it? or hate it?   anyone know how to make a mouse cursor theme out of it?   Or know any good guides so i can turn this into a mouse cursor theme?

---

### Post by Omnios on 2006-05-06
I like it I might even use it if you make a package. Can you make it metalic lol.

---

### Post by graigsmith on 2006-05-06
i dont really know how to make an icon theme yet.  know any good resources? i looked at some other icon themes, but i can't figure out what file format the icons are in.

---

### Post by Omnios on 2006-05-06
Found this on Gnome-look.org.
[http://www.gnome-look.org/content/show.php?content=34031]("http://www.gnome-look.org/content/show.php?content=34031")

---

### Post by graigsmith on 2006-05-06
hmm, i tried that and i couldn't figure out to use that.

---

### Post by Omnios on 2006-05-06
I tryed t o get ti working but does not seem to have a way of importing the images, Ill look for another

---

### Post by Omnios on 2006-05-06
Found this Xcursor theme tutorial on GNome-files
[http://www.gnome-look.org/content/show.php?content=11428]("http://www.gnome-look.org/content/show.php?content=11428")

---

### Post by graigsmith on 2006-05-06
cool thanks, i tried finding a tutorial even, and all that i found were tutorials for installing the cursor themes.

---

### Post by graigsmith on 2006-05-08
well, i can't figure out how to make this a mouse cursor. if anyone wants to try, here's the inkscape file.

---

### Post by Omnios on 2006-05-09
Checked synaptic and found this for icons and cursors. I think its a command line converter that transforms the image into the cursor format which is a first step as this seems to be what is holding us back. Check out icon-slicer in synaptic. Also xcursorgen which I can not seem to get to work.
```
tom@reboot:~$ xcursorgen --help
usage: xcursorgen [-Vh] [--version] [--help] [-p <dir>] [--prefix <dir>] [CONFIG [OUT]]
Generate an Xcursor file from a series of PNG images

  -V, --version      display the version number and exit
  -?, --help         display this message and exit
  -p, --prefix <dir> find cursor images in <dir>

With no CONFIG, or when CONFIG is -, read standard input. Same with OUT and
standard output.
tom@reboot:~$


```

---

### Post by commodore on 2006-05-10
Download [http://www.gnome-look.org/content/show.php?content=32627](http://www.gnome-look.org/content/show.php?content=32627) It has the sources from what it was created from. This way you can figure out how to create the configuration file. It's what I did. If I remember correctly the configuration file contains the location of the spot that clicks on stuff.

---

