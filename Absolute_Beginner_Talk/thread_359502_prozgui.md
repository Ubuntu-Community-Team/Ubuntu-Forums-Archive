---
title: "prozgui"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by sulekha on 2007-02-12
Hi all,

 I have downloaded  prozgui_2.0.5betaa-3_i386.deb  
  from here:[http://crypto.riken.go.jp/archives/linux/debian/debian/pool/main/p/prozgui/](http://crypto.riken.go.jp/archives/linux/debian/debian/pool/main/p/prozgui/)   before that i installed all the 3 libfltk packages via synaptic.

 then when i tried  to install i am getting the following errors (via gdebi)
  1) Error dependency not satisfiable: libftk1.1c102
  
my question is what should i do to make it install

---

### Post by kerry_s on 2007-02-12
You could use the regular prozilla, i'm using it in xubuntu-edgy just install and create the launcher->

command:
xterm -T "Prozilla" -e dproz
or
gnome-terminal -T "Prozilla" -e dproz

Then you just use copy link location in firefox and middle click to paste it in prozilla.

---

### Post by sulekha on 2007-02-12
Hi,
      I downloaded prozilla deb package from here  [http://yaro.gdi.pl/deb/dapper/](http://yaro.gdi.pl/deb/dapper/) and installed it.
      then i tried this xterm -T "Prozilla" -e dproz and getting the following message
 
      Warning: locale not supported by Xlib, locale set to C

    when i tried this gnome-terminal -T "Prozilla" -e dproz  i am getting the following messages

    (gnome-terminal:6634): Gdk-WARNING **: locale not supported by Xlib
   (gnome-terminal:6634): Gdk-WARNING **: cannot set locale modifiers
   Invalid argument: "Prozilla"

 now my question is how to fix this???

---

### Post by kerry_s on 2007-02-12
Try this one-> [http://security.debian.org/debian-security/pool/updates/main/p/prozilla/prozilla_1.3.6-3woody3_i386.deb](http://security.debian.org/debian-security/pool/updates/main/p/prozilla/prozilla_1.3.6-3woody3_i386.deb)

---

