---
title: "Problems with wine. Get rid of gnome frame?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-07
When playing games under wine how do I get rid of the gnome frame and use the full screen?

I've also noticed that the the frame is off center.

My graphics engine is an intel 82945G/GZ Integrated Graphics controller.

Maybe this is just a problem with the graphics chip I don't know.

thanks

---

### Post by tdrusk on 2008-03-07
> **linuxjerk said:**
> When playing games under wine how do I get rid of the gnome frame and use the full screen?

I've also noticed that the the frame is off center.

My graphics engine is an intel 82945G/GZ Integrated Graphics controller.

Maybe this is just a problem with the graphics chip I don't know.

thanks

Go to your Wine settings. Applications> Wine> Wine settings/config

there are options about how programs are ran and such.

---

### Post by Oldsoldier2003 on 2008-03-07
> **linuxjerk said:**
> When playing games under wine how do I get rid of the gnome frame and use the full screen?

I've also noticed that the the frame is off center.

My graphics engine is an intel 82945G/GZ Integrated Graphics controller.

Maybe this is just a problem with the graphics chip I don't know.

thanks

[http://gaming.gwos.org/doku.php/wine:winestuff#advanced_stuff](http://gaming.gwos.org/doku.php/wine:winestuff#advanced_stuff)

try running it in its own x session, you'll get better performance

---

### Post by linuxjerk on 2008-03-08
Oldsoldier2003  how do you run it in it's own x session?

---

### Post by linuxjerk on 2008-03-08
ok I tried configuring wine. I can't find any combination that fills the screen without the gnome frame.

When the frame isn't there you get a tiny window that can't be expanded.

I know wine isn't the best platform for games but it's all I have right now.

There's got to be more of you that have tried gamming with wine??

---

### Post by linuxjerk on 2008-03-08
Tried running the program in xserver. Don't know what I'm doing here.
Help Oldsoldier2003 or someone who knows how to do this.


dennis@dennis-desktop:~$ #!/bin/sh
dennis@dennis-desktop:~$ #uncomment if launching from console session
dennis@dennis-desktop:~$ #sudo /etc/init.d/gdm stop
dennis@dennis-desktop:~$ #KDE use this instead
dennis@dennis-desktop:~$ #sudo /etc/init.d/kdm stop
dennis@dennis-desktop:~$ 
dennis@dennis-desktop:~$ # Launches a new X session on display 3. If you don't have an Nvidia card
dennis@dennis-desktop:~$ # take out the "& nvidia-settings --load-config-only" part
dennis@dennis-desktop:~$ X :3 -ac
X: user not authorized to run the X server, aborting.
dennis@dennis-desktop:~$ 
dennis@dennis-desktop:~$ # Goto game dir (modify as needed)
dennis@dennis-desktop:~$ cd "$HOME/.wine/drive_c/Program Files/DreamWorks Interactive/Trespasser/"
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ 
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Forces the system to have a break for 2 seconds, X doesn't launch instantly 
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ sleep 2
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ 
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Launches game (modify as needed)
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

---

### Post by linuxjerk on 2008-03-08
This is about a difficult as everything else in linux.

I put "sudo" in the x and now I get a window but the program doesn't run.

How do I get the x server window set up correctly???
(Make sure that your X server is running and that $DISPLAY is set correctly.)

Like I said previously, you have to be a programer to get anything to work in linux:(

---

### Post by linuxjerk on 2008-03-09
Can someone please help me decipher this x window mess? I don't have a clue. thanks

---

### Post by linuxjerk on 2008-03-09
Can someone please help me run this game in it's own x session?

---

### Post by linuxjerk on 2008-03-09
I really need help with this x session thing. thanks

---

