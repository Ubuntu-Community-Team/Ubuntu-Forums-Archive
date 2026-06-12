---
title: "I can NOT install Google Earth for Linux"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-06-13
Hello!

I am trying to install "Google Earth" to my Ubuntu Dapper v6.06.

I downloaded the ("Beta 4" version) ".bin" file from:

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

I then performed the following:

> root@dimitris-desktop:/home/dimitris/Desktop# chmod a+x GoogleEarthLinux.bin

root@dimitris-desktop:/home/dimitris/Desktop# sh GoogleEarthLinux.bin

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
You don't see to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...

What "X server" should I be running?

Any ideas?

Am I missing a package which I need to install?

Thanks.

---

### Post by thaddeusq on 2006-06-13
As a normal user I ran:
sh GoogleEarthLinux.bin
Trying to sudo didn't work for me.
Hope this helps.
ThaddeusQ

---

### Post by taurus on 2006-06-13
As the error message said, you are not running X so you can't install or run GoogleEarth!!!  When you boot Dapper, do you see a nice GUI (login screen) with a drum beat or do you just see a login prompt, waiting for you to log in?

---

### Post by rbalfour on 2006-06-13
```

xxxx@xxx:~/Desktop$ chmod +x GoogleEarthLinux.bin
xxxxxx@x:~/Desktop$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................

(setup.gtk2:8998): Gtk-WARNING **: Theme directory 96x96/action of theme HumanAzul2 has no size field

Installing mimetypes...
Running /usr/bin/update-mime-database /home/ddddd/.local/share/mime
***
* Updating MIME database in /home/gggggg/.local/share/mime...
Wrote 7 strings at 20 - fc
Wrote aliases at fc - 100
Wrote parents at 100 - 104
Wrote literal globs at 104 - 108
Wrote suffix globs at 108 - 260
Wrote full globs at 260 - 264
Wrote magic at 264 - 270
Wrote namespace list at 270 - 274
***
Installing desktop menu entries...
xxx@xxxxxx:~/Desktop$

```

No issues installing Google Earth.

---

### Post by ubernoob on 2006-06-13
X Server is the graphical stuff that Gnome and KDE is running in. You have to install Google Earth from inside one of them, and not from command line like Ctrl+Alt+F1

---

### Post by steve.horsley on 2006-06-13
I just installed with the following commands (from inside gnome-terminal):
> steve@StevesPC:~/Linux/downloads$ sudo su
Password:
root@StevesPC:/home/steve/Linux/downloads# chmod +x GoogleEarthLinux.bin
root@StevesPC:/home/steve/Linux/downloads# ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /root/.local/share/mime
***
* Updating MIME database in /root/.local/share/mime...
Wrote 2 strings at 20 - 6c
Wrote aliases at 6c - 70
Wrote parents at 70 - 74
Wrote literal globs at 74 - 78
Wrote suffix globs at 78 - d0
Wrote full globs at d0 - d4
Wrote magic at d4 - e0
Wrote namespace list at e0 - e4
***
Installing desktop menu entries...
root@StevesPC:/home/steve/Linux/downloads# exit
exit
steve@StevesPC:~/Linux/downloads$ googleearth


I have to say, it's extremely impressive.

---

### Post by dvarsam on 2006-06-14
[QUOTE=taurus]As the error message said, you are not running X so you can't install or run GoogleEarth!!!  When you boot Dapper, do you see a nice GUI (login screen) with a drum beat or do you just see a login prompt, waiting for you to log in?[/QUOTE]

Dear "taurus",

Thanks for your reply!

Yes, when I boot, I see a login Screen (& hear a drum beat sound) & do NOT have/see a "black screen" login prompt.

Awaiting for your instructions,

Thanks.

---

### Post by taurus on 2006-06-14
So, you hear the welcome sound but don't see the GUI screen!  Sounds like there is a problem with your video card.  Since you already at a console, terminal, you need to edit your /etc/X11/xorg.conf.  Type this at a prompt,
```

sudo nano /etc/X11/xorg.conf

```
Now, use the arrow keys and scroll down the the section about Device.  Change the "Driver to whatever it is now to "vesa" as
```

Driver           "vesa"

```
Save it and reboot.  Hopefully, X starts again and you can log in from there.  By the way, what video card do you have because you need to install the right driver for it once you get X working?

---

