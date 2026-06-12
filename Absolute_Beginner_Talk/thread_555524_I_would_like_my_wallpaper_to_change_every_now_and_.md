---
title: "I would like my wallpaper to change every now and again. Can't start crond!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by wilsonsamm on 2007-09-20
Hello there. I've recently changed to Ubuntu after having stuck with Slackware ever since 10.2.

When I was on slackware, I had a crontab which said
00 * * * * fbsetbg /home/bilete/jenny.jpg
05 * * * * fbsetbg /home/bilete/tomandsam.jpg
10 * * * * fbsetbg /home/bilete/holidayinreading.jpg
   .
   .
   .
and so on. crond would then change my wallpaper every five minutes by invoking the next command on the list. I tried setting up a similar thing under ubuntu but there's no such command as crond and so I'm stuck . . . Anyone know what to do?

---

### Post by KrisWillis on 2007-09-20
Try ```
crontab -e
```

---

### Post by Jeroen Vernooij on 2007-09-20
Hi,
As far as I know ubuntu is using anacron.
Check system ->admin -> services.

I think you can enter your command in a text file stored in
/etc/cron.d
or /etc/cron.hourly

for examples look in /etc/cron.daily
where you find the cronjobs for apt and more.

---

### Post by tenjin1 on 2007-09-20
** How to set up (automatic) background/wallpaper-changer application for GNOME**

    * You must have Python installed (python package in Synaptic Package Manager, or from the command line): 
```

sudo apt-get install python
```

    * Method 1 uses a simple Python script named change-wallpaper.py: 

        * Download and rename the python script change-background-py and make it executable: 

```
wget http://oracle.bridgewayconsulting.com.au/~davyd/misc/change-background-py.html
mv change-background-py.html change-background.py
chmod +x change-background.py
```

        * Create a folder for your wallpapers and make a link (in your home directory) to it named .backgrounds: 

```
mkdir ~/wallpapers
gksudo ln -s ~wallpapers ~/.backgrounds

```
    or make a link (in your home directory) named .backgrounds to your /usr/share/backgrounds folder: ```


gksudo ln -s /usr/share/backgrounds ~/.backgrounds
```

        * Create a menu entry for wallpaperchanger: 

```
Right Click on Applications-> Edit Menus -> File -> Accessories -> New item
Name: Wallpaper changer
Command: ~/change-background.py (or python ~/change-background.py)

```
        * Change desktop background every time you reboot your computer: 

```
System -> Preferences -> Session -> Startup Programs
Add: ~/change-backgrounds.py  (or python ~/change-backgrounds.py)

```
        * To change the desktop background every X minute of the hour: 

```
crontab -e
```

    In the opened file enter: 

```
X * * * * * python ~/change-backgrounds.py 

```
    1 as X would mean: every hour:01. For every minute, just use * as X. 
    To exit: press ctrl+x, y 

    * Method 2 uses a more complex Python script named wallpaperchanger.py: 

        * To install the script into a different location than your home directory, replace "~" with your path 

```
cd ~
wget http://members.chello.at/horst.jens/files/wallpaperchanger.py
chmod +x wallpaperchanger.py
~/wallpaperchanger.py
gedit ~/.wallpaperchanger/wallpaperchangerconfig.py
```

        * Edit all the lines not beginning with an "#": 

```
gksudo gedit wallpaperchangerconfig.py
```

        * Create a menu entry for wallpaperchanger: 

```
Right Click on Applications-> Edit Menus -> File -> Accessories -> New item
Name: wallpaperchanger
Command: ~/wallpaperchanger.py
```


        * Change desktop background every time you reboot your computer: 

```
System -> Preferences -> Session -> Startup Programs
Add: ~/wallpaperchanger.py
```

        * To change the desktop background every X minute of the hour: 

```
crontab -e
```

    In the opened file enter: 

```
X * * * * * python ~/wallpaperchanger.py
``` 

    1 as X would mean: every hour:01. For every minute, just use * as X. 
    To exit: press ctrl+x, y 

** How to set up automatic background change (KDE)**

    * Go to K-menu -> System Settings -> Desktop -> Background
    * Choose Slide Show
    * Press Setup...
    * Press Add... to add pictures you wish to see as desktop background
    * Set 'Change picture after' to desired picture rotation interval.
    * Press 'OK'

---

### Post by wilsonsamm on 2007-09-20
Yup, I've written a crontab, and saved it.
I waited to see if it was active or not, and it wasn't, because the wallpaper still isn't changing :)
I know that cron and anacron are running, since they're both checked in a settings thing called "Tenester" which means "services", but I don't know if they've "seen" or "register" or whatever they need to do to my crontab for it to take effect...

---

### Post by tenjin1 on 2007-09-20
> **wilsonsamm said:**
> Yup, I've written a crontab, and saved it.
I waited to see if it was active or not, and it wasn't, because the wallpaper still isn't changing :)
I know that cron and anacron are running, since they're both checked in a settings thing called "Tenester" which means "services", but I don't know if they've "seen" or "register" or whatever they need to do to my crontab for it to take effect...

Hmmm...still not changing? Did you experiment with the time?
1 as X would mean: every hour:01. For every minute, would be * as X ..from above.

---

### Post by mysticmatrix on 2007-09-20
> **wilsonsamm said:**
> Hello there. I've recently changed to Ubuntu after having stuck with Slackware ever since 10.2.

When I was on slackware, I had a crontab which said
00 * * * * fbsetbg /home/bilete/jenny.jpg
05 * * * * fbsetbg /home/bilete/tomandsam.jpg
10 * * * * fbsetbg /home/bilete/holidayinreading.jpg
   .
   .
   .
and so on. crond would then change my wallpaper every five minutes by invoking the next command on the list. I tried setting up a similar thing under ubuntu but there's no such command as crond and so I'm stuck . . . Anyone know what to do?

Well I know little about programming and such..
So I'll suggest you give a look to Webilder([http://www.webilder.org/](http://www.webilder.org/)), a great app that sets flickr photo's as background.

---

### Post by hyper_ch on 2007-09-20
you're using gnome?

---

### Post by wilsonsamm on 2007-09-24
Hello, sorry for the late reply, I've just moved house and started at university, so I've just gotten hooked up to the 'net. 
I use xfce. I've used this guide to put my problem right: [http://www.howtoforge.com/xfce_desktop_background_wallpaper_changer](http://www.howtoforge.com/xfce_desktop_background_wallpaper_changer)
so thanks everyone!

---

### Post by hyper_ch on 2007-09-24
the howtoforge one is the same as here as I posted it in both places... so I wonder why it didn't work for you here...

---

### Post by kelvin spratt on 2007-09-24
use this link if you use gnome [http://www.getdeb.net/download.php?release=583&fpos=0](http://www.getdeb.net/download.php?release=583&fpos=0)  its called desktop drapes set to what ever length of time you want i hope this helps

---

### Post by Drakkor on 2007-09-24
Wallpaper Tray, it's in Synaptic :)

---

### Post by brundlelinux on 2007-10-14
I use a great utility program called Wallpaper Tray.  I'm not sure off the top of my head where I got it, but I'm sure Google would pop you an answer in .3 seconds.  It's a program that takes image files from a specified directory (your choice) and uses them as your wallpaper.  Also includes an easy pull-down menu to set up time reference for automatic changes.

I use Gnome and just added it to my boot program list at startup and that was it.

No Cron or script involved, and it was available as a Deb package file.

Good luck.

---

### Post by happy-and-lost on 2007-10-14
*sudo apt-get install wallpaper-tray*

---

