---
title: "Compiz and Desklets on XFCE"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Treeroot on 2007-01-29
I am brand new to linux and xfce, and have nearly no programing skills. 

I am using a twinview setup with an Nvidia Quadro fx 500 128 card. And have configured xgl. But in xgl I run compiz settings manager, and get a Dbus error that says "Dbus failed to load; compiz is not running. The dbus plugin cannot be activated unless compiz is runing." I think I have compiz running, I have the taskbar icon and gl desktop enabled. Any idea what is causing my problems?

Also, I was hoping for some help on gdesklets, as I have it installed, though when I try to run it, nothing happens.  Thanks for the help, this looks like a great support environment.

---

### Post by Fasga on 2007-01-29
If it's anything like Beryl, the taskbar icon is beryl-manager.  Beryl-manager doesn't start Beryl.  Try right clicking the task bar icon and checking if there is any option to 'start' or 'select' compiz.  

Also, I don't think you need XGL if you're running an NVidia card.

---

### Post by Treeroot on 2007-01-29
Yes, when I right click it allows me to enable GL desktop, which I have enabled.
XGL is not necessary, though it doesn't work in Xfce sessions either.
Will beryl run in Xfce?

---

### Post by Skidlz on 2007-01-29
Yes xfce works with beryl.

example [http://ubuntuforums.org/gallery/showphoto.php/photo/4798/cat/4](http://ubuntuforums.org/gallery/showphoto.php/photo/4798/cat/4)

Not my SS so thanks to orlfman

---

### Post by Treeroot on 2007-01-29
I can't get beryl to work either
It says that 

"Another window manager is alread running on screen: 0
No manageable screens found on display :0.0

any help?

---

### Post by primarycircle on 2007-12-10
If using XFCE4, follow these steps.

Open a terminal (gnome-terminal, xterm, eterm)
Use the following commands exactly:

touch start-compiz
nano start-compiz

(while in nano type)

#!/bin/bash
compiz --replace &&
emerald --replace

[ctrl-o] [ctrl-x]

while in terminal type:

sudo chmod +x start-compiz

In the XFCE menu, go to Settings -> Autostarted Applications
Click Add, give it a name, description, command -> browse for the start-compiz file

Make sure it is checked to start when XFCE starts, then you should be all set.

Hope this helps.  Sorry its months later.

Enjoi.

---

