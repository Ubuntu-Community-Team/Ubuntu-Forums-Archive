---
title: "wine not working"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-17
I installed wine by following this site

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

Everything installed i can download an windows app.exe file to my linux desktop and double click and wine will install it..But if i try to start the app from the icon on the desktop nothing happens.. If i go to the command line and type wine /home/john/Desktop/window.exe  it says it it doesn't exsist? Any ideas? I'm sure it's gotta be a simple setting somewhere

---

### Post by Kilz on 2006-06-17
[QUOTE=lime4x4]I installed wine by following this site

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

Everything installed i can download an windows app.exe file to my linux desktop and double click and wine will install it..But if i try to start the app from the icon on the desktop nothing happens.. If i go to the command line and type wine /home/john/Desktop/window.exe  it says it it doesn't exsist? Any ideas? I'm sure it's gotta be a simple setting somewhere[/QUOTE]

The standard wine application will install applications to /home/username/.wine/Program Files/ApplicationName not to the desktop. What is usually placed on the desktop is a launcher. It may not setup correctly.
If you are using Gnome to see the .wine folder in /home/username you may have to click Edit then Preferences, then  check the box by "Show hidden and backup files" then click close, then close and reopen your home directory.
Even if the file is installed correctly by wine, there is no guarantee that it will launch or work correctly. Wine isn't perfect. It doesn't run 100% of windows programs, [check here]("http://appdb.winehq.org/") to see if the application you are running works with wine or if it needs special configuration. If the application is supported, you may have better luck using a [pre configured .deb package.]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb")

---

