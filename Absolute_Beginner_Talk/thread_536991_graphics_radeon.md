---
title: "graphics radeon"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-08-28
hello,
My system has a Radeon 2400xt graphics card and i dont whether i need to install any graphics drivers as such - the cd in the box didnt have any for Linux. when i type in
glxinfo |grep direct, it gives me the following response:-

[B]deep@deep-desktop:~$ glxinfo |grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect[/B]

When i tried to open an avi file with gxine, the picture was warbled and i got an error message 
video_out_xv: No adaptors found.

You can improve performance by installing an X11
driver that supports the Xv protocol extension.

My question is 
1. do i need to install any graphics drivers to get the best results from my card? - looking at above its no in direct rendering
2. what does the error message  video_out_xv: No adaptors found mean?


ps:
the same avi file does open in vlc however it freezes after 10 mins for some reason? also the avi file is stored on my hdd.

---

### Post by overdrank on 2007-08-28
> **deepblue80 said:**
> hello,
My system has a Radeon 2400xt graphics card and i dont whether i need to install any graphics drivers as such - the cd in the box didnt have any for Linux. when i type in
glxinfo |grep direct, it gives me the following response:-

[B]deep@deep-desktop:~$ glxinfo |grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect[/B]

When i tried to open an avi file with gxine, the picture was warbled and i got an error message 
video_out_xv: No adaptors found.

You can improve performance by installing an X11
driver that supports the Xv protocol extension.

My question is 
1. do i need to install any graphics drivers to get the best results from my card? - looking at above its no in direct rendering
2. what does the error message  video_out_xv: No adaptors found mean?


ps:
the same avi file does open in vlc however it freezes after 10 mins for some reason? also the avi file is stored on my hdd.

HI I don't know if this is help but I did find this
[http://www.phoronix.com/scan.php?page=category&item=Graphics](http://www.phoronix.com/scan.php?page=category&item=Graphics)

:confused:

---

### Post by kellemes on 2007-08-28
You need to install the fglrx-driver to get optimal performance..
fglrx and XGL is what you need..

Just posting some links here..
[http://ubuntuforums.org/showthread.php?t=515573]("http://ubuntuforums.org/showthread.php?t=515573")
[http://ubuntuforums.org/showthread.php?t=511166]("http://ubuntuforums.org/showthread.php?t=511166")

---

