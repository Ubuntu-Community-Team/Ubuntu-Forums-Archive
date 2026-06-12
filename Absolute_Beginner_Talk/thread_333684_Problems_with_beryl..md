---
title: "Problems with beryl."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by aGit on 2007-01-07
I really had no idea where to post this thread, so i'm going to go with this, the newcomer section, cause after all, that is what i am to ubuntu, a newcomer.

Anywho, i have edgy with beryl/xgl installed on it, and after the install i have not been able to launch beryl on start up except for the very first time. Dont know why, even if i choose the correct session. it just wont start. However on terminal, i can start it with ease. but nowadays for somereason it has been runnin hella slow, the 3d animations lag, scrolling with mouse wheel on any browser is slow as a 10ft poo out of an ants behind, @ sign (shift + 2) doesnt work while using beryl, rolling the dekstop cube is slow and missing frames.... these are the problems i can think of now, i have geforce nvidia  GF6600 with the NVidia binary X.Org driver. 

when i start beryl from the terminal i get the following:

agit@agit-desktop:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Initiating splash
No framebuffer_object support! (only simple blur aviable)
No packed_depth_stencil support! (this may cause some artefacts in fbo mode)

when i installed beryl i remember the installer prompting that few packages could not be retrieved from the server. could this be why im having these problems? Could reinstall do the trick, or is there a "repair" install of some sort available? 

ps. tags? i have no idea what tags i should have used for the thread, so i went with edgy and beryl, sorry in advance if they were wrong some way :p 

-aGit

---

### Post by Waappu on 2007-01-07
Hi

You can try re-install. Here is example code
```
sudo aptitude reinstall beryl
```

---

### Post by aGit on 2007-01-08
ok i tried that, but it really is the same as it was before. i think i have to uninstall it and download the whole shebang again, and if the problem still presists, its not with beryl but with something else.

---

### Post by PriceChild on 2007-01-08
If you're on edgy & nvidia then follow [http://wiki.ubuntu.com/BerylOnEdgy](http://wiki.ubuntu.com/BerylOnEdgy)

oh and you need to remove xgl.

---

### Post by anjoze on 2007-01-08
Try this:
1- Update your Edgy
2- Install the latest Nvidia drivers: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (this is realy good)
3- fallow the instructions on: [http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page)

My beryl is working perfect with these steps.

---

### Post by aGit on 2007-01-09
Thanks for the help everyone looks like reinstall and update on nvidia drivers did it. =D

---

