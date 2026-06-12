---
title: "Is it possible to get the dimensions of an image via bash?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-12-19
Can I find the image dimensions via the command line? This would be helpful while using SSH as well as within local machines

---

### Post by jordanmthomas on 2007-12-19
try this:
```
file filename
```
The dimensions of images are listed here at the end of the line (last 3 words) and can be easily parsed and put into a script if need be,

**edit**
sorry, that doesn't seem to work on jpgs (I only tried a gif)

---

### Post by jordanmthomas on 2007-12-19
OK, I have found a better way.
You will need imagemagick installed (it seems to be installed on most systems I visit)
```
identify -format '%wx%h' filename
```
Will give you something like this:
```
500x400
```

---

### Post by pfwd.tech on 2007-12-19
ah thanks that worked a treat
the first one works on png

---

