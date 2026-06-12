---
title: "exiting X server issues"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-01
I am told to exit X server before updating my video driver but after i exit the X server i can't to anything.  i type in a command and then press enter but that just moves the underscore to the next line.  Am i doning something wrong or missing something?

---

### Post by MobiusNZ on 2007-10-01
You generally shouldn't need to quit out of X to update your video card with Feisty... you can do it graphically then you just restart.

---

### Post by RyanZec on 2007-10-01
Well nvidia says otherwize, there message when i try to install

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

and after i exit X server i can run any command unless i am doing it wrong.

---

### Post by MobiusNZ on 2007-10-01
OK, well

1) Looks like you're install the nvidia drivers the *hard way*. In Ubuntu, go to your Restricted Drivers Manager and select the nvidia driver. That will download, install and configure it for you automagically. All you'll have to do is restart once its done. 

If you use Kubuntu, open Konsole and type ```
sudo aptitude install nvidia-glx-new
```
Once thats installed, go into System Settings-> Monitor & Display -> Hardware, and change the properties for graphics card to proprietary.

2)If you really want to do it with the standard nvidia binary (and have to do it every time you want to update) to exit the X server, log out of KDE/Gnome. Press Alt-F1 and login with the text screen there. Type ```
sudo init 3
``` to kill off X. Once you're done, you can either restart or sudo init 5

---

### Post by RyanZec on 2007-10-01
Thanks for the advice, did not know about the other easier way.  Still learn Ubuntu but like it so far,

---

