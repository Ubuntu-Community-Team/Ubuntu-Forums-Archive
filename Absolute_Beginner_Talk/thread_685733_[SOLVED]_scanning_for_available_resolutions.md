---
title: "[SOLVED] scanning for available resolutions"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-02-02
Is there a way to scan an external monitor for available resolutions?
I have an LCD TV that I use for an external monitor, it's native resolution according to online info is 1280x768, but it won't accept 1280x768 as an acceptable mode. I heard that some manufacturers, will limit the PC resolution of their TVs, presumabley to coax you into buying an LCD "monitor" as opposed to using an LCD "TV" I guess.

I've run xrandr, and I get this list of resolutions below. The problem is that it's a 16:9 aspect ratio monitor, and the 2 higher resolutions leave 3-4 inches of my desktop visible when I set the video player into fullscreen mode. It's really annoying. 

jeezus@MacWheezy:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected (normal left inverted right)
   1280x1024      59.9  
   1280x960       59.9  
   800x600        56.2  
   640x480        60.0  
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

---

### Post by bwhite82 on 2008-02-02
If you've booted with the external monitor attached already, you can check your 'Xorg.0.log' (/var/log/Xorg.0.log) for lines like the following:

> (II) fglrx(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0

In my case, my monitor is capable of a max resolution of 1280x800

---

### Post by Jeezus on 2008-02-03
Thanks!
 The next time I reboot, I'll leave the monitor plugged in and check the log again.

---

