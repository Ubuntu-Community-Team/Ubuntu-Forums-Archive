---
title: "How to create x11 cursors?"
date: 2005-12-11
forum: Art &amp; Design
---

### Post by commodore on 2005-12-11
Are there any tutorials on it? I downloaded a cursor set to figure it out, but the files are wierd and they are not images.

---

### Post by commodore on 2005-12-12
So many people are making those. How can't there be anyone who knows how to make them?

---

### Post by commodore on 2005-12-13
Bump

---

### Post by benplaut on 2005-12-13
the first step is to download a few cursors on gnome-look, and look at the config files for them... i haven't gone much beyond that

---

### Post by commodore on 2005-12-13
Lol

---

### Post by benplaut on 2005-12-13
hey, it works... i've got the highest rated theme on gnome-look from modding another one ;)

[http://gnome-look.org/index.php?xsortmode=high&page=0](http://gnome-look.org/index.php?xsortmode=high&page=0)

---

### Post by commodore on 2005-12-14
Well, I want to make my own images.

---

### Post by Jinx-Wolf on 2008-02-22
I'm reviving this dead thread, cause I don't want to make a new one...

I have a cursor theme, but the transparency of the busy cursor is much to large.

How does one create and/or edit the image files?

---

### Post by Jinx-Wolf on 2008-02-22
Nobody knows how to make cursor sets?

---

### Post by Jinx-Wolf on 2008-02-23
Bumping one more time:

This is the cursor I'm trying to use:
[http://gnome-look.org/content/show.php/Green+Apparatus?content=72698]("http://gnome-look.org/content/show.php/Green+Apparatus?content=72698")
The issue with it is in the comments.

help?

---

### Post by Chokkan on 2008-02-23
Oh, I love your cursor set. Very nice indeed. I hope someone can help with this 'cos I'd love to see more from you :)

---

### Post by Aphorism on 2008-02-23
Hope this helps.  You can create some intriguing new works using it. Pay close attention to the animated approach, as there are some roll-ons and roll-offs that might be achievable.

man xcursorgen

```
NAME
xcursorgen - create an X cursor file from a collection of PNG images

SYNOPSIS
xcursorgen [ -V ] [ --version ] [ -? ] [ --help ] [ -p dir ] [ --prefix dir ] [ config-file [ output-file ] ]

DESCRIPTION
Xcursorgen reads the config-file to find the list of cursor images along with their hotspot and nominal size information. Xcursorgen converts all of the images to Xcursor format and writes them to the output-file.

Each line in the config file is of the form:
<size> <xhot> <yhot> <filename> <ms-delay>

Multiple images with the same <size> are used to create animated cursors, the <ms-delay> value on each line indicates how long each image should be displayed before switching to the next. <ms-delay> can be elided for static cursors.

If config-file is not specified, or is specified as "-", standard input is used for the configuration file. If output-file is not specified, or is specified as "-", standard output is used for the output file.
OPTIONS

-V, --version
    Display the version number and exit.
-?, --help
    Display the usage message and exit.
-p dir, --prefix dir
    Find cursor images in the directory specified by dir. If not specified, the current directory is used. 

```

---

### Post by ColeNi on 2010-01-24
try here:

[http://www.mediafire.com/?8zyxnhzm9ta](http://www.mediafire.com/?8zyxnhzm9ta)


I haven't actually tried it yet, but it looks promising...

---

