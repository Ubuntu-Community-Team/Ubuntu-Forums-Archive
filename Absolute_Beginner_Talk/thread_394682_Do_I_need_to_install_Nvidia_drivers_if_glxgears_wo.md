---
title: "Do I need to install Nvidia drivers if glxgears works?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-27
Hi guys,

When I installed Ubuntu 6.06 i386, I noticed that I didn't have to install graphics drivers, and glxgears would work. Previously in AMD64 version, I needed to install the drivers before glxgears would work. So far my benchmark of "whether my drivers are installed" are to run glxgears.

But I noticed something...this time, the glxgears are rotating very slowly. And my default screensaver (something like windows flower box) moves extremely slowly too.

this is the result of my glxgears framerates:
```

gkinson@ubuntu:~$ glxgears -printfps
1209 frames in 5.5 seconds = 219.991 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
kinson@ubuntu:~$

```

How would I check whether my video drivers are installed then?

Cheers and thanks,
Kinson

---

### Post by lamalex on 2007-03-27
installing them will speed up glx and give you worthwhile 3d capabilities

---

### Post by eitch on 2007-03-27
glxgears is only one of the few things I would check, if you want to be sure you 3d works. the other would be that glxinfo of fglrxinfo (depending on your graphics adaper) shows direct rendering = yes. And also there shouldn't be anything like mesa driver loaded or so...

Hope that helped you....

eitch

---

### Post by ceeg on 2007-03-27
I didn't want to make a new thread, so maybe I'll hijack this one :)

Will installing nvidia drivers speed up my gnome FPS at all? Gnome bottlenecks sometimes for me resulting in medium lag and response, which is odd considering I have 1GB ram and an athlon 2700.

---

### Post by eitch on 2007-03-27
I can't say really, but as far as I know the nvidia 2d-drivers will certainly help, but that is only true if the problem lies with the default xorg driver loaded on your machine. 

Anyone got any other insight on the problem?

---

### Post by ceeg on 2007-03-28
So yeah installing nvidia-glx made gnome a speed demon. Win :)

---

### Post by deuchar1 on 2007-03-28
Ubuntu will autodetect the nvidia card and run it with only 2d capabilities. Works fine for general desktop use, but obviously it won't handle 3d OpenGL support.

I ran Envy to get the correct drivers installed and confgiured everything through the Nvidia settings GUI. 

That also sped up my glxgears count quite significantly, as you'd expect. And screensavers appeared as screensavers and not as slideshows :)

---

