---
title: "[SOLVED] Can't install driver for GeForce 7600 GT???"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by jtrink on 2008-04-09
Hey, I dunno if i'm studpid or what, but I'm trying to get compiz working with gusty gibbon... I go to the appearance preferences tab > custom and it says : "Desktop effects could not be enabled" (side note: I followed directions on how to install the emerald and advanced desktop appearance from the snyapic package manager)

Then i went to system > admin > restricted drivers manger: and it says "your hardware does not need any restricted drivers"

What can i do to enable the custom tab  under desktop appearances? Any ideas?

---

### Post by buried on 2008-04-09
Try installing the drivers from the NVidia website, look for linux version, if you need a linux instruction if the driver is a tar.gz, I'll post, if it's .deb, .bin doubleclick, search around Ubuntu for more help, I bet there's a tutorial somewhere.

---

### Post by jtrink on 2008-04-09
"NVIDIA-Linux-x86-169.12-pkg1.run" there is the name of the file... And it says the type is "shell script"

---

### Post by jtrink on 2008-04-09
if this helps...

jared@jared-linux:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by jtrink on 2008-04-09
I installed in safe graphics mode... Could this be why i have no restricted drivers to access??

here is my glxinfo | head information:

jared@jared-linux:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer




can anyone please help?:confused:

---

### Post by swoll1980 on 2008-04-09
use envy it's the easiest way  [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by buried on 2008-04-09
Yes, yet envy is the easiest way.

---

### Post by Sef on 2008-04-09
Did you open [multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu")?

---

### Post by jtrink on 2008-04-09
I'm just going to wait and install hard when it comes out. I was using VirtualBox to run Gusty and everytime I tried searching for my video card... VGA VBox video adapter came up. I dunno, I'll prob just install with the wubi installation for hardy.

---

### Post by jtrink on 2008-04-09
I am almost postive the problem was VirtualBox. After I uninstalled Ubuntu and tried the live version I was able to enable my driver in teh Unrestricted drivers panel. When i used ubuntu in VirtualBox I was not able to do that. Wonder if anyone else had a similar problem, but im marking this thread as solved.

---

