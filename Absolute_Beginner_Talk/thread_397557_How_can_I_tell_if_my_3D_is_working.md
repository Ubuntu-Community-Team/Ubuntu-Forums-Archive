---
title: "How can I tell if my 3D is working?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-30
I have not been using my 3D features of my ATI Radeon 9200SE video card. How do I know that it is working? Does the 3D look like a 3D movie where you have objects appearing as though they are coming out of the screen when you wear red and green lens glasses? Does it require some special glasses to see the 3D on my monitor?

Thanks for your input.
kh

---

### Post by Zuuswa on 2007-03-30
hahaha, no, thats not normally what a 3d graphics card does.  Instead it allows you to play games and run opengl screensavers and run beryl, etc.  To see if you have direct rendering, you can try a few things like

```
glxinfo
glxgears
```

with glxinfo there should be line 'Direct Rendering:', if it says yes then your 3d acceleration is working.

---

### Post by kittyhawk63 on 2007-03-30
> **Zuuswa said:**
> hahaha, no, thats not normally what a 3d graphics card does.  Instead it allows you to play games and run opengl screensavers and run beryl, etc.  To see if you have direct rendering, you can try a few things like

```
glxinfo
glxgears
```

Hey, it is funny. Glad you cleared that up. The reason I asked, I can find sites on the web and they have 3D art. or images. I just thought that these were images in 3D. Thanks for your reply.
kh

---

### Post by Maestro23 on 2007-03-30
Is my 3D enabled on my card?

> glxinfo | grep direct

---

### Post by kittyhawk63 on 2007-03-30
> **Maestro23 said:**
> Is my 3D enabled on my card?


 			 				glxinfo | grep direct

Guess not. Tells me that it can't register entrypoint.
Thanks.
kh

---

### Post by Zuuswa on 2007-03-30
although if I remember correctly the screensaver 'blobuole' or something like that has a stereo effect that supposedly works if you wear red and blue 3d glasses . . . havnt tried it though.

---

### Post by kittyhawk63 on 2007-03-30
> **Zuuswa said:**
> although if I remember correctly the screensaver 'blobuole' or something like that has a stereo effect that supposedly works if you wear red and blue 3d glasses . . . havnt tried it though.

I think I had 3D working in Windows using my ATI installer CD. But I don't think the same installer CD will work with Linux. I guess I should try it. However, today is the first time in almost two months that I have not had a screen crash with the ATI card. I saved my xorg file to disk just in case I have to reinstall.

---

### Post by Maestro23 on 2007-03-30
> **kittyhawk63 said:**
> I think I had 3D working in Windows using my ATI installer CD. But I don't think the same installer CD will work with Linux. I guess I should try it. Howevr, today is the first time in over a month that I have not had a screen crash with the ATI card. I saved my xorg file to disk just in case I have to reinstall.

Hey KH, I haven't been on the forums in about 3 weeks.  When I was last here, didn't you have your system up and running good?

---

### Post by kittyhawk63 on 2007-03-30
> **Maestro23 said:**
> Hey KH, I haven't been on the forums in about 3 weeks.  When I was last here, didn't you have your system up and running good?

NOPE!!!! I haven't had it working right since my first install over a month ago. I have installed this crazy program over 30 times and tried every thing I could think of to get it working. I still don't know why it is working now. Just today, actually last night, I finally got the ATI card from crashing. That's why I saved my .xorg file to floppy disk. Maybe you can advise me. Is there some other files I should save?
kh

---

