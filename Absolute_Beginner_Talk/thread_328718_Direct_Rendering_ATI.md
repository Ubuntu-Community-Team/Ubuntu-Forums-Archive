---
title: "Direct Rendering ATI"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by opticalfiber on 2006-12-31
i've installed correctly fglrx drivers following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
and I verified it works typing fglrx!
but if i type glxinfo grep | rendering
it says: direct rendering: no
Any ideas?!:confused:

---

### Post by bvanaerde on 2006-12-31
> **opticalfiber said:**
> it says: direct rendering: no
Try this:
> glxinfo | grep rendering

It should do the trick ;)
edit: what I meant is: you should put the pipe (|) in front of the grep command.
But as you mentioned it displayed the line "direct rendering: no", I guess you entered it correctly.

What's the output of this command?
> fglrxinfo

---

### Post by schnauzer93 on 2008-03-25
I also have this problem. 

My fgrlxinfo output is:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


```

however, when I type ```
glxinfo | grep rendering
```

I get ```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
I am a beginner, and do not know how to set this.

If anyone out there on teh intarwebz could help me, that would be super-duper.

---

