---
title: "Problem saving xorg.conf"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by r5gtt2k3 on 2007-11-29
Trying to save my Nvidia settings to dual screen so everytime i restart my pooter it keeps the same settings, but on the Nvidia control panel when i click the save an error box appears with 

"Unable to create new X config backup file 
'/etc/X11/xorg.conf.backup'

Is there anything i can do ?


Thanks

---

### Post by Belyel on 2007-11-29
Yep, make sure if you want to save your xorg.conf that you are running the nvidia-settings manager as root.

you can do this by typing "alt+f2" to get the run dialog, then run the program "gksu nvidia-settings" (maybe nvidia-setting), without quotes.  It will ask your password, then when you click save xorg.conf it should do so.  

Another way that I've done it is to show the xorg changes that it is makign then just copy/paste them manually into the xorg.conf using "gksu gedit /etc/X11/xorg.conf".

---

### Post by civic_si on 2007-11-29
Try opening the Nvidia program from a command line as root and see if that fixes it. It sounds like its run with you user not root.

---

### Post by r5gtt2k3 on 2007-11-29
> **Belyel said:**
> 

you can do this by typing "alt+f2" to get the run dialog, then run the program "gksu nvidia-settings" (maybe nvidia-setting), without quotes.  It will ask your password, then when you click save xorg.conf it should do so.  



Thanks, that has done the trick :) 

Im also getting sticky pages, Like when i have closed them, parts of them are sticking to the desktop but they are actually not there, Whats that all about ? 

and is there an option to like "refresh" my desktop ?

---

### Post by civic_si on 2007-11-29
F5 will refresh the desktop.

---

### Post by r5gtt2k3 on 2007-11-29
Thanks, thats not sorting it though :S 

Seems like its all distorted at the top of my screen

---

