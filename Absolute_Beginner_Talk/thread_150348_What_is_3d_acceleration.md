---
title: "What is 3d acceleration?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-03-25
I have frequently come across posts talking about this whole 3d acceleration thing. What is it all about? 

I always assumed if I could see a GUI on the screen, my monitor has been set up fine. Is there more to it? 

If so, how do I know whether I have 3d accel enabled? 

Also, I read about the glxgears command. What is a decent fps to have? 

Thanks !

---

### Post by dermotti on 2006-03-25
If you dont know what is is you will never know you dont have it. Unless you try to play a video game with 3d graphics.

---

### Post by dcstar on 2006-03-25
[QUOTE=harisund]I have frequently come across posts talking about this whole 3d acceleration thing. What is it all about?

I always assumed if I could see a GUI on the screen, my monitor has been set up fine. Is there more to it?

If so, how do I know whether I have 3d accel enabled?

Also, I read about the glxgears command. What is a decent fps to have?

Thanks ![/QUOTE]
3D acceleration is using inbuilt hardware functions on a video card to create images on the screen, rather than the OS having to do it (in usually a much slower way).

Having it working should improve general video performance if the O/S recognises it and supports it.

**glxinfo** will tell you, look for:
```
direct rendering: Yes
```

As far as FPS go, it depends entirely on your hardware, you can search for a thread on people's own posted glxgears results:
```
glxgears -printfps
```

---

### Post by harisund on 2006-03-25
Thanks. So basically, I wouldn't notice a big difference until I try out some high performance games, right? In that case, I am really not worried.. 

Also, does "direct rendering: Yes" mean 3D enabled, or does it mean the other way around? 

Also, is VESA  some sort of a generic driver, or is it geared for one card / family of cards? Does using VESA talk anything about 3d accel? My card is an ATI, but the xorg.conf says it's using VESA. What is the tradeoff?

---

### Post by lordofkhemenu on 2006-03-25
[quote=dcstar]3D acceleration is using inbuilt hardware functions on a video card to create images on the screen, rather than the OS having to do it (in usually a much slower way).

Having it working should improve general video performance if the O/S recognises it and supports it.

**glxinfo** will tell you, look for:
```
direct rendering: Yes
``` 
As far as FPS go, it depends entirely on your hardware, you can search for a thread on people's own posted glxgears results:
```
glxgears -printfps
```[/quote]
Just an addendum -- The glxinfo "direct rendering: yes" won't necessarily mean your card doesn't support it, it just means it's not enabled.
When my X was auto-configured during the install of ubuntu, the generic vesa driver was used, therefore no direct rendering.
I had to change it to the "ati" driver and restart X. THEN I had direct rendering.
What graphics card do you have, harisund?

---

### Post by lordofkhemenu on 2006-03-25
[quote=harisund]Thanks. So basically, I wouldn't notice a big difference until I try out some high performance games, right? In that case, I am really not worried.. 

Also, does "direct rendering: Yes" mean 3D enabled, or does it mean the other way around? 

Also, is VESA  some sort of a generic driver, or is it geared for one card / family of cards? Does using VESA talk anything about 3d accel? My card is an ATI, but the xorg.conf says it's using VESA. What is the tradeoff?[/quote]
Change the vesa driver to 'ati' and restart X. 
[i saw this post after i posted my original reply]

---

### Post by harisund on 2006-03-25
haha.. interesting how that happened. 

Thank you very much. Just what I was looking for !1

---

