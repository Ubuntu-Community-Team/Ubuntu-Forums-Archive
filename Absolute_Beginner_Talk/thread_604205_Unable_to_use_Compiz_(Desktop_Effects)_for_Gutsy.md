---
title: "Unable to use Compiz (Desktop Effects) for Gutsy"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by abhilash82 on 2007-11-05
I have been using desktop effects in the Feisty for a long time and i haven't had any problems whatsoever. In Gutsy I am not able to enable the Desktop effects even in the Normal mode. I get a message saying that "Unable to use desktop effects". I have given my PC configuration in the footer. Please help me out with a workaround for the above. I have also tried installing the Advanced Compiz Config manager and this package is not starting up.

:confused:

---

### Post by Digitallysick on 2007-11-05
what type of graphics card do you have?

---

### Post by abhilash82 on 2007-11-06
Onboard video as per Intel 865GBF motherboard.

---

### Post by lazyart on 2007-11-06
type compiz at the terminal and post the output... we can see why it's refusing to start.

---

### Post by adityakavoor on 2007-11-06
[http://ubuntuforums.org/showthread.php?t=579530](http://ubuntuforums.org/showthread.php?t=579530)

this might help

---

### Post by abhilash82 on 2007-11-07
Output of running compiz --replace:

> abhilash@abhilash-desktop:~$ compiz --replace
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/bin/sh: gtk-window-decorator: not found
inotify_add_watch: No such file or directory

my window panels go missing and as per the error message above should i install gtk-window-decorator to restore my panels?

---

