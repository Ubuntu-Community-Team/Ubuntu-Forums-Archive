---
title: "Trouble installing kxdocker on GNOME"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2006-10-18
Basically when i try to ./compile i get the following message (preceded by loads of successful checks) :

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


Anyone know whats wrong?!

---

### Post by jordanmthomas on 2006-10-18
```
sudo aptitude install xorg-dev
```
should get you the X includes.

---

### Post by raqball on 2006-10-18
Try this 1st:

sudo aptitude install xorg-dev

Edit: See above post... I hunt and peck to darn slow (big fingers, little keys) 

:)

---

### Post by slibuntu on 2006-10-18
That worked great! But any ideas on this one??

checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!

???

---

### Post by jordanmthomas on 2006-10-18
```
sudo apt-get install build-essential xorg-dev qt3-apps-dev kdebase-dev kdelibs-dev automake
```

I'm pretty sure that's everything you'll need to build kxdocker.

---

### Post by magiceraser06 on 2006-11-17
when I got to make. i get all sorts of errors.  here are some of them.

eplugin_configurator.cpp:783: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:785: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_plugin_casella_add()':
xeplugin_configurator.cpp:798: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:800: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_del()':
xeplugin_configurator.cpp:813: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:815: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:815: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:816: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:819: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:822: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:824: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::plugins_selectionChanged(QListViewItem*)':
xeplugin_configurator.cpp:864: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:866: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:876: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:879: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:880: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:883: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:883: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:890: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:890: error: invalid use of undefined type 'struct 



NOt sure what that means.

---

### Post by jordanmthomas on 2006-11-17
[http://kde-apps.org/content/show.php?content=10958](http://kde-apps.org/content/show.php?content=10958)

What version did you download?
Apparently, the newest version corrects some compilation issue.

Also, unless you particularly want to build it yourself, try downloading the precompiled binary version.

---

### Post by magiceraser06 on 2006-11-17
I have the latest version installed. but I just can't run it.

Im a newbie to Linux.  i am fully upgraded to Edgy Eft.

I've literally gone through EVERY version of how to install kxdocker.  or even the GTK+ menu that someone recently released.

ANY help would be appreciated.  SOmething easy enough even for me to follow.

---

### Post by koshari on 2007-04-30
why dont you just use the repo version?

---

