---
title: "Multiple Window Managers"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by seabattle on 2007-08-31
I've installed Ubuntu from the alternative cd (no gnome/kde) and then installed fluxbox, I've been running this quite happily for a while with no login manager and logging in at a text prompt and typing startx if I need to run fluxbox. However, I've not installed FVWM and Blackbox and I cant figure out how to start these, I've tried to create and dot xinitrc file with a simple script but the startx and xinit commands dont seem to read arguments or obey them.

Where does Ubuntu attempt to start the window manager from? And does anyone have any suggestions about how to be able to make startx or xinit boot the WM I choose WITHOUT using GDM/KDM?

Cheers!

---

### Post by david_e on 2007-08-31
I don't know anything about FVWM and BlackBox, as I didn't tried them, but I suggest you to try [SLiM]("http://slim.berlios.de/") which is a lightweight graphical login manager, maybe you could find it more comfortable then the "startx" thing.

---

### Post by jombeewoof on 2007-08-31
Try this

```
update-alternatives --config x-window-manager
```

---

### Post by RedSquirrel on 2007-08-31
> **seabattle said:**
> I've installed Ubuntu from the alternative cd (no gnome/kde) and then installed fluxbox, I've been running this quite happily for a while with no login manager and logging in at a text prompt and typing startx if I need to run fluxbox. However, I've not installed FVWM and Blackbox and I cant figure out how to start these, I've tried to create and dot xinitrc file with a simple script but the startx and xinit commands dont seem to read arguments or obey them.

Where does Ubuntu attempt to start the window manager from? And does anyone have any suggestions about how to be able to make startx or xinit boot the WM I choose WITHOUT using GDM/KDM?

Cheers!

Hmm... I haven't had any problems using ~/.xinitrc and running startx.

If you were using your ~/.xinitrc to run Fluxbox, I assume you have made your ~/.xinitrc executable...

```
chmod +x ~/.xinitrc
```Are you using the correct command to start the other window managers in your ~/.xinitrc?

If you have installed fvwm and blackbox from the repositiories, try looking in /usr/share/xsessions for the "*.deskop" files which correspond to fvwm and blackbox.

Look in those files for the line:

```
Exec=path_to_executable
```and put

```
exec path_to_executable
```at the end of your ~/.xinitrc.

Feel free to post your ~/.xinitrc if it still doesn't work.


PS - Welcome to the forums! :)

---

### Post by seabattle on 2007-09-01
> **jombeewoof said:**
> Try this

```
update-alternatives --config x-window-manager
```

Cheers for this, I've created a bash alias to switch window managers as follows

```
sudo update-alternatives --config x-window-manager && startx
```

Which I can now run after I login when I want to switch window managers.



> **RedSquirrel said:**
> Hmm... I haven't had any problems using ~/.xinitrc and running startx.

If you were using your ~/.xinitrc to run Fluxbox, I assume you have made your ~/.xinitrc executable...

```
chmod +x ~/.xinitrc
```Are you using the correct command to start the other window managers in your ~/.xinitrc?

If you have installed fvwm and blackbox from the repositiories, try looking in /usr/share/xsessions for the "*.deskop" files which correspond to fvwm and blackbox.

Look in those files for the line:

```
Exec=path_to_executable
```and put

```
exec path_to_executable
```at the end of your ~/.xinitrc.

Feel free to post your ~/.xinitrc if it still doesn't work.


PS - Welcome to the forums! :)

I have made it executable and checked the paths but this still doesnt seem to get run when I run startx with any argument

```
#!/bin/sh

ARG=$1

DEFAULTWM="startfluxbox"

if [ ! $ARG]; then
  WM=$DEFAULTWM
fi

if [ $ARG="fluxbox" ]; then
   WM=startfluxbox
elif [ $ARG="blackbox" ]; then
   WM=blackox
else 
   WM=$DEFAULTWM
fi
exec $WM 

```

Cheers

---

### Post by RedSquirrel on 2007-09-01
> **seabattle said:**
> I have made it executable and checked the paths but this still doesnt seem to get run when I run startx with any argument

```
#!/bin/sh

ARG=$1

DEFAULTWM="startfluxbox"

if [ ! $ARG]; then
  WM=$DEFAULTWM
fi

if [ $ARG="fluxbox" ]; then
   WM=startfluxbox
elif [ $ARG="blackbox" ]; then
   WM=blackox
else 
   WM=$DEFAULTWM
fi
exec $WM 

```Cheers

Oh, I see now what you are trying to do. I don't think you can do that with startx. It has its own arguments, things like '-br' and so on.

My approach would be to create a separate script that sets up an appropriate .xinitrc file for a given window manager.

Create files such as .xinitrc_fluxbox, .xinitrc_icewm, .xinit_fvwm, etc., each with relevant contents, say, at the very least, the line 'exec *window_manager_executable*' at the bottom.

Then create a script like this:

```
#!/bin/sh

ARG=$1

case $ARG in
        "flux" )
        `cp -f /home/user/.xinitrc_fluxbox /home/user/.xinitrc`
        ;;
        "ice" )
        `cp -f /home/user/.xinitrc_icewm /home/user/.xinitrc`
        ;;
        * )
        echo
        echo "Not a valid option."
        echo
        exit 1
        ;;
esac

startx

exit 0
```This is obviously just the basic idea; you can make the script as fancy as you want. ;)

---

