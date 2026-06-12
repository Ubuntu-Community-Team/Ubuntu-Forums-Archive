---
title: "Wine"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by boombaxx on 2007-05-30
i managed to get wine installed but don,t know how to launch it. how do you add it to your program list. Also in the restricted packages manager i tried to get my nvidia video card to work. It says do you want to enable nvidia card i enable it but it says  not functioning the video card is FX 5900 vtd. Am i missing drivers or something

---

### Post by Peetke on 2007-05-30
To get wine up and running, simply type "winecfg" in a terminal. It will setup all settings and give you some options. Afterwards you can run .exe files in wine.

---

### Post by Borzo on 2007-05-30
you need to launch a windows application with wine, so from console... typing wine /media/cdrom/setup.exe should work.
or you can open a window of your install cdrom and select the . exe file, right click it, select wine as an application to be used by default to open .exe files, then click on such file

---

### Post by sankarv on 2007-05-30
to run any windows exe files


type

> 
wine <file-name>.exe


if it is a setup file it will install it to **.wine** dir in your [B]home dir
[/B]

a menu entry called **wine** is created in **Applications** menu where the wine installed items have thier menu entries.

---

### Post by burt_57 on 2007-05-30
> **boombaxx said:**
> i managed to get wine installed but don,t know how to launch it. how do you add it to your program list. Also in the restricted packages manager i tried to get my nvidia video card to work. It says do you want to enable nvidia card i enable it but it says  not functioning the video card is FX 5900 vtd. Am i missing drivers or something
YA that is one thing with nvidia. Also my monitor should be at 60 hertz but it only work at 54.
I have downloaded tha NVIDIA for linus but do not know how to install it..it sit on my desktop " the updates ".
The view on my screen is to small for me and get some flicker some time because of wrong set up
for Phillips 19 flat monitor ,....am in same boat as you. :(

---

### Post by AndyCooll on 2007-05-30
You don't actually "launch" Wine. It's a compatability layer that acts as a "middle manager" so to speak between Linux and your Windows app. You "launch" the app itself.

Typing "winecfg" opens up a configuration utility for Wine, however follow sankarvs instructions to actually open a Windows app.

:cool:

---

### Post by kitch on 2007-05-30
Can't I use "create launcher" from the desktop to create a shortcut to a program running on wine?

---

### Post by ajgreeny on 2007-05-30
You certainly can!  Use you normal method of doing that, but in the command box you will need to type:-
wine full_path_to _file.exe

---

### Post by kitch on 2007-05-30
just tried that, I used the TYPE Application in Terminal and it opens and closes the terminal window at light speed but my app doesnt open:(

---

### Post by kitch on 2007-05-30
worked it out sort of,  the file path has a space in it. how do I overcome this without renaming the folder as there are other files using it?

---

### Post by AnRa on 2007-05-30
> **kitch said:**
> worked it out sort of,  the file path has a space in it. how do I overcome this without renaming the folder as there are other files using it?You have to put it quoted (e.g. "/path with space/to/program").

---

### Post by j.miller565 on 2007-05-30
Use a \ 
for example:   /home/bob/My\ Pictures/furrylion.jpg

You still put a space in after the backslash (\)

---

### Post by kitch on 2007-05-30
I love you guys!   :lolflag:

and this Linux lark is really starting to catch on...

---

