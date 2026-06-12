---
title: "Can't change resolution in KDE"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Konsolkongen on 2006-06-27
Hi. yesterday i installed KDE, (apt-get install kde) and today i rebooted my computer and startet it up in KDE. It asked me how i would like it to behave (WIN, MAC, KDE and anotherone), so i just picked KDE.

The resolution is 1280 x 1024 @ 60hz. Not very nice to look at. I want to change this to 1024 x 768 @ 85hz. But how do i do that?

A few months back i also had KDE installed, and back then i chosed WIN and just had to right-click on the desktop to change resolution.

So, how do i change KDE to act like windows? Or can i remove all of KDE and just try again?

I've searched for something similar to this, but couldent find anything.

Thank you.

---

### Post by shoot2kill on 2006-06-27
if you have got to your settings and no other res is possible post your xorg.conf details here
> gedit /etc/X11/xorg.conf

else, change in display settings

---

### Post by nalmeth on 2006-06-27
Click the kmenu, go to System Settings, go to Display.
If for whatever reason you can't find it there, click Run Command

systemsettings

---

### Post by Konsolkongen on 2006-06-27
There is no Display option in the Kmenu :/

---

### Post by shoot2kill on 2006-06-27
> Click the kmenu, go to System Settings, go to Display.
If for whatever reason you can't find it there, click Run Command

systemsettings

then open the terminsl and type
> systemsettings

---

### Post by Konsolkongen on 2006-06-27
Nothing happens.

> systemsettings: command not found


---

### Post by Konsolkongen on 2006-06-28
Is there a way to completly remove KDE, and delete all settings? Then i could just install it again.

---

### Post by shoot2kill on 2006-06-28
[QUOTE=Konsolkongen]Is there a way to completly remove KDE, and delete all settings? Then i could just install it again.[/QUOTE]

NOT TRIED IT (not at my ubuntu machine), BUT IM SURE        

```
sudo apt-get remove kde-desktop
```

will work.. then to re-install it

```
sudo apt-get install kde-desktop
```

or, aptitude, depending on what you used to install it in the first place

[COLOR="Red"]**NOTE: i cant remember if the code is "KDE" or "KUBUNTU"......**[/COLOR]

---

### Post by user1397 on 2006-06-28
okay, first of all, just look around in kmenu > system or settings or something to change the resolution, you don't have to be so drastic as reinstalling all of kde.
btw, how did you install kde?  did you use apt-get, synaptic, or aptitude?

and btw shoot2kill, there's 2 things wrong with **sudo apt-get remove kde-desktop**
first of all, the package is kubuntu-desktop, so you were almost right.  also, that code wouldn't remove kde at all, it would just remove the kubuntu-desktop metapackage, a "pointer" or a package that points to many other programs.  so therefore, you would remove nothing.  it's the same thing as using synaptic, cause synaptic is just a graphical front-end of apt-get.  

the best way to install/remove kde, is to follow my guide in my sig.

---

### Post by Konsolkongen on 2006-06-29
Last time i had KDE installed i could change resolution in the Kmenu, yes. But this time the option is not there.

I'm running Ubuntu 6.06 and i'm using Gnome atm. I used apt-get to install KDE.

---

### Post by Konsolkongen on 2006-06-29
[QUOTE=erik1397]
the best way to install/remove kde, is to follow my guide in my sig.[/QUOTE]

Yes. Thats seems to work. 

I will try to install KDE using aptitude now. Thank you.

---

