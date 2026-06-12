---
title: "Quick AiGLX question."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Sunnz on 2006-12-15
I have heard/read about it and attempted to install them on my ubuntu and gentoo boxes.

I am however, a bit confused... so I hope to clarify my confusion before I go any further in tinkering with my computers.

1, I have a nVidia card. I have installed the nVidia-glx driver, the 9XXX series one, and I am pretty sure that is required to do AiGLX.

2, As far as I understand, AiGLX and XGL is where the OpenGL engine is used to draw the DE, which results faster Desktop experience? Please tell me if I get the idea wrong here. And it is just AiGLX or XGL by itself, no fancy WM like Compiz/Beryl is required - they are for the eye candies, right?

---

### Post by Sunnz on 2006-12-15
3, So AiGLX is built into xorg 7.1?? After the nVidia is being installed, all I need to do is add into xorg.conf something like "AiGLX" "enable" and "Composition" "true" in "extensions" and etc??? Right???

4, How do I know if AiGLX is "working"?? I am not messing with fancy WM yet(beryl/compiz), I just wanted a more responsive DE at this stage. I've checked nVidia driver by glx-info and look for direct rendering: yes; so the driver is correctly installed.

Cheers.

---

### Post by dbd on 2006-12-15
I think that all you need to do to get your graphics card working fully with your desktop is to ensure the correct drivers are installed. As far as I know there is no reason to set up AIGLX or Xgl unless you also want to use Beryl or compiz for eye candy, although I may be wrong.

What are your system specs? If you have a slow system and want better performance it may be best to go with Xubuntu (which you can install on top of a normal ubuntu install by installing the xubuntu-desktop package).

Also, to see if you are using the correct graphics drivers it may be useful for us to see the output of 
> cat /etc/X11/xorg.conf

For info on installing AIGLX on see here: [https://help.ubuntu.com/community/CompositeManager/AIGLX?](https://help.ubuntu.com/community/CompositeManager/AIGLX?)

---

