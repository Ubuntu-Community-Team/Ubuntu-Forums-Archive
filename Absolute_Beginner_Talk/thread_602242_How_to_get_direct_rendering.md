---
title: "How to get direct rendering?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-04
First, I have an Ati Radeon 9500 Pro.

If I use the drivers in the repos (8.37) I get direct rendering.  However, I can't play 3d games because anything 3d just freezes the entire system.  I don't know why, but it does.  I disabled the restricted drivers in the repos and downloaded Envy.  I used Envy to install 8.40 in hopes that would fix my freezing problems in 3d applications, but I can't even run 3d applications because I don't have direct rendering.  glxinfo | grep direct gives me this 

 glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


Any idea how to fix it?  I don't want to use the repo drivers for obvious reasons, but I can't seem to get 8.40's to work at all.

---

### Post by TheOrangePeanut on 2007-11-04
Okay, so I used Envy to uninstall the 8.40s and then I used Envy to install the 8.42s.  They installed correctly and I had direct rendering, but 3d applications wouldn't even start up (and my computer would still freeze.)  I decided to go back to the 8.37s from the repos, but I've had trouble.

I uninstalled the 8.42s using Envy.  I restarted and then enabled the driver from the repos.  I also moved my xorg.conf that I backed up before doing ANY of this back to /etc/X11.  I restarted and the restricted device manager says that the driver is not in use (even though it is enabled.)  Likewise, I get no direct rendering and the same error message.

I'm getting very frustrated.  I've made several posts about getting my drivers to work that never made it anywhere (you can look at my post history to see).  If someone could help me get my restricted drivers 8.37s back working before I'd be at least feeling a little better.

---

### Post by jpittack on 2007-11-04
There are some threads that already exist in the Multimedia and Video section.  Everyone has tons of trouble with ATI cards, myself included.  Which thread you look at will depend on if you have a 32 or 64 bit install.  Keep in mind if you are using desktop effects or plan on using them.  Reverting to metacity using the command

> metacity --replace

will help elimante problems with full screen games.  If you aren't using compiz, well, don't bother with the command, as you are already using metacity.

I will gladly redirect you to a forum how to that should solve your problems.  I will need to know as much as I can about what you are doing with this driver and your type of install.  Of course, you are welcome to look yourself.  My intent will be to help you with the 8.42 drivers, as I have found attempting to revert back to the 8.37 drivers never works, atleast for me.

If you plan on using me for an avenue for help, please tell me if the command

> fglrxinfo

returns with mesa or ati driver output.

You will learn a lot when working with ati drivers.  I hope you see it as a learning experience.

---

