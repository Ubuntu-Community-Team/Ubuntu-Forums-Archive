---
title: "[SOLVED] When I run Terminal Window it logs out of 'X'"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by gshockxc on 2007-12-08
When I open the terminal window to run a command, the window appears for an instant and then Xubuntu logs out and takes me back to the login screen.  Xubuntu 7.04

VisionBook Pro Series laptop 7590.  

Running terminal window in an effort to improve display resolution.

---

### Post by overdrank on 2007-12-08
> **gshockxc said:**
> When I open the terminal window to run a command, the window appears for an instant and then Xubuntu logs out and takes me back to the login screen.  Xubuntu 7.04

VisionBook Pro Series laptop 7590.  

Running terminal window in an effort to improve display resolution.

Hi and this thread may help
[http://ubuntuforums.org/showthread.php?t=572752&highlight=terminal+logs+out&page=2](http://ubuntuforums.org/showthread.php?t=572752&highlight=terminal+logs+out&page=2)

---

### Post by mali2297 on 2007-12-08
> **gshockxc said:**
> When I open the terminal window to run a command, the window appears for an instant and then Xubuntu logs out and takes me back to the login screen.  Xubuntu 7.04

VisionBook Pro Series laptop 7590.  

Running terminal window in an effort to improve display resolution.

This is a known bug:
[https://bugs.launchpad.net/xfce/+bug/91849](https://bugs.launchpad.net/xfce/+bug/91849)

See the latest comments, there you will find possible workarounds. They involve editing xorg.conf, which you probably are going to do anyway to improve display resolution.

Press Alt-F2 and type
```

gksudo mousepad /etc/X11/xorg.conf

```
This will allow you to edit the configuration file.

An alternative is to use another terminal, like **xterm**. Press Alt-F2 and type
```

xterm

```

---

### Post by gshockxc on 2007-12-08
> **mali2297 said:**
> This is a known bug:
[https://bugs.launchpad.net/xfce/+bug/91849](https://bugs.launchpad.net/xfce/+bug/91849)

See the latest comments, there you will find possible workarounds. They involve editing xorg.conf, which you probably are going to do anyway to improve display resolution.

Press Alt-F2 and type
```

gksudo mousepad /etc/X11/xorg.conf

```
This will allow you to edit the configuration file.

An alternative is to use another terminal, like **xterm**. Press Alt-F2 and type
```

xterm

```

Thanks for the suggestions.  I'll try that and post back with the results.  Just starting to lift the hood and see what's in there.

I appreciate all the help.

---

### Post by gshockxc on 2007-12-09
> **mali2297 said:**
> This is a known bug:
[https://bugs.launchpad.net/xfce/+bug/91849](https://bugs.launchpad.net/xfce/+bug/91849)

See the latest comments, there you will find possible workarounds. They involve editing xorg.conf, which you probably are going to do anyway to improve display resolution.

Press Alt-F2 and type
```

gksudo mousepad /etc/X11/xorg.conf

```
This will allow you to edit the configuration file.

An alternative is to use another terminal, like **xterm**. Press Alt-F2 and type
```

xterm

```

Tried that... same result.  I typed in the command and tried to run it in a terminal window, and it logged me out and sent me back to the login screen.  Then I tried to run it without the terminal window.  I got the xorg.conf file, but I don't know what to edit.  The screen resolutions that I want are all there, but they don't show up when I open up the Display Preferences (Right-click Desktop, Settings, Display Settings.)

---

### Post by mali2297 on 2007-12-10
> **gshockxc said:**
> Tried that... same result.  I typed in the command and tried to run it in a terminal window, and it logged me out and sent me back to the login screen.  Then I tried to run it without the terminal window.  I got the xorg.conf file, but I don't know what to edit.  The screen resolutions that I want are all there, but they don't show up when I open up the Display Preferences (Right-click Desktop, Settings, Display Settings.)

To fix the terminal error, try adding
```

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```
at the end of the file.

Doesn't xterm work if you start it from the run dialog (Alt+F2)?


As for the screen resolution, see if this Howto helps:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by gshockxc on 2007-12-10
> **mali2297 said:**
> To fix the terminal error, try adding
```

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```
at the end of the file.

Don't xterm work if you start it from the run dialog (Alt+F2)?


As for the screen resolution, see if this Howto helps:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Yes, Xterm works with Alt+F2.  Your suggestion seems to have fixed the terminal problem.  What was wrong and why does your suggestion work?  What's happening when I edit the xorg.conf file?

I read the link you gave and tried a couple of possible solutions.  Something is odd on my xorg.conf file.  

I don't have  the driver heading.  I have the following sections: 

Section "Files"
Section "Module"
Section "InputDevice" 
     Identifier "Keyboard"
Section "InputDevice" 
     Identifier "Configured Mouse"
Section "InputDevice"
     Driver "wacom"
     Identifier "stylus"
Section "InputDevice"
     Driver "wacom"
     Identifier "eraser"
Section "InputDevice"
     Driver "wacom"
     Identifier "cursor"
Section "Device"
     Identifier "Chips and Technologies F6555 HiQVPr"
     Driver "chips"
Section "Monitor"
     Identifier "Generic Monitor"
     Option "DPMS"
Section "Screen"
     Identifier "Default Screen"
     Device "Chips and Technologies F6555 HiQVPr"
     Monitor "Generic Monitor"
SubSection "Display"
     Depth, 1, 4, 8, 15, 16, 24 (each one has its own subsection with display resolutions).

Any suggestions?  

Terminal works great.  Thanks for the help.

---

### Post by mali2297 on 2007-12-11
> **gshockxc said:**
> Yes, Xterm works with Alt+F2.  Your suggestion seems to have fixed the terminal problem.  What was wrong and why does your suggestion work?  What's happening when I edit the xorg.conf file?

It is a bug in the default terminal for the Xfce desktop environment. The workaround means that you disable the use of composite window management, that is, transparent windows and such. I don't know why this fixes the problem.

> 
I read the link you gave and tried a couple of possible solutions.  Something is odd on my xorg.conf file.  

I don't have  the driver heading.  I have the following sections: 

Section "Files"
Section "Module"
Section "InputDevice" 
     Identifier "Keyboard"
Section "InputDevice" 
     Identifier "Configured Mouse"
Section "InputDevice"
     Driver "wacom"
     Identifier "stylus"
Section "InputDevice"
     Driver "wacom"
     Identifier "eraser"
Section "InputDevice"
     Driver "wacom"
     Identifier "cursor"
Section "Device"
     Identifier "Chips and Technologies F6555 HiQVPr"
     Driver "chips"
Section "Monitor"
     Identifier "Generic Monitor"
     Option "DPMS"
Section "Screen"
     Identifier "Default Screen"
     Device "Chips and Technologies F6555 HiQVPr"
     Monitor "Generic Monitor"
SubSection "Display"
     Depth, 1, 4, 8, 15, 16, 24 (each one has its own subsection with display resolutions).

Any suggestions?  


I suggest that you mark this thread as solved and start a new thread on the separate issue of the screen resolution, post there the name of your graphics card and the entire content of xorg.conf. Hopefully, more people will then come to the rescue.

---

