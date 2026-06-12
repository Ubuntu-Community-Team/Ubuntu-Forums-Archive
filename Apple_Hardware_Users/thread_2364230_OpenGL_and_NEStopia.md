---
title: "OpenGL and NEStopia"
date: 2017-06-20
forum: Apple Hardware Users
---

### Post by Richardcavell on 2017-06-20
Hello everyone. I've just installed Ubuntu 16.04 MATE on an iMac5,1 that has a Radeon Mobility X1600 video chipset.  NEStopia runs, but when I attempt to run a "ROM", it quits unexpectedly. I've run NEStopia on this machine under OS X without issues. Higan chugs on my machine, unfortunately. Does anyone have any ideas? 

```

richard@richard-iMac:~/Coding/wrap$ nes
0 joystick(s) found:
Could not create glcontext: Could not create GL context: GLXBadFBConfig
OpenGL: (null)
Database: 2901 items imported from internal DB
/home/richard/.nestopia/disksys.rom not found, Disk System games will not work.
Ines: 32k PRG-ROM set
Ines: 8k CHR-ROM set
Ines: vertical mirroring set
Ines: NTSC set
Ines: mapper 0 set
Board: NES-NROM-256
Board: 32k PRG-ROM
Board: 8k CHR-ROM
Region: NTSC
nes: Couldn't find current GLX or EGL context.
richard@richard-iMac:~/Coding/wrap$ glxinfo | head -n 20
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 

```

---

### Post by howefield on 2017-06-20
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by deadflowr on 2017-06-20
Probably best to see what it actually had to say about OpenGL
```
glxinfo | grep OpenGL
```

---

### Post by Richardcavell on 2017-06-20
```
richard@richard-iMac:~/Coding/wrap$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV530
OpenGL version string: 2.1 Mesa 12.0.6
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:

```

---

### Post by deadflowr on 2017-06-20
Looks like nestopia requires OpenGL 3.2 at the very least:
[http://0ldsk00l.ca/nestopia/]("http://0ldsk00l.ca/nestopia/")
>  - Updated to modern OpenGL (version 3.2 minimum)
Whatever that means.
:(:-?

---

### Post by Richardcavell on 2017-07-04
Hi everyone. Just wanted to reply so that this thread is able to be viewed by other people.  Yes, it seems that the NEStopia included with Ubuntu 16.04 is actually the Undead Edition, version 1.47-1, which requires hardware capable of OpenGL 3.2 minimum. I have pre-OpenGL 3.2 hardware.  I installed version 1.46-2 from [http://archive.ubuntu.com/ubuntu/pool/universe/n/nestopia/](http://archive.ubuntu.com/ubuntu/pool/universe/n/nestopia/) (which does not require OpenGL 3.2), and it works perfectly on my machine.  Hope this helps.

Richard

---

