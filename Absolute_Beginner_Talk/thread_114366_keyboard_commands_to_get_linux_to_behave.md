---
title: "keyboard commands to get linux to behave"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by mr.wx on 2006-01-08
I've been doing a search for keyboard commands that help linux behave especially when it crashes.A few times now I've had some trouble with  programs that came with ubuntu locking up.I've tried using the following keys to get a window to close:escape,alt+f4,even tried ctrl+alt+Del,right clicking on the selected window and selecting close and clicking on the X in the corner and none of them worked.
I've had the desktop lock up on me where I could use the mouse to move the cursor around but not able to click on anything to shut down.I had to shut down using the button on the pc tower.

So my question is what are the commands in linux that would help me recover from a crash such as those?- thanks.

---

### Post by stuporglue on 2006-01-08
If you have keyboard controll, you can go to a virtual terminal and open a console there.

Ctrl+alt+{F1 or F2 or F3 ....F6} will bring you to a terminal. Use alt+{left or right arrow key} to move between them.

Log on with your user name and password.

Once logged on, you can do all sorts of fun stuff:

restart the gui: 

$ sudo /etc/init.d/gdm restart

shutdown:

$ sudo halt

See what processes are taking up CPU/memory (press m or c to sort by Memory or CPU). q to quit
$ top

Kill a program that is frozen
$ ps aux | less (use this, or top, to find the PID number of the program)
$ kill -9 $PIDNUMBER

And basicly any command line utility you could want.

---

### Post by mr.wx on 2006-01-08
thanks stuporglue thats sound pretty cool what you can do with the terminal.I will print out your suggestions and try them the next time it locks up on me.

---

### Post by r_a_trip on 2006-01-08
[QUOTE=mr.wx]
So my question is what are the commands in linux that would help me recover from a crash such as those?- thanks.[/QUOTE]

If you are using Gnome, you can rightclick on the panel above and add **Force Quit**. This little program lets you kill almost anything on the desktop that doesn't respond anymore. If a program freezes, just click Force Quit, your pointer becomes a crosshair and then click the frozen program. It will be killed.

The other option is to use [CTRL] - [ALT] - [BACKSPACE]. This kills the entire X-server  and any desktopmanager running ontop. After X is gone, it should automatically be restarted and bring you back into the desktop.

---

### Post by mr.wx on 2006-01-08
[QUOTE=r_a_trip]If you are using Gnome, you can rightclick on the panel above and add **Force Quit**. This little program lets you kill almost anything on the desktop that doesn't respond anymore. If a program freezes, just click Force Quit, your pointer becomes a crosshair and then click the frozen program. It will be killed.

The other option is to use [CTRL] - [ALT] - [BACKSPACE]. This kills the entire X-server  and any desktopmanager running ontop. After X is gone, it should automatically be restarted and bring you back into the desktop.[/QUOTE] 

thanks r_a_trip for your suggetions I have added force quit to my panel and written down the ctrl+alt+backspace

---

