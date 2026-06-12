---
title: "Brown Screen but no desktop?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-03-22
So today i booted into my ubuntu desktop, and i got just a standard brown screen, it went to the loading screen, showed loading nautilus and then boom just the standard brown screen. i cut x and reinstalled gdm but to no avail. The weird thing is i can get my process list up and it shows gdm is running but i can't interact with the desktop because it's not there. I've considered jsut moving my files over to windows and re-installing but i'm hoping it won't come to that :(.. Any advice?

---

### Post by arkangel on 2007-03-22
when login in session menu  chose fail safe , you will have an xterm 
in there type 

#gnome-session 

and post the output

---

### Post by rj686 on 2007-03-22
I couldn't figure out how to copy and paste from terminal so here is some of the stuff it spit out

```
SESSION_MANAGER=local/deafboy-laptop:/tmp/.ICE-unix/5080
Gnome-Message: gnome_execute_async_with_env_fds: returing -1
libnotify-Message: Unable to get session bus: Unable to determine address of the message bus (try 'man dbus-launch' and 'man dbus-deamon' for help)
Xlib: extension "XFree86-DRI" missing on display ":0.0"

```

---

### Post by cowlip on 2007-03-22
can you try this?

sudo rm -rf /tmp/.ICE-unix

---

### Post by rj686 on 2007-03-23
i get the same error again :(

---

### Post by arkangel on 2007-03-24
I googled for your error,  and many people had this problem when installing either gl or beryl or just doing an update  , 

try installing the drivers again

# apt-get search  "nvidia" or  "fglrx" (depends on which card you have ) and then 
#apt-get install  ("your suitable driver")
  also if you have a copy of your old  xorg.conf  replace the  new one, do a bk 

if you can try installing another Wiwdows manager , xfce (apt-get install xfce ) for example , so we can isolate  the error , and see if  the problem is gnome , xorg , or  smth else

---

### Post by rj686 on 2007-03-24
I thought it might be that too, until i changed to the vesa driver and still had the same issue, since feisty is in beta i figured i'd just do a re-install =). But thanks for the help dude.

---

