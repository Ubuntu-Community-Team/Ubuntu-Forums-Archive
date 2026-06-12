---
title: "[SOLVED] Cinelerra"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-11-27
Ok I installed cinelerra for gutsy by following the directions on the site. 
Everything went well but when I try to open it, it doesn't do anything. When I try to run it in the terminal I get:
> 
steven@steven-desktop:~$ cinelerra
cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory
steven@steven-desktop:~$ 


Any ideas?

---

### Post by piratesmack on 2007-11-27
anyone

---

### Post by CyfrMonk on 2007-12-01
Me too ...

I had Cinelerra working fine on Gutsy (installed from repos) then a few days ago I installed updates / patches and since then I've been getting this same error.

If I find a solution, I'll pass it along. Other OpenGL apps are working fine for me. Anyone else having issues?

---

### Post by Pena on 2007-12-01
This got it running for me

```
locate libGL.so.1.2
```

found /usr/lib/nvidia/libGL.so.1.2.xlibmesa, link it so cinerella can find it:

```
sudo ln -s /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
```

---

### Post by CyfrMonk on 2007-12-01
That did the trick for me Pena. Thanks!

---

