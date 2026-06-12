---
title: "GIMP Batch Production"
date: 2008-12-01
forum: Art &amp; Design
---

### Post by stooshbunutu on 2008-12-01
Hey, I wanted to look into simple batch production in GIMP. I was thinking simply resizing a bunch of JPG files to a certain % (say 50) of their original size.

I had a look at the tutorial and didn't find it particuarly useful.

Any help muchly appreciated,

Cheers

---

### Post by volanin on 2008-12-01
GIMP batch processing is very powerful with Script-Fu.
But it's very non-intuitive and intimidating in the beginning.

Here is a sample one that scales the current opened image to
500x500px, applies the unsharp-mask filter and a selective
gaussian blur, then saves the image as a JPEG called
image.jpg in the Desktop folder:

```
(define (scale-500px image drawable)
    (let*
        (
        (filename "/home/volanin/Desktop/image.jpg")
        )

        (gimp-image-scale image 500 500)
        (plug-in-unsharp-mask RUN-NONINTERACTIVE image drawable 0.5 0.5 15)
        (plug-in-sel-gauss RUN-NONINTERACTIVE image drawable 2 20)
        (file-jpeg-save RUN-NONINTERACTIVE image drawable filename filename 0.8 0 1 0 "" 0 1 0 0)
        (gimp-image-clean-all image)
    )
)


(script-fu-register "scale-500px"
                    _"Scale _500px..."
                    "Scale images to 500x500 size."
                    "Wagner Volanin"
                    "Wagner Volanin"
                    "9/13/07"
                    "RGB*"
                    SF-IMAGE    "Input image"    0
                    SF-DRAWABLE "Input drawable" 0
)


(script-fu-menu-register "scale-500px"
                         _"<Image>/Script-Fu/Utils"
)
```

After saving this to a .scm file, all you have to do is copy the
file to /usr/share/gimp/2.0/scripts/ and restart GIMP.

You can find technical information about all Script-Fu functions
by going to HELP > PROCEDURE BROWSER, but it's also very
non-intuitive.

Searching google for Script-Fu tutorials would be a very nice
start as well.
:)

---

### Post by michaelzap on 2008-12-01
You could also try using a tool that is designed specifically for batch processing, such as [Phatch]("http://photobatch.stani.be/").

---

### Post by Elzar on 2008-12-02
Phatch is good, but for batch resizing I use this:

[http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/](http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/)

---

### Post by donom on 2008-12-02
Couldn't python scripts do the same? How would I use them?

---

### Post by stooshbunutu on 2008-12-07
> **volanin said:**
> GIMP batch processing is very powerful with Script-Fu.
But it's very non-intuitive and intimidating in the beginning.

Here is a sample one that scales the current opened image to
500x500px, applies the unsharp-mask filter and a selective
gaussian blur, then saves the image as a JPEG called
image.jpg in the Desktop folder:

```
(define (scale-500px image drawable)
    (let*
        (
        (filename "/home/volanin/Desktop/image.jpg")
        )

        (gimp-image-scale image 500 500)
        (plug-in-unsharp-mask RUN-NONINTERACTIVE image drawable 0.5 0.5 15)
        (plug-in-sel-gauss RUN-NONINTERACTIVE image drawable 2 20)
        (file-jpeg-save RUN-NONINTERACTIVE image drawable filename filename 0.8 0 1 0 "" 0 1 0 0)
        (gimp-image-clean-all image)
    )
)


(script-fu-register "scale-500px"
                    _"Scale _500px..."
                    "Scale images to 500x500 size."
                    "Wagner Volanin"
                    "Wagner Volanin"
                    "9/13/07"
                    "RGB*"
                    SF-IMAGE    "Input image"    0
                    SF-DRAWABLE "Input drawable" 0
)


(script-fu-menu-register "scale-500px"
                         _"<Image>/Script-Fu/Utils"
)
```

After saving this to a .scm file, all you have to do is copy the
file to /usr/share/gimp/2.0/scripts/ and restart GIMP.

You can find technical information about all Script-Fu functions
by going to HELP > PROCEDURE BROWSER, but it's also very
non-intuitive.

Searching google for Script-Fu tutorials would be a very nice
start as well.
:)

I managed to manipulate your script to get it to do what I want, tyvm

---

### Post by shakma on 2010-11-05
> **Elzar said:**
> Phatch is good, but for batch resizing I use this:

[http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/](http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/)

+1 Awesome tip!

---

