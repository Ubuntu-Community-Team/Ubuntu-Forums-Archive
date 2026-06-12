---
title: "Installing software Icon's on the desktop"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Hellberg on 2006-11-17
Hi
I am newbee to linux and i have som things i'd like to know the answer to.

when I have installed som packages from a universe or a multiverse repositorie i can't see the icons for the program on the desktop, and I can't find them in programs either. i can see that the file is in user/bin along with all the other files, there were instalt with edgy. i've tryed to install a eletronic design software., and a few other packages. am I doing somthing wrong, or is XP just better for installig applications.
I realy like the way ubuntu look's and i hope i can be fammylier with it.

Sorry my poor english, i from Dk.

Mr. Bo

---

### Post by 23meg on 2006-11-17
If the executable for the package is in /usr/bin, you can create a desktop launcher by just entering the name of the executable alone in the "Command" box in the "Create Launcher" window. If the executable for the program *foo* is /usr/bin/foo, just type *foo*.

---

### Post by Hellberg on 2006-11-17
Thanks for the reply

I will try that. But is this the normal way to do, is it normal that when you install a package the icon for the program is in the usr/bin and not on the desktop, or is this thing package specific. or are any settings i can do.

Mr Bo

---

### Post by 23meg on 2006-11-17
It's not the icon that's in /usr/bin, it's the application's executable. /usr/bin is in your default path, which means that the system will look for anything you type as a command in a command line, the Alt+F2 run dialog or enter in the "Command" box in /usr/bin as well as any other location that's in the path. This is the normal and usual case. 

If your application doesn't add an icon to your menus, you can add one manually, create a desktop or panel shortcut, or just run it by entering the executable name.

---

