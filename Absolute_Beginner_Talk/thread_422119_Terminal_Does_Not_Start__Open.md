---
title: "Terminal Does Not Start / Open"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-04-24
Hey guys,

I don't know what happened, but when I click on Terminal (via shortcut or via Applications | Accessories) the task bar says "Starting Terminal" then it just goes away after about 10~seconds and the terminal window never pops up.

The last thing I remember doing was updating some software updates when the OS notified me.

Any Ideas?

thanks

---

### Post by ben0r on 2007-04-24
Bump-- yes i tried restarting :p

---

### Post by Tundro Walker on 2007-04-24
Ok, here's an ad-hoc solution.

You can add an applet to your panel that should let you run commands.[LIST=1]
[*]Right-click on your panel (in some blank panel spot) and click on "Add to Panel..."
[*]In the "Utilities" section, drag-n-drop the "Run Application..." applet onto your panel somewhere[/LIST]Ok, click on that, and type the following into it, replacing "HelloKitty" with the name of your home directory...

```
bash > /home/HelloKitty/Desktop/test.log 2>&1
```What that should do is test to at least make sure your BASH (Bourne Again SHell) terminal is working.  It should start up BASH, and log all results (both good and bad) to a text file called "test.log" on your desktop.

If it poops out w/o opening bash, then open that test.log, and see what kind of errors show up, or post the error log to your reply here so someone can help.

If BASH terminal shows up ok, then maybe it's the "gnome-terminal", which is the one that tries to open from "main" menu.  So, try...

```
gnome-terminal > /home/HelloKitty/Desktop/test.log 2>&1
```See what the log says if it doesn't start up.  If you're having trouble reading the log file, just cut/paste it into a reply on here and I'm sure somebody will spot something odd.

---

### Post by johnny4north on 2007-04-24
what kind of videocard & chipset  do you have in your computer.  there is a bug problem with the intel 810, that crashes the terminal here the link for more info - [https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)

---

### Post by ben0r on 2007-04-24
> **Tundro Walker said:**
> Ok, here's an ad-hoc solution.

You can add an applet to your panel that should let you run commands.[LIST=1]
[*]Right-click on your panel (in some blank panel spot) and click on "Add to Panel..."
[*]In the "Utilities" section, drag-n-drop the "Run Application..." applet onto your panel somewhere[/LIST]Ok, click on that, and type the following into it, replacing "HelloKitty" with the name of your home directory...

```
bash > /home/HelloKitty/Desktop/test.log 2>&1
```What that should do is test to at least make sure your BASH (Bourne Again SHell) terminal is working.  It should start up BASH, and log all results (both good and bad) to a text file called "test.log" on your desktop.

If it poops out w/o opening bash, then open that test.log, and see what kind of errors show up, or post the error log to your reply here so someone can help.

If BASH terminal shows up ok, then maybe it's the "gnome-terminal", which is the one that tries to open from "main" menu.  So, try...

```
gnome-terminal > /home/HelloKitty/Desktop/test.log 2>&1
```See what the log says if it doesn't start up.  If you're having trouble reading the log file, just cut/paste it into a reply on here and I'm sure somebody will spot something odd.

I copied / pasted this code as you said
```
bash > /home/ben/Desktop/test.log 2>&1
```
but BASH does not come up .... the test.log file was created on my desktop...but the file is empty.

I'm running an intel 865 chipset w/ a nvidia 6800xt

---

### Post by ben0r on 2007-04-25
ok, i found some help on google that might be useful

i opened xterm and typed in gnome-terminal

and this is what poped up
(i dont know how to copy and paste out of this window, so bear with me)

"the program 'gnome-terminal' received an x window system error.
this probably reflects a bug in the program.
this error was 'badvalue (integer parameter out of range for operation)'.
(details: serial 105 error_code 2 request_code 78 minor_code () )
(note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
to debug your program, run it with the --sync command line
option to change this behavior.  You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)"

translation?

---

### Post by ben0r on 2007-04-25
found my problem...
i have dual monitors. with xinerama enabled, gnome terminal will not work

when disabling xinerama, gnome works fine...
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232")

to keep xinerama (spanning 1 desktop over dual monitors) i had to hax0r my xorg.conf file
i had to add

Section "Extensions"
    Option "Composite" "false"
EndSection

whamo- works

gg google

---

### Post by rayashworth on 2008-04-19
This worked for me.

Basically you can just issue this command: sudo nvidia-xconfig --add-argb-glx-visuals
which will add the appropriate line (Option "AddARGBGLXVisuals" "True") to the /etc/X11/xorg.conf file in the appropriate places.

I also added this to xorg.conf

Section "Extensions"
    Option "Composite" "false"
EndSection

Regards
Ray

---

