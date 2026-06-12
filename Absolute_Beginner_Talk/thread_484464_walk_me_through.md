---
title: "walk me through"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-25
Guys could you walk me though how to install wine?
please define this slang term synaptic; do you mean synaptic package manger? Use full words this is the new guy section.
Also could you recommend a screen recorder to me ?

---

### Post by cogadh on 2007-06-25
Run this in a terminal 
```
sudo apt-get install wine
```

---

### Post by RedRover1 on 2007-06-25
Here is a good link

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by BobCFC on 2007-06-25
Synaptic and apt-get are two sides of the same coin.   Programs for Ubuntu come packaged in .deb files because Ubuntu is child of Debian Linux.  

apt-get is a way of downloading and installing .deb files easily from the Ubuntu HQ by typing in a command such as the one above from cogadh.  This will download and install and sort out the mess for you.  You can also uninstall safely and upgrade etc.

Some people don't like to use the command line so the Synaptic Package Manager does the same thing but you can point and click with the mouse and it will do apt-get behind the scenes.  Another good thing about Synaptic is you can browse the descriptions and hit a nice search button to find the stuff you want.

---

### Post by Ssj3_man on 2007-06-25
> **RedRover1 said:**
> Here is a good link

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

thank you it worked
but they forgot to tell me to copy my windows application to usr/.wine/c_drive/system32  and their (Linux's) my computer needs an address bar

---

### Post by bodhi.zazen on 2007-06-25
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

The installation is easy. It is the configuration that, depending on the application, that is hard :twisted:

---

### Post by cogadh on 2007-06-25
You shouldn't need to copy any Windows apps to system32. If Wine complains that it can't find the app in system32, it is usually because you did not supply the appropriate path to the executable when you ran the wine command, so Wine defaults to looking in system32.

For example, if you have the executable on your desktop and you type "wine program_name.exe" in a terminal, Wine won't find the application and will immediately look in system32 for it. However, if you typed "wine /home/*username*/desktop/program_name.exe", the Windows app should launch normally.

---

