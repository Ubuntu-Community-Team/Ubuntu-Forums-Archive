---
title: "Change wallpaper randomly"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-04-13
Hi,

1. Anybody familiar with a gui utility that can change my wallpaper randomally ?
2. I downloaded the ubuntu-calendar, have no idea how to run the app. ??

tnx,
Nir

---

### Post by xenmax on 2006-04-13
From description of ubuntu-calender, it looks like it has feature to just change your desktop wallpaper every month, where as i think you have in mind more like randomly changing wallpaper from a collection of pics you have? Did you read somewhere if ubuntu-calender can do that? i might also be interested in a feature like that

---

### Post by jimbz on 2006-04-13
Perhaps I'm wrong, but I think that ubuntu-calendar is just a *package* and not an application which provides a new wallpaper every month in the same place. And if you select "Ubuntu Calendar" in the wallpaper chooser, then it will change automatically as soon as you update (because the old one will be automatically overriden).

---

### Post by mostwanted on 2006-04-13
I guess you could always write a script to do the job if you looked a bit into what gconf setting or file to manipulate in order to change the wallpaper. You could then run this script in your own user session.

---

### Post by meatbites on 2006-04-13
Wallpaper Tray may be what you're after.

Download this .deb package:
[http://planetearthworm.com/projects/wp_tray/files/wp-tray_0.4.6-1_i386.deb](http://planetearthworm.com/projects/wp_tray/files/wp-tray_0.4.6-1_i386.deb)

Three dependencies to install:
```
sudo apt-get install libgcrypt1 libgnutls7 libtasn1-0
```

Install the main package:
```
sudo dpkg -i wp-tray_0.4.6-1_i386.deb
```

Having installed it, it's simply a matter of running it with the command:
```
wp_tray
```

You can also compile a newer version if you feel up to it. The main site is: [http://planetearthworm.com/projects/wp_tray/](http://planetearthworm.com/projects/wp_tray/)

You would want to make a launcher file for this (right-click desktop > Create Launcher > Command: wp_tray).

---

### Post by nir78 on 2006-04-13
[QUOTE=jimbz]Perhaps I'm wrong, but I think that ubuntu-calendar is just a *package* and not an application which provides a new wallpaper every month in the same place. And if you select "Ubuntu Calendar" in the wallpaper chooser, then it will change automatically as soon as you update (because the old one will be automatically overriden).[/QUOTE]

I cannot see a wallpaper like that...

---

### Post by nir78 on 2006-04-13
[QUOTE=meatbites]Wallpaper Tray may be what you're after.

Download this .deb package:
[http://planetearthworm.com/projects/wp_tray/files/wp-tray_0.4.6-1_i386.deb](http://planetearthworm.com/projects/wp_tray/files/wp-tray_0.4.6-1_i386.deb)

Three dependencies to install:
```
sudo apt-get install libgcrypt1 libgnutls7 libtasn1-0
```

Install the main package:
```
sudo dpkg -i wp-tray_0.4.6-1_i386.deb
```

Having installed it, it's simply a matter of running it with the command:
```
wp_tray
```

You can also compile a newer version if you feel up to it. The main site is: [http://planetearthworm.com/projects/wp_tray/](http://planetearthworm.com/projects/wp_tray/)

You would want to make a launcher file for this (right-click desktop > Create Launcher > Command: wp_tray).[/QUOTE]

I receive a message that I have no wallpapers and the prog. ends...
Any ideas ??

Nir

---

### Post by Sutekh on 2006-04-13
[QUOTE=nir78]I cannot see a wallpaper like that...[/QUOTE]
They are in /usr/share/backrounds.

---

### Post by meatbites on 2006-04-14
Nir:

Once the program is running, you need to right click on its tray icon and select 'Configure'. In there you can choose directories from which the program can cycle through wallpapers.

---

### Post by Mustard on 2006-04-14
I'm going to have a crack at compiling the 0.5.1 version from source to amuse myself. :)

---

### Post by aysiu on 2006-04-14
Use KDE.

---

### Post by nir78 on 2006-04-14
[QUOTE=meatbites]Nir:

Once the program is running, you need to right click on its tray icon and select 'Configure'. In there you can choose directories from which the program can cycle through wallpapers.[/QUOTE]

[QUOTE=Sutekh]They are in /usr/share/backrounds.[/QUOTE]

tnx,

both solutions worked great!

Nir

---

### Post by meatbites on 2006-04-14
Happy to hear!

And Aysiu -- touche. ;)

---

### Post by Mustard on 2006-04-14
Aaagh!  Bummer... I had a succesful compile of 0.5.1 and got all the way through to using checkinstall.  Checkinstall succesfully made the package and installed it, but I don't have the option to choose in when I try to add an applet. :)  Hehehe...well I got close anyway.  I've been hunting around for how the other applets work and where they store there files, but I haven't worked it out yet.

---

### Post by WrathofthePenguin on 2006-04-14
Here's how I did it:

[http://www.ubuntuforums.org/showthread.php?t=95434&highlight=change-bg](http://www.ubuntuforums.org/showthread.php?t=95434&highlight=change-bg)

---

### Post by meatbites on 2006-04-14
Wrath -- I've used that one myself too. I was going to link to it, but a utility with a GUI was specified.

I just recently saw a friend's Mac laptop. I was quite impressed with the background changer on it, as it also has a fade transition between the images. Does anyone know of an existing tool that does that under Linux?

---

### Post by MetalMusicAddict on 2006-04-14
[QUOTE=meatbites]Wrath -- I've used that one myself too. I was going to link to it, but a utility with a GUI was specified.

I just recently saw a friend's Mac laptop. I was quite impressed with the background changer on it, as it also has a fade transition between the images. Does anyone know of an existing tool that does that under Linux?[/QUOTE]
Its been suggested as a Compiz plug-in. :)

---

### Post by meatbites on 2006-04-14
[QUOTE=MetalMusicAddict]Its been suggested as a Compiz plug-in. :)[/QUOTE]

Oooer! That's brilliant news. :)

---

### Post by kditty on 2006-04-15
[QUOTE=aysiu]Use KDE.[/QUOTE]

you always have the simple solutions :D thanks.

---

### Post by true_friend on 2006-08-13
the script is working fine.
but whats about a gui like wallpaper tray.
i installed it but was not working prperly i could not configure it. then i found here
-----------------------
libgcrypt1 libgnutls7 libtasn1-0
----------------------
these three libraries should be installed. i have only first one which is also not satisfying next package it provides error that dependency is not satiscactory. while in synaptic last two are not available.
would some one guide me to add repositories for these libraris????????
i  therefor always ask for a built in small utiliy for background changing just like kde has.

---

### Post by RajivNair on 2006-08-19
People check this out:-

[http://www.gnomefiles.org/app.php/Desktop_Drapes](http://www.gnomefiles.org/app.php/Desktop_Drapes)

---

