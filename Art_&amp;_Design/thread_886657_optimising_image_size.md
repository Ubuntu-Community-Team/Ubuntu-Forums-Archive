---
title: "optimising image size"
date: 2008-08-11
forum: Art &amp; Design
---

### Post by daz4126 on 2008-08-11
Hi,

I've created an icon theme using inkscape to make svg icons that are then exported to make 48x48 pngs.

I then resize these using the Nautilus resize image extension. But this seems to leave me with huge images. If I reduce the size using Gimp then the files are much smaller.

Is there any way that I can quickly reduce the size of a load of icons in one go and also a way of optimising the image size - my icon theme is much larger in size than the Human icon theme, yet it has less files!

thank,

DAZ

---

### Post by Pro-reason on 2008-09-11
So you're talking about reducing *file size* after an operating to reduce *image dimensions* results in a large file?

There are several tools to optimise PNGs.

Install them all!

```

sudo apt-get install *pngcrush optipng advancecomp*

```

An even better tool is *[pngout]("http://www.jonof.id.au/index.php?p=kenutils")*, but it cannot be added to the Ubuntu repositories, because it is not open-source.

---

### Post by Pro-reason on 2008-09-11
Once you have installed one or more image optimisers, run any one of them thus:

(assuming that you are in a directory that contains PNGs)

```

[I]
# This is from the advancecomp package.
# It will optimise files in-place.[/I]
**advpng -z4 *png**

[i]
# pngcrush can only optimise in place if we do one file at a time.
# So, we make an output directory.[/i]
**mkdir output && pngcrush -d output *png**

[I]
# optipng will optimise files in-place[/I]
**optipng -o7 *png**

[i]
# pngout can only handle one file at a time.
# So, we have to cheat, with a “while” loop.[/i]
**ls -1 *.png | while read IMAGE; do pngout $IMAGE; done**

```

---

