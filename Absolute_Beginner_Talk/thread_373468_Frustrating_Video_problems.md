---
title: "Frustrating Video problems"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Hairball on 2007-03-01
Hi, I've been trying to get my video working for about a week now. I'm using an Acer Aspire 5100 with an ATI Radeon Xpress 200M video card. I've done everything I've found on the internet, but nothing seems to work. Here's a little debug stuff:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.5.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
493 frames in 6.5 seconds = 76.212 FPS
450 frames in 6.3 seconds = 71.107 FPS
456 frames in 6.3 seconds = 72.606 FPS
456 frames in 6.3 seconds = 72.786 FPS
456 frames in 6.0 seconds = 75.953 FPS

```

As you can see, those framerates are absurdly low.  I know I shouldn't be using the Mesa drivers, but when I tried installing the ATI drivers, it didn't change anything. I read somewhere that I could change this by running 'fglrxconfig' but that command apparently doesn't exist.

Also, this is a minor detail, but I want my resolution to be 1440x900 rather than the default 1280x800, so I added that to my xconfig, but when I try changing it in the Screen Res options, it doesn't show up. 

My head hurts from all this stuff. I've used ubuntu for about a month now and I'm going insane because of this video problem. The only thing other thing I can think of is that I have an AMD Dual Core Turino proc which is a 64-bit hybrid. Would installing the 64-bit version of ubuntu change anything?

Any help would be greatly appreciated. Thanks in advance.

---

### Post by hansonry on 2007-03-01
Yikes sounds like a problem, I have a nvida card so it wasnt nearly as hard for me, but did you try envy? envy is a script or a program (Sorry I dont remeber wich) that automaticly installs and sets up your video card driver, Worked like a charm for me and my friends in Academia. You should alredy have it installed or just select it with your package manager. 

In any case envy might want you to not be running Xserver, in that case loggout and press *CTRL + ALT + F1* to get to the login prompt.

---

### Post by overdrank on 2007-03-01
> **Hairball said:**
> Hi, I've been trying to get my video working for about a week now. I'm using an Acer Aspire 5100 with an ATI Radeon Xpress 200M video card. I've done everything I've found on the internet, but nothing seems to work. Here's a little debug stuff:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.5.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
493 frames in 6.5 seconds = 76.212 FPS
450 frames in 6.3 seconds = 71.107 FPS
456 frames in 6.3 seconds = 72.606 FPS
456 frames in 6.3 seconds = 72.786 FPS
456 frames in 6.0 seconds = 75.953 FPS

```

As you can see, those framerates are absurdly low.  I know I shouldn't be using the Mesa drivers, but when I tried installing the ATI drivers, it didn't change anything. I read somewhere that I could change this by running 'fglrxconfig' but that command apparently doesn't exist.

Also, this is a minor detail, but I want my resolution to be 1440x900 rather than the default 1280x800, so I added that to my xconfig, but when I try changing it in the Screen Res options, it doesn't show up. 

My head hurts from all this stuff. I've used ubuntu for about a month now and I'm going insane because of this video problem. The only thing other thing I can think of is that I have an AMD Dual Core Turino proc which is a 64-bit hybrid. Would installing the 64-bit version of ubuntu change anything?

Any help would be greatly appreciated. Thanks in advance.

Hi I found this thread that may help. Good luck
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=ATI+Radeon+Xpress+200M](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=ATI+Radeon+Xpress+200M)

---

### Post by Maestro23 on 2007-03-01
And if you are still having trouble.  Try the Envy script.

1. Download the correct driver for your card.

2. Use the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works for both ATI and Nvidia.

If you want to reconfigure Xorg first and start from scratch:

> sudo dpkg-reconfigure xserver-xorg

Good luck.

---

### Post by Hairball on 2007-03-01
Thanks for the quick responses guys. I'm trying the solution Paul Capps' linked and if that doesn't take care of it, I'll try the envy script. Thanks!

---

### Post by Hairball on 2007-03-01
```

GL_RENDERER   = RADEON XPRESS Series Generic
GL_VERSION    = 2.0.6234 (8.32.5)
GL_VENDOR     = ATI Technologies Inc.

6682 frames in 5.0 seconds = 1336.323 FPS
7700 frames in 5.0 seconds = 1539.915 FPS
7705 frames in 5.0 seconds = 1540.953 FPS
7702 frames in 5.0 seconds = 1540.345 FPS
7639 frames in 5.0 seconds = 1527.690 FPS

```

You guys just made my day. Thanks so much!

---

### Post by overdrank on 2007-03-01
> **Hairball said:**
> ```

GL_RENDERER   = RADEON XPRESS Series Generic
GL_VERSION    = 2.0.6234 (8.32.5)
GL_VENDOR     = ATI Technologies Inc.

6682 frames in 5.0 seconds = 1336.323 FPS
7700 frames in 5.0 seconds = 1539.915 FPS
7705 frames in 5.0 seconds = 1540.953 FPS
7702 frames in 5.0 seconds = 1540.345 FPS
7639 frames in 5.0 seconds = 1527.690 FPS

```

You guys just made my day. Thanks so much!

Glad we could help!:lolflag:

---

