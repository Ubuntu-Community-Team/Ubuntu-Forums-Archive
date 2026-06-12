---
title: "where do fonts go"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Dai777 on 2007-07-18
Just downloaded some fonts  and unzipped to my desktop(msttcorefonts).
How do I move these to the fonts folder?

It does not work by drag and drop or cut and paste!

any help would be most appreciated.


Thanks 
Dai

---

### Post by mlentink on 2007-07-18
create a .fonts directory in your home directory and copy them there

---

### Post by AlexenderReez on 2007-07-18
default font folder is in /usr/share/font

---

### Post by Dai777 on 2007-07-18
> default font folder is in /usr/share/font

Could you tell me how to use the terminal to put it here.
As I do not have permission to copy and paste the msttcorefonts here.

Sorry to be a bit of a pain but I'm new to Linux.

---

### Post by testube_babies on 2007-07-18
Make sure you have [extra repositories enabled]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories"), then
```
sudo apt-get install msttcorefonts
```

To install other TTF fonts:
[http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/](http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/)

---

### Post by dptxp on 2007-07-18
open nautilus in terminal to get access to to the fonts folder. Then copy fonts to the fonts folder.

I hope that I remember it right. No harm any way.

---

### Post by Dai777 on 2007-07-18
Cheers installed ok now. Had visions of having to use mv in terminal to do it. Got to get my head round this bash stuff.

---

### Post by Dai777 on 2007-07-18
cheers for the Ubuntu book link

---

