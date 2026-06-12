---
title: "xrandr does not work on TV at 640x480 resolution"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by gpiccirilli on 2008-01-13
Hello,

I have XRANDR working on the S-Video output correctly however providing a resolution of 800x600 to my TV. Since this is not an HD TV, the resolution should be reduced to 640x480. 

If I try the command: xrandr --addmode S-video 640x480
here is what I get:

 ----
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18
 ----
 and if I try: xrandr --output S-video --mode 640x480
here is what I get:

 -----
xrandr: cannot find mode 640x480
 -----

Can someone assist?

Thanks

---

