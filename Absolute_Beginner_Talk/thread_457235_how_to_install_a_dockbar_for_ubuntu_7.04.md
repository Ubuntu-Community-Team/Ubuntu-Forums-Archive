---
title: "how to install a dockbar for ubuntu 7.04?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-28
hi
thank you for reading my post
is there any way to install a dockbar like

kxdocker or engage or something similar in ubuntu using its  apt-get application?
I tried and it returned 

```

sudo apt-get install Engage
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Engage


```

thanks

---

### Post by benanzo on 2007-05-28
I might be wrong, but I think the Engage dock is specific to the Enlightenment desktop.  If you want a good OS X-like dock, have a look at [*Avant Window Navigator*]("http://awn.wetpaint.com/?t=anon").

They have [good instructions]("http://awn.wetpaint.com/page/Ubuntu") for installing in Ubuntu

---

### Post by airtonix on 2007-05-31
yep avant is my favourite so far. heres why : 

**engage**
 [+] looks nice
  [-] but it only works with enlightenment, might be possible to hack it with gnome...who knows

[B]kiba
[/B] [+] again looks nice, you can make it small 
 [+] this does laucher & notification & window control from the same icon.
[+] works with beryl genie animation, end&start point is the actual icon in the bar
[+] optional autohide
  [-] heavy on cpu
   [-] could not at first get new items on the bar via drag n drop of .desktop items. 
 [-] crashes randomly when i click a control widget. some times when launching items.
[B]
awn[/B]
[+] can drag n drop .desktop items easily first go. 
[+] is lite on cpu usage, icons are launchers & notifications & window control...
[+] works with beryl genie animation, end&start point is the actual icon in the bar
[+] optional autohide
[+] mousing over them (with beryl) shows a thumbnail of said prog. 
[+] drag n drop files onto prog icon will launch prog with that file, ie open it.
[=]  the launcher editor is good but the icon picker needs to use the same one in nautilus file properties dialouge box. this enables dragNdrop of icons onto the chooser button.
[-]  cant resize the dock height nor make it stretch to full width.
[-] crashes randomly when i click a control widget. some times when launching items.

---

### Post by Inxsible on 2007-05-31
**KoolDock**
[+] Looks nice
[+] can drag n drop .desktop items easily first go. 
[+] has launchers and tracks open windows
[+] works with beryl genie animation, end&start point is the actual icon in the bar
[+] optional autohide
[+] mousing over them increases size of the icon like OSX. 
[+] drag n drop files onto prog icon will launch prog with that file, ie open it. (i think)
 
[-] crashes randomly when i click a control widget. some times when launching items. sometimes even while hovering over the dock :(
[-] Have to download and install a bunch of KDE libraries -- if you are using Gnome
 
 
Note: I plagiarised the above posters pros and cons format :)

---

### Post by Inxsible on 2007-05-31
> **legolas_w said:**
> hi
thank you for reading my post
is there any way to install a dockbar like
 
kxdocker or engage or something similar in ubuntu using its apt-get application?
I tried and it returned 
 
```

sudo apt-get install Engage
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Engage
 

```
 
thanks
 
the package name might be engage as opposed to Engage. Notice the lowercase 'e'. Linux is case sensitive !

---

### Post by legolas_w on 2007-05-31
> **airtonix said:**
> yep avant is my favourite so far. heres why : 

**engage**
 [+] looks nice
  [-] but it only works with enlightenment, might be possible to hack it with gnome...who knows

[B]kiba
[/B] [+] again looks nice, you can make it small 
 [+] this does laucher & notification & window control from the same icon.
[+] works with beryl genie animation, end&start point is the actual icon in the bar
[+] optional autohide
  [-] heavy on cpu
   [-] could not at first get new items on the bar via drag n drop of .desktop items. 
 [-] crashes randomly when i click a control widget. some times when launching items.
[B]
awn[/B]
[+] can drag n drop .desktop items easily first go. 
[+] is lite on cpu usage, icons are launchers & notifications & window control...
[+] works with beryl genie animation, end&start point is the actual icon in the bar
[+] optional autohide
[+] mousing over them (with beryl) shows a thumbnail of said prog. 
[+] drag n drop files onto prog icon will launch prog with that file, ie open it.
[=]  the launcher editor is good but the icon picker needs to use the same one in nautilus file properties dialouge box. this enables dragNdrop of icons onto the chooser button.
[-]  cant resize the dock height nor make it stretch to full width.
[-] crashes randomly when i click a control widget. some times when launching items.



Can you please let me know which one you find better after all your expertiences?
and how i can install them?

Thanks

---

### Post by Inxsible on 2007-05-31
```
sudo aptitude install kooldock
```

---

### Post by nevin on 2007-06-19
you have to add engage's repos.  dont know what they are but you can find them if you google it.

---

