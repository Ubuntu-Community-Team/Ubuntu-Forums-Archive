---
title: "difference between server and desktop?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by iioorr on 2006-06-02
I dont know if I installed the server version, or if something went wrong but I got no X server after my install. I installed gnome. 

Is there a difference between server and desktop? Am I missing out on anything? Should I download the desktop version and install that instead?

---

### Post by Rinzwind on 2006-06-02
The server install has NO gnome.

From the # do
**sudo apt-get install ubuntu-desktop**

and it installs gnome :)

So as an exercise in doing it correctly I would myself go for a re-install ;)

---

### Post by IYY on 2006-06-02
The server version is just a stripped down version, Ubuntu without the graphical user interface. You can get the graphical stuff with this command:

sudo apt-get install ubuntu-desktop

or (for KDE instead of Gnome)

sudo apt-get install kubuntu-desktop 

or even XFCE:

sudo apt-get install xubuntu-desktop

---

### Post by iioorr on 2006-06-02
Yes, thank you, but I already installed gnome.

Is there a way of knowing If i installed server or if the installation just f-d up?

---

### Post by lkagan on 2006-06-02
I don't know the details, but when I think of the difference between most servers vs. desktops, the GUI is the first thing that comes to mind.   To be honest, I would suggest that you install the desktop if that's indeed what you'll be using it as.  You can of course do anything on the server that you can do on the desktop by installing, changing, removing packages but certain configurations will be different and may make it more difficult to find help since everyone else out there using a desktop has something slightly different.  

Anyway, typing 'gdm' should get you a gui.

Larry

---

### Post by lumpki on 2006-06-02
It sounds like your video card didn't get autodetected and set up properly. Do see a text "login:" prompt? If so, log in there and type
```
sudo dpkg-reconfigure xserver-xorg
```
Which will allow you to set up all of the X server options... if you're not sure how to answer some of them, pick the default. If you can't get it working, please post details on your video card and monitor.

Hope this helps!

---

### Post by iioorr on 2006-06-02
I got something like "X server not available because of missing file XXX". So I installed gnome. 
And now everything works. 

All I want to know, is there a way of knowing if I installed server or desktop? Been looking through system and help and Im none the wiser. 

Btw, maybee the dvd release was faulty, because they removed them from ubuntu.com.

---

### Post by lumpki on 2006-06-02
There's really no difference except in the selection of packages that are installed... you can install things like apache httpd (web server), mysql server, etc on your desktop system, and you can install Gnome or KDE (or both) on your server system. Linux is flexible that way.

---

### Post by iioorr on 2006-06-02
[QUOTE=mukta]There's really no difference except in the selection of packages that are installed... you can install things like apache httpd (web server), mysql server, etc on your desktop system, and you can install Gnome or KDE (or both) on your server system. Linux is flexible that way.[/QUOTE]

I dont have apache installed, so I guess I installed the desktop version. Hopefully dapper will appear solid after this little misshap. May be a bad dvd-r I or something I guess. 

Thanks guys :D

---

### Post by hermitology on 2006-06-02
then tell me how to disable server as i get error message at long on dhcp not configured , plz tell me how to figure this out amd also kindly tell me my mistake during installation . i wanted to install desktop .

---

