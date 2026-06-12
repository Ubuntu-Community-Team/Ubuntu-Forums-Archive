---
title: "error message in  GUI"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by aad1925 on 2007-06-27
theres an error message in the screen appearing after  i type the **startx** command... the error message is  Xsession: unable start X session --- no "root/x.session" file, no "/root/.Xsession"  file, no session managers, no window managers, and no terminal emulators found; aborting.  please help me to configure this error ... thank you

---

### Post by drwho_cn on 2007-06-27
Did you modify the /etc/X11/xorg.conf ?

---

### Post by hvc123 on 2007-06-27
i take it you installed the ubuntu server?  when i installed server version you do not get a gdm,kdm or wm 

if you want kde 

type in 

sudo apt-get install kubuntu-dekstop
if you want gnome 

sudo apt-get install ubuntu-desktop

---

