---
title: "Nvidia and 1440x900 resolution"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by spinflick on 2006-11-14
Can sonebody please help? I just bought a 19'' wide screen monitor, but will need to update the drivers. My graphics card is a Geforce FX5500.

Will it show the new resolutions (1440x900) when the drivers are updated or will I have to mess about with other things?

Thank you.

---

### Post by ReaderRat on 2006-11-14
nVIDIA - Install & enable drivers from the repositories
          **[http://ubuntuforums.org/showpost.php?p=1754570&postcount=9](http://ubuntuforums.org/showpost.php?p=1754570&postcount=9)**
[**Installing Nvidia Drivers**](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
One of these should help...

---

### Post by spinflick on 2006-11-15
I already have glx enabled so I tried the second link.But all it gave me was an NVidia Settings box so how do I change the resolution? Thanks

---

### Post by lonce on 2006-11-15
you have to edit your /etc/X11/xorg.conf file and add the resolutions you want to use.  Its pretty simple.  When you open the file you will see what I mean.

---

### Post by zenbuntu on 2006-11-15
I got my 19" WS monitor (on nVidia video card) working like this:

```
sudo dpkg-reconfigure -phigh xserver-org
```

Make sure you select 'nvidia' as the driver, then use the spacebar to mark resolutions you need (choose 1440x900 here). 

This will set your /etc/X11/xorg.conf file for you. 

You will need to restart the machine or at least press CTRL-ALT-BACKSPACE

Good luck.

---

### Post by spinflick on 2006-11-15
Thank you everyone for your help.I got into xorg and my first resolutions settings where set at 1440x1440 so I changed them. Now I have 1440x900 :-D 

But my refresh rate is set at 75Hz and should be 60Hz this doesnt look like a problem at the moment but might be in the future.So I.... sudo gedit /etc/x11/xorg-conf but nothing is there :confused: What's happened?

---

### Post by zenbuntu on 2006-11-15
Use:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by spinflick on 2006-11-15
Sorry for being a pain but it's not showing any refresh rates :oops:

---

### Post by Perfect Storm on 2006-11-15
Do not use sudo gedit. It's gksudo gedit or better yet use sudo nano instead.

Do you have some horizental and vertical specs for your monitor (can be found in monitor manual).

---

### Post by spinflick on 2006-11-15
gksudo gedit wont work :confused: cant I just keep using the one Im use to?

---

### Post by Perfect Storm on 2006-11-15
It can mess up our system so it's not advisable. Use nano then. It's good to learn nano as it also works in CLI.

---

### Post by spinflick on 2006-11-15
will it mess up my xorg? ie will I be asked numerous questions about my keyboard and the likes? I already messed up twice and I would rather leave things as there are than going through a complete install :(

---

### Post by spinflick on 2006-11-15
Dont matter cause nano dont work either ](*,)

---

### Post by Perfect Storm on 2006-11-15
You know that linux is case sensitive so you have to do it correctly:
```
sudo nano /etc/X11/xorg.conf
```


A good idea before messing with xorg is to back it up first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup
```

so you can easely change back if you mess it up by:
```
sudo cp /etc/X11/xorg.mybackup /etc/X11/xorg.conf
```

---

