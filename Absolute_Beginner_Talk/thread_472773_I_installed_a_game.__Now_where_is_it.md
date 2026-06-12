---
title: "I installed a game.  Now where is it?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by kstruve on 2007-06-13
This is something weird about Ubuntu that I haven't figured out yet.  Sometimes when I install a new app through Synaptic, it doesn't show up anywhere in my applications menu.  For instance, last night I installed the game "Gnugo" but now I can't find it to play it.  Any ideas?

Thanks a bunch.

---

### Post by kittyhawk63 on 2007-06-13
Type gnugo in Terminal. Hit "enter".

---

### Post by Anonii on 2007-06-13
I bet that you will be able to run it from the terminal with the command "gnugo". (If you have no idea on what the terminal is, try reading this: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) , or at least the basic parts of it.). 
But, if gnugo has a graphical user interface, it's quite weird if it doesn't have a menu entry.

Try what I said, please, and post back. If it indeed has a GUI and it doesn't have a menu entry, you can easily create one.

---

### Post by kstruve on 2007-06-13
I ran "gnugo" in the terminal but it's just a non-graphical program.  So I then installed the frontend for Gnugo but I still don't see it in the menu.  When you install an application, where does it go by default?

Thanks!

---

### Post by thelinuxguy on 2007-06-13
Go to a terminal and type 'gnugo'.
Edit: Never mind...I was late...

---

### Post by Seti on 2007-06-13
In a terminal do 
```

whereis gungo

```

This will show you the location of the binary for your program.

---

### Post by kstruve on 2007-06-13
Ah, very good to know.  I'll try the "whereis" command.  Thank you!

---

### Post by kittyhawk63 on 2007-06-13
In Synaptic it says that it is a text-only game. There is no GUI.

Read this from Synaptic concerning Gnugo.
GNU Go is a free program that plays the game of Go, its homepage can
be found at [http://www.gnu.org/software/gnugo/](http://www.gnu.org/software/gnugo/). The program provides
a **text-only user interface**, have a look at the cgoban or qgo package
if you want to play on a graphical board.

---

### Post by KIAaze on 2007-06-13
That's because shortcuts are not always installed by default.
It's up to those who create the binary packages to add launchers to be installed automatically.
If they don't, you can still easily do it yourself. It's not done the same way as in Windows (which I find more intuitive), but it's not hard either.

How to create a shortcut manually:
First of all, find out the command used to launch the game ("gnugo" in your case).

_GUI method:_
Open a terminal and type:
```
alacarte
```
It will launch a GUI to add menu entries. (can probably be launched from the menu too, but I'm on another PC without Ubuntu right now)

Go to the Game section in Alacarte and push the New Item button. Fill in;

-Name: whatever you want
-Comment: whatever you want
-Command: command used to lauch the game from a terminal
-Icon: whatever you want

_CLI method:_
(here with an example shortcut for the Loose Cannon game (copied from the Ubuntu Gamers Arena site))
```
sudo nano /usr/share/applications/Loosecannon.desktop

```

Add the following;

> [Desktop Entry]
Name=Loose cannon
Comment=3rd person action adventure game.
Exec=loosecannon
Icon=/usr/local/share/loosecannon/pics/smg.png
Terminal=false
Type=Application
Categories=Application;Game;

Save and exit: ctrl+o, ctrl+x

You can find other examples by opening existing .desktop files in "/usr/share/applications".

---

### Post by christhemonkey on 2007-06-13
If you installed a graphical interface then you probably installed cgoban or qgo.

To launch either of these just type its name into the terminal:#
```
cgoban 
```

```
qgo  
```


And if you installed either of these and they dont have menu items, please file a bug! :D

---

### Post by kstruve on 2007-06-13
Great!  Thanks for all the tips, guys.  AND the prompt responses!

---

### Post by linuxforrealpeople on 2007-06-20
Why isn't there a menu item for Alacarte (ha!)? As in why isn't phoenetic spelt with an 'F'

---

### Post by KIAaze on 2007-06-20
??
What?

There's probably no menu item for Alacarte because you can access it by right-clicking and choosing "edit menus".

---

