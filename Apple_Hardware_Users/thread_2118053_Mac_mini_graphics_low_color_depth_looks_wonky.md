---
title: "Mac mini graphics low color depth looks wonky"
date: 2013-02-20
forum: Apple Hardware Users
---

### Post by monkeypet on 2013-02-20
i installed ubuntu 12.04 and 12.11 on an intel mac mini 2012 model.  I am using the HDMI connected to 1080p TV (samsung).  The install was good and it boots up into xwindows fine.  However, I am seeing that the color depths is low.  Maybe it is using 256 colors, 8bpp.  However, I don't know where to look to figure things out.  The color is all dithered and yucky.  I believe this model mac mini has the Intel HD 4000 graphics unless I am wrong.

---

### Post by monkeypet on 2013-02-21
Now, I am suspecting that it isn't the graphics card at fault.  When I connect a normal computer monitor using a HDMI to DVI converter, the color depth seems fine.  Only when I connect it via HDMI to my Samsung TV does the color depth get reduced.

I think I need to modify the display/screen section of my xorg.conf.  Hoping someone can give me hints?

---

### Post by monkeypet on 2013-02-21
I stumbled upon the post below and that fixed my issue.

These cmds (first one fixed it):

intel_reg_write 0x70008 0xC4002000
intel_reg_write 0x70180 0xDA004400

[http://lists.freedesktop.org/archives/intel-gfx/2012-February/015395.html](http://lists.freedesktop.org/archives/intel-gfx/2012-February/015395.html)

Here is the link to the bug:

[https://bugs.freedesktop.org/show_bug.cgi?id=46800](https://bugs.freedesktop.org/show_bug.cgi?id=46800)

---

