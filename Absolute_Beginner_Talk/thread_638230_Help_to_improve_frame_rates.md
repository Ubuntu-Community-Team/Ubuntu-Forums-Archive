---
title: "Help to improve frame rates"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by GlorytheWIz825 on 2007-12-11
Hi guys,

I am not sure if it is the problem lies with my video card or some setting I am not configuring correctly. Basically my window scrolling and video playback seems to be significantly slower than when i was using XP. For example, scrolling in Firefox is not smooth as the frame rate cannot keep up. When I watch videos on YouTube, the frames are very jumpy and I essentially don't even get smooth playback. 

Like I said before, I'm not sure if this is a video card driver problem or something else.

Thanks in advance.

---

### Post by spiderbatdad on 2007-12-12
are you running compiz-fusion or other composite windows manger? What are your system specs?

---

### Post by skymera on 2007-12-12
i get jumpy videos on the web too.

perhaps a flash bug?

---

### Post by shae on 2007-12-12
What is the output of the following:
```
glxinfo | grep direct
```

```
glxinfo | grep 'OpenGL vendor'
```

```
glxinfo | grep 'OpenGL renderer'
```

```
glxinfo | grep 'OpenGL version'
```

---

### Post by GlorytheWIz825 on 2007-12-16
> **shae said:**
> What is the output of the following:
```
glxinfo | grep direct
```

```
glxinfo | grep 'OpenGL vendor'
```

```
glxinfo | grep 'OpenGL renderer'
```

```
glxinfo | grep 'OpenGL version'
```

1. direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
2. OpenGL vendor string: DRI R300 Project
3. OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
4. OpenGL version string: 1.3 Mesa 7.0.1

---

