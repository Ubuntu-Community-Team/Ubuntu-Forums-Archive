---
title: "former windows user help"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by antgul338 on 2006-12-26
i cant figure out how to install anything i dl from the net unless it does it on its own can anyone help?? and does anyone know if there is a prog that converts video files to dvd-r i use VSO Software with windows but im not sure with this......

---

### Post by finferflu on 2006-12-26
Do you mean you downloaded Ubuntu and don't know how to install it?
If so, you just need to burn the .iso file you downloaded as a **disc image**, not as data. You can easily do that with Nero for example, but there are also many free apps able to do that. After that, make sure your machine boots from the CD drive (you can set it from the BIOS, but new machines do it automatically, just reboot your machine with the CD inserted and see if it works), and reboot with the CD in the drive. Then select "Start or install Ubuntu" on the screen. When Ubuntu starts up, just double click on the Install icon, and follow the instructions you are given.

As for the program you have asked, I don't know, but I bet someone else will ;)

Good luck!

---

### Post by antgul338 on 2006-12-26
no im using it now but i dl divx movies and i use vso software to convert them and burn them to dvd that plays in the home dvd player  in a click or two            i ussually put 3 divx movies (>700mb) on one dvd, im trying to find out if there is something similar

---

### Post by taurus on 2006-12-26
How to install ANYTHING:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

How to convert avi to DVD:
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
(it's also available through the repos...)

---

### Post by antgul338 on 2006-12-26
thanks i will tak a look

---

### Post by elcasey on 2006-12-26
Taurus, I'm interested in this DeVeDe application myself, but I can't seem to compile the source.

I just tried to install it with "apt-get," which works, but I'm still curious how to compile and install the source from the link at the bottom of the DeVeDe website. Thanks!

EDIT: The apt-get installed version crashes before it ever loads up. I get a "Failed to load modules 2. Exiting" message when it type "devede" at the command prompt, and nothing ever happens if I run it through the Sound & Video=>Devede GUI link. Any ideas?

---

### Post by taurus on 2006-12-26
You don't compile DeVeDe since it's a python.  You just install it with the installing script after you unpack it...

---

### Post by elcasey on 2006-12-26
That makes sense. But when I run "install.sh", with or without "sudo," I get all sorts of errors about directories not existing. I'll try running some of the .py files in the dir.

EDIT:
Here's some output:```
ch@ch-laptop:~/devede28$ sudo ./install.sh
install: target `/usr/local/share/pixmaps/' is not a directory: No such file or directory
install: cannot create regular file `/usr/local/share/applications/devede.desktop': No such file or directory
```

```
ch@ch-laptop:~/devede28$ python devede.py
DeVeDe 2.8
cp: cannot stat `/usr/share/devede/devedesans.ttf': No such file or directory
Traceback (most recent call last):
  File "devede.py", line 2069, in ?
    init_main(arbol,structure,global_vars)
  File "devede.py", line 1995, in init_main
    w.connect("toggled",value_changed4,arbol,global_vars)
AttributeError: 'NoneType' object has no attribute 'connect'
```

Not sure why this is happening.

---

### Post by TooRight on 2006-12-26
Try uninstalling it, and then reinstalling it through Synaptic... I used synaptic to install it on my comp and it works beautifullyyy!!

I used to use VSO on windows too!! 

Devedee is reallyyyy simple to use, and seems to work quicker than VSO :O

I just convert to an mpeg with it and then use K3b to burn it :D


I just wanted to add, that Devede even gives you a preview of what your vid will be like after conversion, and it lets you set the preview to however long you want (in seconds)....veryyyyyyyy handy for checking video/audio quality!!

---

### Post by halitech on 2006-12-26
another nice program I just started using is manDVD (or was it MANdvd hmmmmm) either way, I like it cause it allows you to create a background that loads with a menu of the movies on the dvd that you can select using your dvd remote. you can also add background music. I used it last night to create a dvd with 2 movies (avi format), background and music and on my duron 1.3 it took about 4 hours from start to finish.

---

### Post by elcasey on 2006-12-26
I uninstalled Devede using apt-get (which is how I installed it), deleted the source files, and installed it via Synaptic.

If I run Devede from the CL, it still crashes. I tried "gksudo devede" and got the following: ```
DeVeDe 2.8
(devede:6674): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Failed to load modules 2. Exiting
```
WTF, over? ](*,)

---

