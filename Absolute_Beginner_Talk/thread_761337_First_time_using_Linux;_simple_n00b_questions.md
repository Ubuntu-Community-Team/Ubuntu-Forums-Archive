---
title: "First time using Linux; simple n00b questions"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by HyperHacker on 2008-04-21
I've been using Windows all my life, and I've got pretty good at it, but this is my first time really using Linux (Xubuntu 7.10). I've played with some Unix stuff before, and read a fair bit about it, and I've been coding in C/C++ for a while now (using gcc, even) so I'm pretty familiar with computers in general and can manage basic command line stuff. There's just a few things I'm not entirely clear on, and a bunch of Windows tricks I'm used to that don't seem to be present here.

First of all, window managers. I'm not entirely clear how this works. I've heard how X uses a client/server system, which lets you do neat things like run an X client on one machine and a server on the other. Am I correct in understanding that window managers such as Xfce, Fluxbox, Beryl etc are all X clients, and you're using the X server no matter which you use? Programs talk to the server to have their windows updated and it talks to the client to have those updates pushed to the screen?

Also, I was playing a bit with Fluxbox on the Gparted live CD and it seems really neat, but it doesn't have compositing, which I quite like. (I'm not a PC gamer, so as long as I have this nice fancy 3D card, I may as well use it for something. :p) Is there a window manager similar to Fluxbox but with compositing? I don't really care about all the fancy eye candy like being able to bend and stretch and warp things or having a spinning cube, but I'd love to be able to rotate my windows around at least the Z axis (3D space manipulation would be even nicer) and have hardware-accelerated translucency (if I don't already :p) and tinting (glColor).

Also, there are a number of shortcuts and tricks I use often in Windows, and I'd like to know if similar ones exist in Xfce/Xubuntu or if I can enable them. A few that come to mind are:
-Windows key to pop up the Applications menu.
-Win+R to pop up a "Run" dialog (or even a terminal) like I just now discovered Alt+F2 does
-Win+M to minimize all active windows
-Alt+numbers on the numpad to enter extended characters like é by number
-Ctrl+Alt+Delete to open the System Monitor
-MouseKeys; when Num Lock is off, the numpad moves the mouse (great for pixel-precise work).

I see in Keyboard Preferences there's a shortcut editor, but I can't seem to edit the shortcuts. Edit only lets me change the assigned command, and if I try to add a new one, I get told the command doesn't exist even if it's the same as one already assigned. O_o

Finally, how can I make Num Lock be enabled at startup?

---

### Post by natman on 2008-04-21
I can only answer some of your questions, to bring up a system monitor i just have a system Load/processor icons on my task bar full time way better than the windows ctrl+alt+del,, in gnome right click on the top bar and add to panel search for system monitor.
Also to enable the numlock is that not done in the bios menu somewhere?

---

### Post by Sbarton on 2008-04-21
Control+Alt+D = minimize windows
regards

---

### Post by nicedude on 2008-04-21
I am not 100% but I believe if you wanted eye candy effects then what I think is the superior desktop gui that you should be using is gnome that comes with ubuntu instead of using xcfe that comes with xubuntu. Others might argue that but I was under the impression that xubuntu shines when used on older equipment or if you really want super fast program startups and such on newer PC's, but this is due to less graphics stuff in the xcfe desktop while ubuntu uses the gnome desktop. So if you have a fast box and good 3D card you might want to rethink your choice before you go any farther as you might be more happy with that. I can just right click on my top or bottom toolbar and add buttons to do half the stuff you asked about and allot more. Gnome has gdesklets where you can add any of 100 or so desktop widgets to display or do various things. It is just going to take you awhile to get used to linux from windows just keep at and you will figure it out.

Yoda said it best  --  You must unlearn what you have learned. :-)

---

### Post by marufaberlin on 2008-04-21
Try installing compiz:
```

sudo apt-get install compiz
sudo apt-get install compiz-config-settings-manager
sudo apt-get install beryl*

```

then running compiz-config-settings-manager, along with other things you can set shortcuts with general settings.

---

### Post by FredB on 2008-04-21
No need to install beryl packages anymore. Beryl is a dead project, merged with compiz to produce compiz Fusion.

---

### Post by HyperHacker on 2008-04-21
> **natman said:**
> I can only answer some of your questions, to bring up a system monitor i just have a system Load/processor icons on my task bar full time way better than the windows ctrl+alt+del,, in gnome right click on the top bar and add to panel search for system monitor.I meant the task manager actually, I noticed it was called System Monitor in the menu. I've got those monitors on the bar already, quite nice to have.

I'll try Compiz later (up way too late right now :p). I do value performance far more than eye candy, but I figure if the GPU is doing all the window rendering, that's less work for the CPU, and a GeForce 6200 OC should have plenty of processing power to do rotation, blending and tinting, which (I would imagine) requires only a few extra microseconds of the CPU's time to call glRotate/etc to tell it to do that. :)

---

### Post by marufaberlin on 2008-04-22
Right, my knowlege seems to be out of date:
```

apt-get update
apt-get upgrade brain

```

:-D

---

### Post by Cifra on 2008-04-22
Just to make it clear:
You can see how the OS was built - when you log in it starts an X session with your Desktop Environment of Choice.

Now Fluxbox and Beryl are windows managers, but XFCE is a desktop environment.

---

### Post by RedSquirrel on 2008-04-22
> **HyperHacker said:**
> Also, there are a number of shortcuts and tricks I use often in Windows, and I'd like to know if similar ones exist in Xfce/Xubuntu or if I can enable them. A few that come to mind are:

...

-MouseKeys; when Num Lock is off, the numpad moves the mouse (great for pixel-precise work).

...

Finally, how can I make Num Lock be enabled at startup?


To use the mouse with the numpad, press **Ctrl+Shift+NumLock**. (Turn the feature off the same way.)

Select the "click mode" on the numpad:
**/** selects left-click
***** selects middle-click
**-** selects right-click

then press **5** to perform the click.

I use **numlockx** to enable NumLock at startup. It's in the repositories.

---

### Post by HyperHacker on 2008-04-22
Re: Num Lock, it is set to be on at boot in the BIOS, but it goes off again when GRUB starts. O_o (At least, I'm guessing it's GRUB; I didn't watch to see precisely when, but it's off when Windows starts too.)

RedSquirrel, thanks. :)

> **Cifra said:**
> Just to make it clear:
You can see how the OS was built - when you log in it starts an X session with your Desktop Environment of Choice.

Now Fluxbox and Beryl are windows managers, but XFCE is a desktop environment.What's the difference exactly?

---

