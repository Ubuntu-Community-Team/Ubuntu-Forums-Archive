---
title: "flash mx on linux helllllllllllp1!!!!!  plzzzzzz"
date: 2007-11-06
forum: Art &amp; Design
---

### Post by tboandfshady on 2007-11-06
hi im new to ubuntu and i wanteed to know if theres a program like flash mx that i can download i cant use wine 4 sum reason i just want to make some flash animations plzzzzzzzzzzzz some1 help :)

---

### Post by smartboyathome on 2007-11-06
There is F4L, but other than that, you will have to use Wine to run Adobe stuff (note that CS3 doesn't work with wine).

---

### Post by smartalecks on 2007-11-06
flash is proprietary, and adobe only seems interested in developing the studios for windows. If you can get wine working (its in the repositories), Flash 8 works perfectly with wine.

Get Wine, it is in the default repos!
```

System > Administration > Synaptic Package Manger > Search: wine

```

or

```

$     sudo apt-get install wine

```

Install it, and in a terminal
```

$     winecfg

```
Set it to emulate Windows XP. When you get the Flash 8 trial
```

$     wine ~/Desktop/Flash8-en.exe

```
And then follow the install instructions. Once it is done, make a launcher (right click desktop, "Create Launcher"). Set it's type to "Application in Terminal," name "Flash 8 Trial," the command:
```

wine "/home/USERNAME/.wine/drive_c/Program Files/Macromedia/Flash 8/Flash.exe"

```
If you want an icon (made by me from the flash logo), save this icon to a folder, click on the icon button, browse to the icon's location and select it. Hit "OK" and it'll be created on your desktop, you can put it on the panels or menu, etc.

[IMG]http://img340.imageshack.us/img340/5891/flashlogojv9.png[/IMG]

f4l, I think, has been abandoned or if he is continuing development its going very slowly :/

---

### Post by tboandfshady on 2007-11-22
thx man but i cant get wine il try any thanx 
is there any way to convert in to a bin file for ubuntu to install ?:)

---

