---
title: "ATI TV out and Control Panel + media"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Gru001 on 2007-03-04
Hey all,

I've been using Ubuntu for few days now and there are only few more things that I need to set up and I have replaced Windows :)

1. First, and most important for me is TV-Out capability. Ubuntu did detect my card which is ATI 8500 LE 128MB DDR and I do have 3d acceleration, however I do not have control panel nor the ability for TV out and I need that badly.

I have tried installing the drivers as specified on the following page:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I used method one. When I rebooted I just got a black screen, and couldn't do anything. I had to reinstall Ubuntu and lost all the info :(

I then tried the steps from the official Ubuntu help files and the same problem happened.

This was the page I followed the steps from:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

After following all of those steps, I did a verification and it didn't say ATI.

*If fglrxinfo gives you the following, your installation is not completed correctly:*

[I]$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/I]

I got something similar to that above...

Any ideas on what to do, will easyubuntu help?

That is all for now :lolflag: 

Thanks for any assistance you can provide! It is appreciated.

---

### Post by Gru001 on 2007-03-05
bump  :-\"

---

### Post by Kevf on 2007-03-10
Try using envy

[http://www.albertomilone.com/guides.html](http://www.albertomilone.com/guides.html)

First uninstall the drivers and then install the driver. Ubuntu will prompt you for an update after reboot.

---

