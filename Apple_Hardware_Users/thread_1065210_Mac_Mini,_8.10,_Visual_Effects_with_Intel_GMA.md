---
title: "Mac Mini, 8.10, Visual Effects with Intel GMA"
date: 2009-02-09
forum: Apple Hardware Users
---

### Post by gundo on 2009-02-09
Hello everyone,

Ive just installed Ubuntu for the first time on my intel mac mini.
Everything seems fine, except i cant get the visual effects running, but they would work when I booted into the live CD.

here is the output of lspci:
mark@macubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Does anyone know why this is not working? 
Thanks very much,

mark.

---

### Post by mpsii on 2009-02-09
Check the output of the following:
```
glxinfo|grep DRI
```

DRI should = YES

If not, no effects. Are you using the intel linux drivers for the GMA card?

---

### Post by rcmn on 2009-02-09
nevermind

---

### Post by gundo on 2009-02-10
Hiya,

thanks for the reply.
Ive since got it working now, by changing the following in xorg.conf:
```

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual 2048 1024
		#Virtual 2432 1024
	EndSubSection

```

The answer to your question is:
```
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061102 x86/MMX/SSE2

```

Ive no idea what any of this means! Im just glad its working now! I assume that im using the linx intel drivers, ive just done a fresh install and havnt changed anything. Is there any way I can tell?
Thanks,
Mark.

---

