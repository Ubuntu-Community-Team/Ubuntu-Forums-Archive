---
title: "having different wallpapers in workspaces"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by nootdog on 2005-07-30
Is there a way you can display different wallpapers for each of the 4 workspaces in the Ubuntu work environment??

---

### Post by UbuWu on 2005-07-30
With this application, you can:

[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

There are installation instructions on its webpage.

---

### Post by nootdog on 2005-07-30
cool thanks

---

### Post by sophtpaw on 2005-07-30
[QUOTE=nootdog]Is there a way you can display different wallpapers for each of the 4 workspaces in the Ubuntu work environment??[/QUOTE]

Good question, because in kde this was standard to be able to have a unique flavor for each workstation.

--
sophtpaw

---

### Post by sophtpaw on 2005-07-30
[QUOTE=UbuWu]With this application, you can:

[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

There are installation instructions on its webpage.[/QUOTE]


Great! how do i install in Ubuntu. The installation instructions are for Fedora. 

can i sudo dpkg -i ?

          or?


thank you


---
sophtpaw

---

### Post by sophtpaw on 2005-07-30
[QUOTE=nootdog]cool thanks[/QUOTE]


can you tell me how to install wallpapoz?

thx

sophtpaw

---

### Post by nootdog on 2005-07-30
still trying to figure it out lol. because I followed the directions on their website but I don't know exactly what I'm installing.  I don't understand what this is ..... 

Requirements: libglademm-2.4 and libxml++-2.10 ( See Dependencies section )

then when I click on one of these things it has a list of things to download.  I'm assuming that it is the different version of whatever u need but I don't know what it is and why I need it.  :?

---

### Post by bored2k on 2005-07-30
[QUOTE=nootdog]still trying to figure it out lol. because I followed the directions on their website but I don't know exactly what I'm installing.  I don't understand what this is ..... 

Requirements: libglademm-2.4 and libxml++-2.10 ( See Dependencies section )

then when I click on one of these things it has a list of things to download.  I'm assuming that it is the different version of whatever u need but I don't know what it is and why I need it.  :?[/QUOTE]
 libglademm-2.4-dev and libglademm-2.4-1 can be acquired through apt-get install.

---

### Post by bored2k on 2005-07-30
I will try to compile and build a debian package. Wish me luck. If anyone else does it first, be my guest. Nevermind. This uses a weird install.sh and  don't want to polute my drive just for this. I'm a black gb guy anyway.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=bored2k]I will try to compile and build a debian package. Wish me luck. If anyone else does it first, be my guest.[/QUOTE]


There has to be an easier way of doing it. Whereby Synaptic automatically finds the necessary dependencies instead of you running around installing things. Still if you figure out a way please let me know,

Good luck

sophtpaw

---

### Post by bored2k on 2005-07-30
[QUOTE=sophtpaw]There has to be an easier way of doing it. Whereby Synaptic automatically finds the necessary dependencies instead of you running around installing things. Still if you figure out a way please let me know,

Good luck

sophtpaw[/QUOTE]
 I just don't like the "install.sh". If I needed to "make install" instead it would be worth it. But I don't feel like compiling for nothing. The instructions are quite simple, but I just wanted the .deb, not to install it.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=bored2k]I just don't like the "install.sh". If I needed to "make install" instead it would be worth it. But I don't feel like compiling for nothing. The instructions are quite simple, but I just wanted the .deb, not to install it.[/QUOTE]

yes, i'm struggling with 'install.sh' too. I've emailed akbar at [email]akbarhome@gmail.com[/email] maybe he'll know, but maybe he doesn't. all his installation instructions are for Fedora. 

I'll keep you updated if i have a breakthrough!

g- nite,


sophtpaw

---

### Post by UbuWu on 2005-07-30
There are bugreports about this in gnome and ubuntu bugzilla:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=12120](https://bugzilla.ubuntu.com/show_bug.cgi?id=12120)
[http://bugzilla.gnome.org/show_bug.cgi?id=48004](http://bugzilla.gnome.org/show_bug.cgi?id=48004)

Hopefully this will get done sometime! (but the bug in gnome's bugzilla is more than 4 years old...)

---

