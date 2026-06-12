---
title: "xserver-xorg-input-joystick and mouse/joystick speed"
date: 2010-07-16
forum: Assistive Technology &amp; Accessibility
---

### Post by emmdarakis on 2010-07-16
Hello there,

I am trying to use xserver-xorg-input-joystick to control the mouse cursor (my sister is unable to use a mouse or keyboard) in ubuntu lucid lynx using a usb joystick. 

I installed xserver-xorg-input-joystick as described here 
[http://ubuntuforums.org/showthread.php?t=516709](http://ubuntuforums.org/showthread.php?t=516709)

Now I can move the cursor but the speed that the cursor moves is too high.

I spent several hours trying to configure the speed (and button assignments) of both the mouse and the joystick using xorg.conf as described in that thread with no success. 

Then I fount that recently ubuntu have been using HAL instead of xorg.conf to configure such things. I tried configuring it using fdi files etc (as described for example in [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)) again with no success (not even the mouse can be controlled like this in my case). 
 
Yesterday I fount that in ubuntu 10.04 one can use the command xinput ([http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)) to control mouse speed and it works (for the mouse only). 

Still though when I use the joystick, the cursor is too fast. 

Is there a proper or at least working way to control the cursor speed when xserver-xorg-input-joystick is used in ubuntu 10.04???

I have also tried qjoypad but it won't install in 10.04 (64 bits). It requires Qt 4.2 or higher, I have 4.4 and the ./config stops with the message "Error: you need at least Qt version 4.2 to use this program". 

Any help appreciated.

Thanks a lot in advance...

---

