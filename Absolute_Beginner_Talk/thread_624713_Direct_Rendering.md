---
title: "Direct Rendering"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-11-27
i fired up the "glxinfo | grep direct" and this is what i get:

   ```
 sudo glxinfo | grep render

    direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
    OpenGL renderer string: Mesa DRI i815 20050821 x86/MMX/SSE
```

My graphic card is the Intel 82815 using the i810 drivers..where do i do this settings for LIBL_DEBUG??? cos znes emulator dont even work on my graphics..:confused:

---

### Post by mahiyar on 2007-11-27
Maybe this link will help [http://ubuntuforums.org/archive/index.php/t-331033.html](http://ubuntuforums.org/archive/index.php/t-331033.html) it seems that direct rendering is only possible on 16 bit color.

---

### Post by Da King on 2007-11-27
i already had it at 16 in the xorg.conf yet no changes..direct rendering is still NO:confused:

---

