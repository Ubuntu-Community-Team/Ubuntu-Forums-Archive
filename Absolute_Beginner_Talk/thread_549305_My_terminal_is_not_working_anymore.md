---
title: "My terminal is not working anymore"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by graben3 on 2007-09-12
Terminal is not working anymore. It used to be working. But I tried to download the Desktop search package and it did'nt download. I clicked close on the dialog box of the Add-Remove software utility in feisty fawn. I was also configuring my dual monitors at the same time. I overwrited my xorg.conf and retarted X by hitting ctrl+alt+backspace and then I cannot open the console. It open a task in the task bar with title "Starting console..." then it disappears of the taskbar.


However I can still access the other terminals (ctrl+alt+f1, f2, f3, etc....)
It is just frustrating since I cannot make any new software install in graphical mode anymore since it requires the console to be working to install packages.


Can someone point me in the right direction.... got no clue how to resolve this...

Forgot to tell .... my dual screen configuration is working perfectly so I don't think this has to do with the bug of my terminal program

---

### Post by asmoore82 on 2007-09-12
it sounds like you may be using KDE/Kubuntu ...

IF you are using GNOME ...

1. try "Run" (alt+f2, by default) -> "xterm"
and/or
2. do a [ctrl]-[alt]-[f1], login and run

```
~$ gnome-terminal --display=:0
```

that will let you see the error being thrown so you can post it.

---

### Post by graben3 on 2007-09-12
Ok... tried what you told me :

1. try "Run" (alt+f2, by default) -> "xterm"
It opens up a terminal window, no errors !... but when I try opening a terminal window via :
Application > Accessories > Terminal the window never come up, it is just a taskbar item which disappears after 3 seconds...

2. gnome-terminal --display=:0
It gives me an error here is the output :

The program 'gnome-terminal' received an X Window System error
This probably reflects a bug in the program
The error was 'BadValue (integer parameter out of range for operation)'.
  Details : serial 103 error_code 2 request_code 78 minor_code 0)
... (not to programmers text here removed since it has nothing to do with the error)

What does this error means ? does it have to do with the command ?
I'm running ubuntu feisty fawn with all updates installed. I'm pretty sure to be running gnome as window manager. I'm definitively not running kde since i have not installed it and it is not in the choices I have on the login page for my xwindow system. Maybe i'm running a window systems which looks the same as gnome ? Is this possible ? I don't know but I know that on the login screen if i choose gnome it is exactly as it is on my desktop now.... same theme same menus, etc... so I must be running gnome as window manager.

---

### Post by graben3 on 2007-09-12
I just found this thread, seems like my problem :

[http://forums.fedoraforum.org/archive/index.php/t-159767.html](http://forums.fedoraforum.org/archive/index.php/t-159767.html)

Watch the post by eliot :

eliot
2007-07-13, 11:34 PM PDT
i'm having the same issue here except on ubuntu.

i think it does have something to do with the xorg. config because it only started for me when i setup dual monitor with xinerama.

if i go back to an old single monitor xorg.conf file and reload X, then terminal works great! i really think the difference for me is running xinerama, but i have no idea why that is and how i can fix it.

i can run xterm starting from alt-F2 fine but when i try to run gome-terminal it errors out (can't copy full error because haven't a hard time copying in xterm :-P):

"The program 'gnome-temrinal' received an X Window System error"

any thoughts would be greatly appreciated.

eliot
2007-07-14, 09:17 AM PDT
hey ikiini,

i found a solution that worked for me from the ubuntu forums and i'm thinking that it may help you as well.

apparently there's an issue with xinerama and nvidia-glx, which i'm guessing you may be running on your system. adding the following to the end of your xorg.conf file (/etc/X11/xorg.conf) was recommended:

Section "Extensions"
Option "Composite" "false"
EndSection

Worked like a charm for me, hope it helps you too.

Best,
Eliot

--------------------------------------------------------------------------------------------------

I have the same configuration and it happened when i was setting up dual screens with xinerama so I guess this will work for me....

I'll get back to you as soon as I have tried this....

---

### Post by asmoore82 on 2007-09-12
try re-installing 'gnome-terminal' through Synaptic

---

### Post by graben3 on 2007-09-12
Ok..... the problem is resolved ! it was only the composite extension in xorg.conf....


So if anyone of you are using ubuntu feisty fawn, have the nvidia proprietary drivers running with dual screen (Xinerama) and your terminal don't open anymore try adding this to 
/etc/X11/xorg.conf :

Section "Extensions"
Option "Composite" "false"
EndSection


Work like a charm for me !

Thank to everyone for their help !

---

