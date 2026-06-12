---
title: "Nvidia 7600 GT SLI Driver"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by xtreme35967 on 2007-04-02
I and a noobe to Ubuntu and I need your help. I tried to use Envy to install my driver but now i get a error that says that my xserver is not configured correctly. Plz help me. Also is there SLI support in Ubuntu?

---

### Post by Kobalt on 2007-04-03
When you boot your computer and get this error, press Ctrl+Alt+F1, log in with your username/password, then enter the following command line 
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions (leave default choice if you don't know), and then restart your computer. Now you should again have a graphical and working session (though it might not be the good resolution settings). After that I suggest you to install nVidia drivers this way : [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)
If your a beginner in Ubuntu/Linux you shouldn't try to install beta drivers, use Synaptic instead, it's much more safer and easier for driver updates. 

About SLI : it's possible, this way [http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html)

---

### Post by xtreme35967 on 2007-04-03
Thank You for the Help. I will try that when I get home.

---

