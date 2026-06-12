---
title: "Xserver not found after xgl bud install"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by El Viejo Lobo on 2007-03-13
I have a Dell Desktop PC  with Ubuntu 6.10. After trying to install GXL and failing  in doing it. I turned off my PC.  Now when I turned it on I get a window that say:
***"Failed to start the Xserver it is likely that it is not set up correctly. Would you like to view the Xserver out put to diagnose the problem. - {Yes}  {No}***

I click for yes and get a new window:
***GDM: Xserver/usr/bin/xgl :0 :0 -fullscreen - ac -accel  glx: buffer-accel  xv : fbo-kb-auth/ver/lib/gdm/:0 Xauth-molisten lcp vt7 error: command not executed. Please install the X server or correct GDM configuration and restart GDM***

What is the way out of this problem that is not reinstall Ubuntu from screch?

---

### Post by vijayanand_sodadasi on 2007-03-13
I had the same exact problem.  I didn't find the resolution yet, but I have a workaround (works for me).  This problem occurs to me everytime I boot afresh.

The workaround:
1. After the error screen appears, I click yes and a blank screen (black) appears.
2. Then I will press Alt+F1 which gives me a login prompt.  Then I reboot the computer and at the grub menu I select the safe mode ( or something of that kind, I dont remember the exact name) option.
3. It boots and gives only the command line interface.  Then I start gdm by using the command: sudo gdm
4. It starts my xserver and login screen appears, and I can log into the system.
5. After this even if I reboot again and select the normal mode, surprisingly xserver starts without error.  It seems that xserver error occurs only on my first boot.

_PS;_ I actually searched a lot but couldn't find a solution to my problem.  Still searching for one.  I actually replaced the /etc/X11/xorg.conf file which I took a backup before installing beryl.  I also did sudo dpkg-reconfigure xserver-xorg but nothing seem to have worked.

---

### Post by El Viejo Lobo on 2007-03-13
I had to reinstall Ubuntu.

---

