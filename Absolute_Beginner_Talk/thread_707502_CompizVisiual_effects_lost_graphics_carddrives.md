---
title: "Compiz/Visiual effects lost graphics card/drives"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by drubin on 2008-02-25
Hi guys.

After MUCH fighting it finally got my graphics card working
Install the driver manually:-

```
1) Install the required prerequisites for the Nvidia installer using:-
Code:

sudo apt-get install build-essential

2) Download the Nvidia driver:-
Code:

wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run

3) Make a few changes to the "DISABLED_MODULES" line of a modules file using:-
Code:

gksudo gedit /etc/default/linux-restricted-modules-common

to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Note:- From this point on you will be using the CLI(Command Line Interface) where you will have to be completely dependent on commands.

4) Kill the X-Server using:-
Code:

sudo /etc/init.d/gdm stop

5) Execute the Nvidia installer using:-
Code:

sudo sh NVIDIA-Linux-x86-169.07-pkg1.run

6) After the installation is successful reconfigure the X-Server using:-
Code:

sudo dpkg-reconfigure xserver-xorg

choosing the driver as "nvidia" and any other options you may need.

7) Restart the GUI using:-
Code:

sudo /etc/init.d/gdm start

```

Every thing was ok, Untill i tried to enable more visual affects. (I mean i have a decent graphics card  Gfore 7300GS-TD 256mb) It asked me to to enable the restircted drivers so i did. I then lost ALL my hard work setting up my graphics card.(screen res all that jazz).

I uninstalled the "restricted driver" and re-installed the manual way that worked the first time :).

But i STILL cant seem to use normal affects. SEE screen shots.


Things i used to have but dont any more :( 
1)  My terminal used to be able to go transparent, (not just show the desktop image, but let any other windows below it "shine" through.
2)  Used to have my title bars being semi transparent.
3) Used to be able to view previews of windows when pressing alt+tab (now just icon iamges)

Little things that i miss? Does any one know how i can get them back, they were working at a point in time.  

Thanks again

---

### Post by drubin on 2008-02-25
Guys after much searching, i found the solution. -[COLOR="Red"]-This idid NOT work. [/COLOR]

I much prefer CMD, to the GUI menus at least you know it is going to do what you want it to do. :)

[http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting) 
[http://wiki.compiz-fusion.org/CompizFusionIcon](http://wiki.compiz-fusion.org/CompizFusionIcon)
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
```
compiz --replace ccp & emerald --replace & 
```

Hope this helps other people.

---

### Post by drubin on 2008-02-25
Sorry i take that back, I restarted my computer, and all the nice affects were gone again.

after doing.
```
sudo apt-get upgrade
```

And well any time i use the cmd compiz  it logs me out of my xserver session?

---

### Post by drubin on 2008-02-26
Hi sorry i keep replying to my self, but i keep finding out more details that i HOPE well help solve the problem.

I decieded to see the output of runing the comman compiz.  but it restarts my xserver. 

So i ```
compiz >compiz.txt
```
here is the output. it generated before it restarted xserver.
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01df (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: 
```

---

