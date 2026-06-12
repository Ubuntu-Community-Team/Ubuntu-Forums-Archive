---
title: "ImageMagick JPEG"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by pocon on 2008-04-18
I don't appear to be able to get ImageMagick-6.3.9 to find the JPEG library.

I run: ```
 sudo ./configure --disable-static --with-modules --prefix=/usr
```

and in the output (abbreviated output):

[COLOR="RoyalBlue"]JPEG v1           --with-jpeg=yes  [/COLOR]                  [COLOR="Red"]  no[/COLOR]

of course I'm expecting a yes instead of a no value - jpeg-6b is installed...

Any suggestions?

Thanks,
Paul

---

### Post by joshrobinson on 2008-04-18
isnt imagemagick in the repos?

---

### Post by joshrobinson on 2008-04-18
i ran just a regular old ./configure
and i got
```
JPEG v1           --with-jpeg=yes		yes
JPEG-2000         --with-jp2=yes		yes

```

have you tried a standard ./configure without the other options?

---

### Post by pocon on 2008-04-19
Yes it is, but its an older version - I believe its 6.2 I'm trying to upgrade to 6.3.9.

I did try with a regular ./configure, same result. 

btw, thanks for the quick reply yesterday.

---

### Post by pocon on 2008-04-19
The package actually does install - it just doesn't recognize JPEG files. When I try to convert one I get this message:

[COLOR="Blue"] no decode delegate for this image format[/COLOR]

---

