---
title: "system is up to date ???!!!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by ZoRRoCanCer on 2008-04-19
Dear fellow
   I have successfully upgraded to Ubuntu 7.10, I know that 8.04 is on its way.
   During the installation procedure ubuntu had to connect to internet, but unfortunately at that time my LAN was not configured and dialog box said that you should update ubuntu after installation from Update Manager. I did as I finished installation,
Update Manager say that " Your system is up to date" when i click on "check" button then it just load 6 files and does not show any update. I want you to tell me. Is this behavior is normal?
Second is, whenever i try to install any program using Add/remove program from Application menu it show a dialog box which say
"The list of applications is not available"
"click on reload button to load it. to reload you need a working internet connection"

but my internet is working fine. Please help me

---

### Post by Helios38 on 2008-04-19
open terminal and type:



```
sudo apt-get update
```



try looking 4 updates again.

---

### Post by forestpixie on 2008-04-19
Probabley need to enable sources - open software sources - in System > Admin - put ticks in all except sources and disable cd-rom - if you want also in 3rd party tab - enable partner sources. Close and it will reload - then check for updates again

---

