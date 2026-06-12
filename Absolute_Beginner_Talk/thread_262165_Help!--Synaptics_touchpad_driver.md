---
title: "Help!--Synaptics touchpad driver"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by mharris5 on 2006-09-21
I have tried to set a synaptic mouse functionality feature as shown on this webpage,

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

Bad idea! I went to restart the x-server and got this message,

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <YES> <NO>"

If anybody knows how to fix this please help. 

Thanks,

Matt

---

### Post by Brunellus on 2006-09-21
as a first step, at least to get xorg up and running again do this:

1) log in.  This will be the scary textmode login. Don't panic.  the password prompt, by the way, will not echo any characters--just type your password and hit ENTER.

2) execute

```

sudo dpkg-reconfigure xserver-xorg
```

3) follow the prompts.

4) reboot.   Your graphical user environment should now be working again.  Then we can see about getting your touchpad to work.

---

### Post by wjp.reg on 2006-09-21
ctrl-Alt-F1

sudo dpkg-reconfigure xserver-xorg

and follow the bouncing ball.. :)

---

### Post by mharris5 on 2006-09-21
Thanks, 
but for some reason I still get an error message. I've been through the menu's and after restarting my system it's still the same message.

---

### Post by mharris5 on 2006-09-21
Great, after playing with some of the settings it has worked. Thanks a lot! And as for the mouse settings, I think I'm going to read into and learn a bit more about both the software and the xserver setting before attempting anything again.

Thanks again, the help is greatly appreciated!

Matt

---

