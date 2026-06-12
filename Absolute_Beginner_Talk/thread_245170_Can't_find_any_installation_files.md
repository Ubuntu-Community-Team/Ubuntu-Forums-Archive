---
title: "Can't find any installation files"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by hepcecob on 2006-08-27
I have an inspiron 6400, finally found a simple guide that finally recognised my resolution.  Now my problem is that when I install programs through the synaptic package manager i have absolutely no idea where it installs them.  Theoretically, to my understanding, they're supposed to show up under applications and games (i installed several games that didn't show up).  The two programs I remember installing were Tux Racer, and Affiche (desktop sticky notes).  Also, when I say install i just mean I checked what i wanted downloaded and then hit apply, I thought that's what downloads and installs everything, if not please tell me.

Another thing I installed and would really like to see working is the 3ddesktop program (3rd from the top when you just start the package manager).  I also have no idea where it's installed.

---

### Post by Kobalt on 2006-08-27
Hi,

I have no idea of what is the 3D dektop program, so I can't help you on that one. But, for your insatllation stuf : you need to reload your Gnome panel to see your newly installed apps appear, sometimes. To do so, type in command line :
```
killall gnome-panel
```
If it still does not appear, press Alt+F2, then enter the name of the application you want to start. You can make yourself a launcher afterwards to place on your desktop with that command. 

Cheerios !

---

### Post by Ryan Marcus on 2006-08-27
Maybe I can help explain this a little better...

Judging by the fact that you have an inspiration notebook, I will assume you are used to Windows...

In Windows, when you download an application, you get the literal executable file. You can place this file anywhere, and then double click on it to run it or add it to the "Start" menu.

However, things are a little different in Linux, as far as I know. You don't download applications in the traditional sense... instead, you install various packages, which can be run from a shell, sometimes called a command line.

When you click on an item in the Applications menu, all you are really doing is running a command in the shell... For example, when you click on Firefox, it just executes the command "firefox" in the shell. Go ahead and try it. If you want, you can even run "firefox http://apple.com" to load the Apple web page.

You can use an application called "Alacarte" to edit your menu, or you can right click on your panel (at the top of your screen) to add new items to it. If the command for gnome-racer happened to just be "gnome-racer", you would add a custom application launcher to execute the command "gnome-racer".

Now, doing this can be a pain, because, as far as I can see, there is no way to figure out what packages have what commands.

It makes it much easier to not use Synaptic unless you are installing something PHP, and just use the Add / Remove application in your applications menu.

I hope I helped, and I hope I did not give you incorrect information...

---

