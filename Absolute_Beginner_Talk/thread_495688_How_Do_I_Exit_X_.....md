---
title: "How Do I Exit X .... ????"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by RajivNair on 2007-07-08
Hello Everyone,

    I just happened to download the latest nvidia binary drivers from the nvidia site .. but however it needs me to completely exit all X services for it to be installed ... can anyone tell me as to whats the command to completely exit X ... ???

Thanks in advance,
Rajiv Nair

---

### Post by Sunforge on 2007-07-08
I could be wrong but try:
 
sudo /etc/init.d/gdm stop
 
This should kill of the desktop completely and leave you ready to do whatever you were planning on doing.
 
Remember to back up /etc/X11/xorg.conf just in case you make changes to the config as a result of loading the NVIDIA binary and then want to go back to where you were before.

---

### Post by diafanos on 2007-07-08
@ Sunforge

No, you are not wrong at all....

@Rajiv Nair
Just go to a virtual terminal (press Alt+Ctrl+F1)
login and write  (as Sunforge said) > sudo /etc/init.d/gdm stop
Install drivers and then to restart X server write: > sudo /etc/init.d/gdm start

---

### Post by RajivNair on 2007-07-08
thnx a lot people .. its all working good ... :)

---

