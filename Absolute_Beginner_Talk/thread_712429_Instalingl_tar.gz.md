---
title: "Instalingl tar.gz"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by GaryLittlemore on 2008-03-01
I've got the following file on my desktop, could someone please give me the terminal command to install it?

flock-1.1d.en-US.linux-i686.tar.gz

Thanks

---

### Post by TeoBigusGeekus on 2008-03-01
It is a compressed archive, something like a zip or a rar archive. Double click it and extract its contents anywhere you want.

---

### Post by herbster on 2008-03-01
Yup, a simple double-click will open it with the archive manager so you can browse its contents and extract it via GUI. If you want to use the terminal, navigate to where it is, let's say it's on your desktop:

```
cd Desktop
tar xzf flock-1.1d.en-US.linux-i686.tar.gz
```

---

### Post by GaryLittlemore on 2008-03-01
It's a tar.gz file which I believe to be compressed but I want to install it.

---

### Post by owbizi on 2008-03-01
Yup, but first you have to extract it, just like they said...

Depending of the program, you don't have even to install, just extract -> run.

---

### Post by TeoBigusGeekus on 2008-03-01
It cannot be installed unless it is decompressed first.

---

### Post by herbster on 2008-03-01
A tar is a compressed file, so look for a readme file in the archive after you uncompress it, the process depends on the program.

---

### Post by jken146 on 2008-03-01
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Oldsoldier2003 on 2008-03-01
> **herbster said:**
> Yup, a simple double-click will open it with the archive manager so you can browse its contents and extract it via GUI. If you want to use the terminal, navigate to where it is, let's say it's on your desktop:

```
cd Desktop
tar xzf flock-1.1d.en-US.linux-i686.tar.gz
```

then to start flock for the first time:
```

cd flock
./flock
```

it will ask you if you want to import settings etc, and you're off. in the future you won't need to launch a terminal to run flock.

---

### Post by coolbrook on 2008-03-01
For future reference

[https://help.ubuntu.com/7.10/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/7.10/add-applications/C/install-file.html#tarballs)

---

### Post by GaryLittlemore on 2008-03-01
I've got it uncompressed on my desktop now, in a folder called flock.

I can't see a readme file, what type of file am I looking for to install it?

---

### Post by Oldsoldier2003 on 2008-03-01
> **GaryLittlemore said:**
> I've got it uncompressed on my desktop now, in a folder called flock.

I can't see a readme file, what type of file am I looking for to install it?
like i said a couple posts ago


```
cd flock
./flock
```
and you'll be up and running

---

### Post by GaryLittlemore on 2008-03-01
I've done that, but how do I get it install so I can do Applications> Internet> Flock?

---

### Post by Oldsoldier2003 on 2008-03-01
> **GaryLittlemore said:**
> I've done that, but how do I get it install so I can do Applications> Internet> Flock?
you could make a launcher for it (thats the easiest way)
 or you could hack about and put it in your menus manually
I chose the easy way and just made a launcher on one of my panels

---

### Post by Oldsoldier2003 on 2008-03-01
ok found how to do it [here]("http://brentroos.com/2006/07/24/install-flock-on-ubuntu/"). you can change where you want the app to live by modifying the .desktop file to reflect where you want it to live.

sudo gedit /usr/share/applications/Flock.desktop

Add this to the new file:

[Desktop Entry]
Comment=Flock Web Browser
Exec=flock
GenericName=Flock Web Browser
Icon=/opt/flock/icons/mozicon128.png
Name=Flock
Path=
StartupNotify=true
Terminal=0
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=
Categories=Network;Application;

Finally, refresh the Gnome Panel:

killall gnome-panel

Or, if you are using Kubuntu:

dcop kicker Panel configure

---

### Post by PeterJS on 2008-03-01
You can also put local .desktop files in ~/.local/share/applications, no need to modify the system location and it's also cleaner in a multi-user environment having a user specific menu entry for an application installed in a user specific location. Even on single user system there's value in doing things the right way for the sake of doing things right.

---

### Post by Oldsoldier2003 on 2008-03-01
> **PeterJS said:**
> You can also put local .desktop files in ~/.local/share/applications, no need to modify the system location and it's also cleaner in a multi-user environment having a user specific menu entry for an application installed in a user specific location. Even on single user system there's value in doing things the right way for the sake of doing things right.

Point well taken, the directions I gave were pasted from the cited website. Personally I'd rather see flock delivered as a deb package that properly sets up the menus...

---

### Post by GaryLittlemore on 2008-03-02
> **Oldsoldier2003 said:**
> Point well taken, the directions I gave were pasted from the cited website. Personally I'd rather see flock delivered as a deb package that properly sets up the menus...

I too would like to see people to create .deb files. If they've gone to the effort of creating program, why don't they also create a .deb file making easier for people to install?

---

