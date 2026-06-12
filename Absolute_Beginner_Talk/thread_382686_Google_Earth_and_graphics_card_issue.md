---
title: "Google Earth and graphics card issue"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-03-12
Why, when I install Google Earth on Ubuntu am I asked to update my graphics card software and until I do Google Earth will run slow, which it does. Also much of what can be seen is just a blurr on the screen very little detail. If I boot up into XP  it works perfectly.  Any advice anyone?

---

### Post by Bachstelze on 2007-03-12
Install drivers for your graphics card.

---

### Post by a.v.l on 2007-03-12
> **HymnToLife said:**
> Install drivers for your graphics card.

I've installed the driver I thought was the right one for my graphics card, an (ATI Radeon 9250 AGP 8X 128 MB with TV out DVI)  the driver used was an (ATI driver  8.28.8) but having done this, Google Earth tells me that I am still running open GL with software emulation which causes the software to run slowly and to have a very jurky movement when zooming into an area. I am also being told to update my graphics card again. Would anyone know the right driver for this graphics card please?

---

### Post by freebird54 on 2007-03-12
To help we need a little more information about how your system is running.  If you can open an  Applications->Accessories->Terminal run

```
fglrxinfo
```

in it, and then paste the result here, probably we can get this going.  I suspect you'll see the words mesa somewhere in there..... which means it isn't fully operational yet.

As you can see from my signature, I run ATI - and Google Earth is a toss up between XP and Ubuntu for speed.

---

### Post by a.v.l on 2007-03-12
> **freebird54 said:**
> To help we need a little more information about how your system is running.  If you can open an  Applications->Accessories->Terminal run

```
fglrxinfo
```

in it, and then paste the result here, probably we can get this going.  I suspect you'll see the words mesa somewhere in there..... which means it isn't fully operational yet.

As you can see from my signature, I run ATI - and Google Earth is a toss up between XP and Ubuntu for speed.

Thanks for your help I've run fglrxinfo in terminal and get this result.

:~$ fglrxinfo
bash: fglrxinfo: command not found

---

### Post by arron on 2007-03-12
yes my ati performance is the same with xp / linux.  Seting up the drivers was the tricky part.  Google earth with a ati 200m runs nice for me.  I was happy to find a google earth for linux as well, i hope someone makes a package for it.

glxgears -printfps

will show your fps, i get 170 ish.

---

### Post by arron on 2007-03-12
> **a.v.l said:**
> Thanks for your help I've run fglrxinfo in terminal and get this result.

:~$ fglrxinfo
bash: fglrxinfo: command not found

do a search on the forum on how to install these drivers.  Its not *to* bad to install, but i will never buy ati again.

---

### Post by overdrank on 2007-03-12
> **a.v.l said:**
> Thanks for your help I've run fglrxinfo in terminal and get this result.

:~$ fglrxinfo
bash: fglrxinfo: command not found

I would recomend using this guide worked great for me.
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Good luck!

---

### Post by a.v.l on 2007-03-12
> **arron said:**
> yes my ati performance is the same with xp / linux.  Seting up the drivers was the tricky part.  Google earth with a ati 200m runs nice for me.  I was happy to find a google earth for linux as well, i hope someone makes a package for it.

glxgears -printfps

will show your fps, i get 170 ish.

Thanks, my FPS is averaging out at around 110

---

### Post by arron on 2007-03-12
> **paul capps said:**
> I would recomend using this guide worked great for me.
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Good luck!

Sweet! thanks for the link, Im going to try it on my upcoming fresh install, i hope it works for the ati 200m.

a.v.l - np :)

---

### Post by a.v.l on 2007-03-12
> **paul capps said:**
> I would recomend using this guide worked great for me.
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Good luck!

I went through this tutorial but unfortunatly the driver wasn't regonised. Still no fix.

This was my end result:

       +---------------------------------------+
       |    Envy Menu ver.0.8.1                |
       |                                       |
       |    1 - Install the NVIDIA driver      |
       |                                       |
       |    2 - Uninstall the NVIDIA driver    |
       |                                       |
       |    3 - Install the ATI driver         |
       |                                       |
       |    4 - Uninstall the ATI driver       |
       |                                       |
       |    5 - Restart the Xserver            |
       |                                       |
       |    6 - Exit                           |
       |                                       |
       +---------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Dapper 32bit

Your graphic card does not seem to be supported by the driver.

                        Would you like to go ahead with the installation even if, according to Envy, your card is not supported?
                        (Type either "yes" or "no")

---

### Post by XstatyK on 2007-03-12
Nevermind just saw it posted already

---

