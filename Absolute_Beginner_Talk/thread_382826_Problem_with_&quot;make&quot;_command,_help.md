---
title: "Problem with &quot;make&quot; command, help"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-12
I have downloaded this program: [http://www.gnomefiles.org/app.php/GIB](http://www.gnomefiles.org/app.php/GIB) (There was another working link in the thread where it was brought up) and when I extract it to desktop and cd there, I enter "make" in terminal as instructed in the install text, and here's what I get:

```
bobby@bobby-ubuntu:~/Desktop/gib-0.2-src$ make
mcs  -target:exe -out:"gib.exe" -pkg:gtk-sharp -pkg:glade-sharp -r:System.dll ./src/Main.cs ./src/Gib.cs ./src/AssemblyInfo.cs ./src/Functions.cs ./src/Theme.cs ./src/Preferences.cs ./src/NewTheme.cs ./src/About.cs ./src/ThemeBrowser.cs ./src/EditCategories.cs \
        && mkdir build && mv "gib.exe" ./build/. && cp -r ./resources/* ./build/.
/bin/sh: mcs: not found
make: *** [gib.exe] Error 127
bobby@bobby-ubuntu:~/Desktop/gib-0.2-src$
```

I have the dependencies installed I know, please any ideas what is wrong?? I am using Ubuntu 6.10 with GNOME.

---

### Post by siciliancasanova on 2007-03-12
Hey stumbled across this and I've been on your last few topics so I know what you're attempting to do.  Have you thought about **Inkscape** at all?  I use it and you can make icons in it.

---

### Post by herbster on 2007-03-12
Hey bro, thanks for mentioning that I checked out the site, but what I want to do is really just take a set of icons that are already .png files and combine ones I dig into a icon theme I can choose for GNOME. I know GIB will let me do this but I can't get the damn thing past "make" !!! :mad:

---

### Post by hod139 on 2007-03-12
Install the package build-essential to get make, along with everything else required to build.

Edit:  I just visited the website and you will also have to install [FONT=Arial][SIZE=2]
 Mono
Gtk#
ImageMagick[/SIZE][/FONT]

---

### Post by Rui Pais on 2007-03-12
> **herbster said:**
> I have downloaded this program: [http://www.gnomefiles.org/app.php/GIB](http://www.gnomefiles.org/app.php/GIB) (There was another working link in the thread where it was brought up) and when I extract it to desktop and cd there, I enter "make" in terminal as instructed in the install text, and here's what I get:

```
bobby@bobby-ubuntu:~/Desktop/gib-0.2-src$ make
mcs  -target:exe -out:"gib.exe" -pkg:gtk-sharp -pkg:glade-sharp -r:System.dll ./src/Main.cs ./src/Gib.cs ./src/AssemblyInfo.cs ./src/Functions.cs ./src/Theme.cs ./src/Preferences.cs ./src/NewTheme.cs ./src/About.cs ./src/ThemeBrowser.cs ./src/EditCategories.cs \
        && mkdir build && mv "gib.exe" ./build/. && cp -r ./resources/* ./build/.
/bin/sh: mcs: not found
make: *** [gib.exe] Error 127
bobby@bobby-ubuntu:~/Desktop/gib-0.2-src$
```

I have the dependencies installed I know, please any ideas what is wrong?? I am using Ubuntu 6.10 with GNOME.
You don't seems to have all needed.
mcs is the mono compiler for c#. You need to have mono and gtk# installed and mcs on your path. 

Note that mono is a compiler not available through build-essential.

---

