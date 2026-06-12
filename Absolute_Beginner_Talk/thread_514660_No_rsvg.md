---
title: "No rsvg"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by xellzhang on 2007-08-01
I want to compile Lablgtk-2.6.0 for mldonkey. But it needs librsvg. So I use:
sudo apt-get install librsvg2-dev
and then I ran ./configure of Lablgtk. The result seems ok:
LablGTK configuration:
       [COLOR="Blue"] threads         system
        GtkGLArea       not found
        libglade        not found
        librsvg         yes
        libgnomecanvas  not found
        libgnomeui      not found
        libpanelapplet  not found
        gtkspell        not found

        debug           no
        C compiler      gcc[/COLOR]

Then I use "make world" to make it. But I got an error:
[COLOR="Red"]ml_rsvg.c:32:29: error: librsvg/rsvg-gz.h: No such file or directory[/COLOR]

I checked in /usr/include/librsvg-2 and could not find the file.

How to deal with it?

---

### Post by superstylin on 2007-08-05
Compiling sounds like serious business, you may have more luck posting this in the Programming sub-forum! :)

---

### Post by nitro_n2o on 2007-08-05
> **xellzhang said:**
> 

Then I use "make world" to make it. But I got an error:
[COLOR="Red"]ml_rsvg.c:32:29: error: librsvg/rsvg-gz.h: No such file or directory[/COLOR]

I checked in /usr/include/librsvg-2 and could not find the file.

How to deal with it?
Apparently you need libsrvg not libsrvg-2 at least that's what i get from the error..

---

