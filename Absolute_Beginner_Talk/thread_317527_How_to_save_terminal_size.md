---
title: "How to save terminal size?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2006-12-12
I'm new to linux, and I'm just getting my Dapper install configured like I want it, and I've assigned a background picture to my terminal window, but it's a bit bigger than the default size of the terminal, and I have to resize it every time.

I tried finding a command line option using ```
gnome-terminal --help
```, but the only thing I could find was the fullscreen option.

Is there a way to set this?


Thanks,


Evan.

---

### Post by neoflight on 2006-12-12
> **evanvlane said:**
> I tried finding a command line option using ```
gnome-terminal --help
```, but the only thing I could find was the fullscreen option.
Is there a way to set this?

i found this [_here_]("http://gnomesupport.org/forums/viewtopic.php?t=10952&view=next&sid=adbac614042950603e8326dccd8d34b0")
> Currently, to start a gnome-terminal at a particular size, you need to
use the --geometry command line option, as in

```
gnome-terminal --geometry=80x40
```

This can be used in launchers on the desktop or panels. To globally change the default for the terminals launched my the
/Applications/System Tools/Terminal menu, you'd need to edit the
gnome-terminal.desktop file. Finally, the default 80x24 comes from the file GNOME_PREFIX/share/vte/termcaps/xterm, which is a termcap file. 

---

### Post by evanvlane on 2006-12-12
That's perfect!

For some reason when I saw 'geometry' my brain just passed it by.

Thanks for the prompt help. :)


Evan.

---

### Post by Bobtheknight on 2006-12-12
Not to sound stupid, but how do I locate this file to change it?  GNOME_PREFIX/share/vte/termcaps/xterm

---

### Post by lnicolao on 2006-12-17
[This]("http://ubuntuforums.org/showthread.php?p=1064192") is the best solution I've found so far

> **dngpng said:**
> I've just came across a not-so-well solution: "System>Preferences>Preferred Applications", On the "System" tab, select "custom" for the Terminal Emulator, change the "command" field to "gnome-terminal --geometry 100x50 --working-directory=%f". Done!

Click [**[COLOR="Blue"]here[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=1064192") for the original thread

---

