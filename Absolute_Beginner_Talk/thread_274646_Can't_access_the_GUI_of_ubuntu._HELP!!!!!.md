---
title: "Can't access the GUI of ubuntu. HELP!!!!!"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Lameboy on 2006-10-10
I'm trying to abtain the desktop GUI of ubuntu.
I downloaded the ubuntu server 6.06 ISO, and installed it.
As a beginner i din't know the i was going to get terminal everytime i start up. I want to get to the GUI. I tried typing in [COLOR="red"]"apt-get install-desktop"[/COLOR] and [COLOR="red"]"apt-get install x-window-system-core xserver-xorg gnome-desktop-environment"[/COLOR] but each time it shows me [COLOR="Red"]"E: Couldn't find package ubuntu-desktop"[/COLOR]
What must i do? I'm logged in as [COLOR="red"]root@ubuntu:"#[/COLOR]

Please forgive me if all this sound dumb, but this is my first time using linux. ](*,)

---

### Post by xrchris on 2006-10-10
Did you want to have the server or standard desktop installation? If its the latter just reinstalling the desktop version would probably be a lot simpler.  

All depends what your end goal is i suppose.

---

### Post by gosh on 2006-10-10
> **Lameboy said:**
> I'm trying to abtain the desktop GUI of ubuntu.
I downloaded the ubuntu server 6.06 ISO, and installed it.
As a beginner i din't know the i was going to get terminal everytime i start up. I want to get to the GUI. I tried typing in [COLOR=red]"apt-get install-desktop"[/COLOR] and [COLOR=red]"apt-get install x-window-system-core xserver-xorg gnome-desktop-environment"[/COLOR] but each time it shows me [COLOR=Red]"E: Couldn't find package ubuntu-desktop"[/COLOR]
What must i do? I'm logged in as [COLOR=red]root@ubuntu:"#[/COLOR]

Please forgive me if all this sound dumb, but this is my first time using linux. ](*,)

Does
```
startx
```
not work?


For reinstalling the ubuntu-desktop use:
```
sudo aptitude ubuntu-desktop
```

If things still not work try:
```
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm
```

then
```
startx
```

---

### Post by Lameboy on 2006-10-10
I want to use the server ubuntu.
When i type "startx" i get "-bash: "startx: command not found


If i try to run "sudo apt-get install ubuntu-desktop" it gives me "-bash: sudu: command not found" 

Say if i type "apt-get install ubuntu-desktop" it says
Reading package lists...Done
Building dependency tree...Done
E: Couldn'd find package ubuntu-desktop

According to this ([http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)) it should work???


Someone please....:confused: :confused:

---

### Post by TheWizzard on 2006-10-10
it sounds like you downloaded the wrong (server) version of ubuntu.

the easiest is to download the correct version. you should be able to use it as a live cd with a nice graphical interface. 

see also: [https://help.ubuntu.com/ubuntu/desktopguide/C/get-ubuntu.html](https://help.ubuntu.com/ubuntu/desktopguide/C/get-ubuntu.html)

---

### Post by TheWizzard on 2006-10-10
why do you want to use the server version???
i would advice the server version only for professional with a lot of linux experience. 

if you just want to run an ftp-server or file-server for your home network you should use the desktop version of ubuntu.

---

### Post by salguod on 2006-10-10
I think the server version of Ubuntu comes with no graphical environment

---

### Post by Lameboy on 2006-10-10
I'm not shure if it's the incorrect version, its 432mb big and ubuntu 6.06.1 server-i386.

If i boot from the cd i get this [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06) window.

There must be a way, i'm shure.

I'll just try desktop version then i guess...:sad: 

Thx for all u'r help guys

---

### Post by Abstract on 2006-10-10
That is the wrong version. The Ubuntu Desktop is around 600MB and comes with a graphical enviroment.

---

### Post by TheWizzard on 2006-10-11
> **Lameboy said:**
> I'm not shure if it's the incorrect version, its 432mb big and ubuntu 6.06.1 server-i386.

If i boot from the cd i get this [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06) window.

There must be a way, i'm shure.

I'll just try desktop version then i guess...:sad: 

Thx for all u'r help guys

this is the server version. use the desktop version!

---