### Post by u.b.u.n.t.u on 2006-06-14
[QUOTE=dvarsam]Dear "taurus",

Thanks for your reply!

Yes, when I boot, I see a login Screen (& hear a drum beat sound) & do NOT have/see a "black screen" login prompt.

Awaiting for your instructions,

Thanks.[/QUOTE]

Please check my post here, as it might be useful:

[http://ubuntuforums.org/showthread.php?t=195930&page=2](http://ubuntuforums.org/showthread.php?t=195930&page=2)

Also I have tested Google Earth to the point where I see our Earth being zoomed in on.

---

### Post by taurus on 2006-06-14
[QUOTE=u.b.u.n.t.u]Please check my post here, as it might be useful:

[http://ubuntuforums.org/showthread.php?t=195930&page=2](http://ubuntuforums.org/showthread.php?t=195930&page=2)

Also I have tested Google Earth to the point where I see our Earth being zoomed in on.[/QUOTE]
You need to be in X first before you can install GoogleEarth so his problem right now is he can't log into Gnome/KDE/or whatever window manager on his machine...

---

### Post by u.b.u.n.t.u on 2006-06-14
Does Google Earth have sound? I hear nothing when it starts up but it seems to be working fine.

---

### Post by u.b.u.n.t.u on 2006-06-14
[QUOTE=taurus]You need to be in X first before you can install GoogleEarth so his problem right now is he can't log into Gnome/KDE/or whatever window manager on his machine...[/QUOTE]

Thanks.

Edit, there is a terminal command to instruct ubuntu to assess the graphics cards and monitor again, without a reinstall if "vesa" doesn't solve the problem.

---

### Post by RRS on 2006-06-14
Move the .bin file to /user/home if it's not already there and run "sh GoogleEarthLinux.bin" from the gnome terminal.

---

### Post by openmind on 2006-06-14
Uhh, Taurus, I'm not reading his reply like that, I think he's saying that he logs in using the GDM screen. (No "Black screen login/prompt).

'Course, I could be wrong, but re-read it just in case.

---

### Post by taurus on 2006-06-14
[QUOTE=u.b.u.n.t.u]Thanks.

Edit, there is a terminal command to instruct ubuntu to assess the graphics cards and monitor again, without a reinstall if "vesa" doesn't solve the problem.[/QUOTE]
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by dvarsam on 2006-06-14
Dear "openmind",

[QUOTE=openmind]Uhh, Taurus, I'm not reading his reply like that, I think he's saying that he logs in using the GDM screen. (No "Black screen login/prompt).
'Course, I could be wrong, but re-read it just in case.[/QUOTE]

I do NOT know what you are "all" talking about...

To clarify all things said:

When I boot my Ubuntu, I get the following screen:

A white/yellowish/brownish screen comes up which has a "user name" box in the middle of the screen...
At the bottom left I have a "choices" word (or options or whatever you want to call it...), which i can select...
At the bottom right, I have a "dimitris-desktop//Date displayed"...

Now, I do NOT know what the "above" is called...

But I _definately_ know that the screen is NOT black colored/filled with a prompt (ugly) sign, asking me (with this: ">"), to enter commands (e.g. like a Terminal prompt sign)...

Did this clarify what I have...?

Thanks.

---

### Post by taurus on 2006-06-14
[QUOTE=dvarsam]
When I boot my Ubuntu, I get the following screen:

A white/yellowish/brownish screen comes up which has a "user name" box in the middle of the screen...
[/QUOTE]
Then why not input your username and password to log into Gnome!  Don't have to click any lower left button!!!  Once you have logged into Gnome, then open a terminal and install GoogleEarthLinux.bin!!!  :rolleyes:

---

### Post by dvarsam on 2006-06-14
[QUOTE=taurus]Then why not input your username and password to log into Gnome!  Don't have to click any lower left button!!!  Once you have logged into Gnome, then open a terminal and install GoogleEarthLinux.bin!!!  :rolleyes:[/QUOTE]

That is what I did!!!!

That is what I did in the first place...:D 

Please go & read the _first_ post (my problem) in the First page of this thread!!!
:confused:

The program can NOT install, due to that "X" problem...???

"What do I do" _now_ is the question?

Thanks.

---

### Post by taurus on 2006-06-14
Show me the screenshot of your window manager, after you log in, then!!!

---

### Post by thaddeusq on 2006-06-14
Did you try installing using sudo?
Using sudo for me gave me the same error you were seeing. I had to install as the regular user.
Thad

---

### Post by dvarsam on 2006-06-14
Dear "thaddeusq",

[QUOTE=thaddeusq]
As a normal user I ran:

```
sh GoogleEarthLinux.bin
```

Trying to sudo didn't work for me.
Hope this helps.[/QUOTE]

YES!!!

You were right, man...

You _must_ be a normal user for this to work!!!

I finally solved this!!!

Thanks.

P.S.> Why does this matter, anyway?

---

### Post by Harleen on 2006-06-14
Because the current X display belongs to the logged in user. No other user is allowed to open windows on that display. Not even root. It would have worked if you used sudo, as sudo uses your user's environment variables.
To allow anyone (i.e. root) to draw on your display, you can type this:

```
xhost +
```
But be aware that this can cause some security risks, as really anyone can access your X-Server now, even from a remote machine.

---

### Post by Frank Golden on 2006-06-14
Hi All,
   Thanks for the great info. Google earth works great on my machine. Anyone know 
how to migrate my My Places from my XP install of Google Earth?

UPDATE:
Never mind I figured it out. Use File>open in Google Earth and browse to My Places.kml file.
In my case it was at /media/sda1/Documents and Settings/Frank Golden/Application Data/Google/GoogleEarth/my places.kml/  which is the path to the XP partition on my dual boot machine. You have to answer yes to dialog box asking if you want to save temporary places when you close the program to make "permanent". I think this is the first time Google earth made it this easy to migrate these favorites.
Ubuntu is almost perfect now!!!
Thanks

---

### Post by aysiu on 2006-06-14
I created a little quick-and-dirty installation of Google Earth, in case anyone's interested. I found that installing with *sudo* gave me some weird thing about not having permissions to a symlink. I found that installing with user installed it to my home directory (extra clutter--no thank you).

So this script downloads Google earth, runs the installer, moves the installation to /usr/local/bin and makes the menu entry universal.

To use the script, enter in the terminal: ```
gedit installge
``` or ```
kwrite installge
``` and paste in this code: ```
#!/bin/bash
cd
wget -c http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
rm googleearth
rm GoogleEarthLinux.bin
sudo chown -R root:root google-earth
sudo mv ~/google-earth /usr/local/bin/google-earth
sudo ln -s /usr/local/bin/google-earth/googleearth /usr/bin/googleearth
sudo cp /usr/local/bin/google-earth/googleearth.desktop /usr/share/applications/googleearth.desktop
``` Then type ```
chmod +x installge
./installge
``` Answer all the questions with the default (just keep clicking). The script will do the rest.

---

### Post by Frank Golden on 2006-06-15
Thanks aysiu worked like a charm. Question? Did you mean for command to be <gedit instalge> instead of 
<gedit installge>? For the KDE option you show <kwrite installge>. I noticed this before running script and changed
to <gedit installge>, worked just fine.
Again, thanks.

P.S. linked this thread to Scot's Newsletter (EveryThingLinux) forum.
Great stuff.

---

### Post by anakin_sk4jvoker on 2006-06-18
thanks for the script . very easy  :)

---

### Post by HokkaidoHillbilly on 2007-04-12
Hmmm...something didn't work right & now even though there's a menu listing for GE, there's no icon for it I get the following error:

Could not launch menu item:

Failed to execute child process "/home/benny/google-earth//googleearth" (No such file or directory)

Any ideas?

---

### Post by HokkaidoHillbilly on 2007-04-12
This is kinda far down in the pile and I'm the first post to this thread in a while, so...

BUMP ;)

---

### Post by bazzard on 2007-10-29
> **HokkaidoHillbilly said:**
> Hmmm...something didn't work right & now even though there's a menu listing for GE, there's no icon for it I get the following error:

Could not launch menu item:

Failed to execute child process "/home/benny/google-earth//googleearth" (No such file or directory)

Any ideas?

I have the same problem. I installed Google Earth with the Synaptic Package Manager but when I try to open it from the applications menu i get the same error message:

Could not launch menu item:

Failed to execute child process "googleearth" (No such file or directory)

If anyone could help me get google earth working, it would be much appreciated. Cheers.

UPDATE: uninstalled using SPM then used asyiu's method and installed google earth without a problem. Thanks very much.

---

