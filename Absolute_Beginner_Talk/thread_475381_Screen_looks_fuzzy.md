---
title: "Screen looks fuzzy"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-16
My screen looks sort of... fuzzy. it's not that bad when just looking at the desktop, but it's annoying while reading through web pages and horribly obvious when watching movie files (which where very clear on my windows machine.

heres what i can tell you:
My resolution in currently set at 1280X768 and i'm using a Gateway mx6030 i have the gaetway display driver, but i'm not sure if that would be helpful at all, and if so, how to go about installing it.

---

### Post by adamorjames on 2007-06-16
Installing the driver sounds like a good bet!

---

### Post by colddayinapril on 2007-06-16
yeah... thing is, i'm not sure now to go about installing a .exe file in linux

anyy good how-to's for noobs like me on the subject?

---

### Post by adamorjames on 2007-06-16
Was Windows using the same resolution? You found the Linux driver right? Partial list of Gateway Linux drivers -> [http://list.driverguide.com/list/LINUX/company424/index.html](http://list.driverguide.com/list/LINUX/company424/index.html) (there looks to be search bar at the top).

---

### Post by colddayinapril on 2007-06-16
i was running 1200 x 800

---

### Post by quinnten83 on 2007-06-16
I think that *.exe's are not to be installed in Linux.
Maybe the sharpness can be configured by configuring your xorg.conf file, but I wouldn't know exactly how (I'm sort of a nOOb myself).
Your best bet would be to post the contents of your xorg.conf file and the type of video card your using

code
```
lspci
```
look for something referring to vga graphics.

and
```
sudo gedit /etc/X11/xorg.conf
```.

I found a howto to configure fonts [here]("http://http://www.howtoforge.com/sharp_fonts_gnome").
Although I don't think that will help you with the fuzzy video issue.
Wishing you good luck!

---

### Post by adamorjames on 2007-06-16
You may need to change your resolution to 1200x800 in xorg.conf.

---

### Post by PaulFr on 2007-06-16
If your relative fuzziness is because Windows runs your display at a higher resolution, you may want to take a look at **[https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX6027](https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX6027)** for the MX6027 laptop - there is a section at the bottom which indicates you need the 915resolution package to enable the  native 1280x800 resolution. Perhaps this is your problem as well.

---

### Post by colddayinapril on 2007-06-16
just followed quinntens directions, and xorg.conf is completely empty :O

---

### Post by colddayinapril on 2007-06-16
thanks paulf, that cleared everythign right up... and i'm bookmarking those instructions into my recovery folder.

much thanks guys, problem solved :)

---

### Post by meborc on 2007-06-16
> **colddayinapril said:**
> just followed quinntens directions, and xorg.conf is completely empty :O

you probably made a typo... when you try to edit a file that does not exist, it will create one new with the same name/location you were trying to use... try to copy/paste the command

---

### Post by meborc on 2007-06-16
> **colddayinapril said:**
> thanks paulf, that cleared everythign right up... and i'm bookmarking those instructions into my recovery folder.

much thanks guys, problem solved :)

heh :) nice to see you got it working... good luck!

check out this page - [www.ubuntuguide.org](www.ubuntuguide.org) for more fun with your ubuntu box

---

