---
title: "Select/access/edit xorg.conf file? or locate ATIConfig?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by pryan75 on 2007-11-24
I have managed to get through 80% of this how-to:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository)

I've come to a point where I am to configure the driver AKA: 
sudo aticonfig --initial

This is the result:
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

An alternate solution is to edit the xorg.conf file, here is my dilemma:
Which xorg.conf file do I edit? My X11 file shows 26 different versions. Some end with the date, some with numbers, some with failsafe, some with original, some with fglrx, some with failsafe.bak.

Additionally: 
How do I edit the xorg.conf file? gksudo gedit ./etc/x11/<filename> AND sudo gedit ./etc/x11/<filename> yield zilch, zero.

I just need to change Device section: string 'ati' to 'fglrx'

Background:
I have been trying to get my ATI Radeon 9250 graphics card to work for 3 days now. Minimal sleep, minimal water, minimal blinking have rendered me goofy.

Pat

---

### Post by jken146 on 2007-11-24
./etc would mean a hidden file.  You need ```
sudo gedit /etc/X11/xorg.conf
```

It might be a good idea to make a backup of that file first, i.e. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by pryan75 on 2007-11-24
Thanks for the quick reply jken.

```
sudo gedit /etc/X11/xorg.conf
```

Above code opens a blank gedit document. Big surprise, there is no xorg.conf file in my X11 folder. All instances of the xorg.conf file have an appended .<version> (eg= xorg.conf.3, xorg.conf.fglrx-0). Which one is the one being used by Ubuntu? Is there a way to tell? There's 26 different versions!

Thanks again for your help.

---

### Post by taurus on 2007-11-24
Can you post the output of this command from a terminal?

```
ls -la /etc/X11
```

---

### Post by overdrank on 2007-11-24
> **pryan75 said:**
> Thanks for the quick reply jken.

```
sudo gedit /etc/X11/xorg.conf
```

Above code opens a blank gedit document. Big surprise, there is no xorg.conf file in my X11 folder. All instances of the xorg.conf file have an appended .<version> (eg= xorg.conf.3, xorg.conf.fglrx-0). Which one is the one being used by Ubuntu? Is there a way to tell? There's 26 different versions!

Thanks again for your help.

Hi and be sure that is a Capital X  and I recommend the command ```
gksudo gedit /etc/X11/xorg.conf
```

Edit to slow Taurus has it in hand

---

### Post by pryan75 on 2007-11-24
Taurus, output of:** ls -la /etc/X11**

```
total 212
drwxr-xr-x  11 root root  4096 2007-11-24 15:08 .
drwxr-xr-x 128 root root  8192 2007-11-24 15:42 ..
drwxr-xr-x   2 root root  4096 2007-11-22 22:16 app-defaults
drwxr-xr-x   3 root root  4096 2006-08-05 19:21 config
drwxr-xr-x   2 root root  4096 2007-11-22 20:47 cursors
-rw-r--r--   1 root root    14 2006-08-05 19:32 default-display-manager
drwxr-xr-x   7 root root  4096 2007-11-22 19:34 fonts
-rw-r--r--   1 root root 17371 2007-08-16 21:12 rgb.txt
lrwxrwxrwx   1 root root    13 2007-11-22 13:07 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2007-11-22 19:38 xinit
drwxr-xr-x   2 root root  4096 2007-11-22 21:55 xkb
-rw-r--r--   1 root root  1785 2007-11-23 19:41 xorg.conf.1
-rw-r--r--   1 root root  3954 2007-11-23 20:53 xorg.conf.2
-rw-r--r--   1 root root  4262 2007-11-22 19:42 xorg.conf.20071122194208
-rw-r--r--   1 root root  4262 2007-11-23 01:09 xorg.conf.20071123010909
-rw-r--r--   1 root root  3954 2007-11-24 15:02 xorg.conf.20071124150203
-rw-r--r--   1 root root  7684 2007-11-23 20:56 xorg.conf.3
-rw-r--r--   1 root root  2438 2007-11-24 11:50 xorg.conf.4
-rw-r--r--   1 root root  3938 2007-11-24 14:19 xorg.conf.5
-rw-r--r--   1 root root  1774 2007-11-24 14:20 xorg.conf.6
-rw-r--r--   1 root root  3954 2007-11-24 14:22 xorg.conf.7
-rw-r--r--   1 root root  3919 2007-11-24 14:25 xorg.conf.8
-rw-r--r--   1 root root  4018 2007-11-24 14:29 xorg.conf.failsafe
-rw-r--r--   1 root root  1451 2007-11-23 01:42 xorg.conf.failsafe.1
-rw-r--r--   1 root root  4018 2007-11-23 01:43 xorg.conf.failsafe.2
-rw-r--r--   1 root root  1451 2007-11-23 19:43 xorg.conf.failsafe.3
-rw-r--r--   1 root root  3907 2007-11-23 19:44 xorg.conf.failsafe.4
-rw-r--r--   1 root root  1451 2007-11-24 11:52 xorg.conf.failsafe.5
-rw-r--r--   1 root root  1451 2007-11-24 14:21 xorg.conf.failsafe.6
-rw-r--r--   1 root root  1451 2007-11-24 14:23 xorg.conf.failsafe.7
-rw-r--r--   1 root root  1451 2007-11-24 14:29 xorg.conf.failsafe.8
-rw-r--r--   1 root root  3983 2007-11-24 14:23 xorg.conf.failsafe.bak
-rw-r--r--   1 root root  2438 2007-11-23 01:26 xorg.conf.fglrx-0
-rw-r--r--   1 root root  2378 2007-11-23 01:09 xorg.conf.original-0
-rw-r--r--   1 root root  7662 2007-11-23 20:56 xorg.conf.original-1
-rw-r--r--   1 root root  3941 2007-11-24 11:50 xorg.conf.original-2
-rw-r--r--   1 root root  2378 2007-11-24 15:02 xorg.conf.original-3
drwxr-xr-x   2 root root  4096 2007-11-22 21:52 Xresources
drwxr-xr-x   2 root root  4096 2007-11-22 22:21 xserver
-rwxr-xr-x   1 root root  4157 2006-10-12 11:33 Xsession
drwxr-xr-x   2 root root  4096 2007-11-24 15:33 Xsession.d
-rw-r--r--   1 root root   265 2006-06-11 23:40 Xsession.options
-rw-r--r--   1 root root    13 2007-07-24 05:59 XvMCConfig
-rw-------   1 root root   614 2006-08-05 19:20 Xwrapper.config
```

overdrank, thanks.

---

### Post by taurus on 2007-11-24
Why don't you reconfigure it again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pryan75 on 2007-11-24
Seems easy enough, why wouldn't they just have you do that in the how-to?

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository)

I'm with you, I ran:

```
sudo dpkg-reconfigure xserver-xorg
```

Auto detect graphics hardware: Yes. Shows driver as Intel and card name as Intel Integrated.

execute above code a second time but select 'No' for auto-detect: 

Auto detect graphics hardware: No. Shows driver as ATI and name as ATI Radeon 9200 Pro.

Can't seem to get 3d acceleration!
Some background..I have a Dell Dimension, with Intel onboard graphics accelerator and PCI ATI Radeon 9250. System Dual boots Ubuntu Gutsy and XP Pro. I have disabled the onboard in the BIOS..apparently to no avail as two graphics cards appear in System>Admin>Screens and Graphics. Restricted driver manager is supposed to show my ATI driver but doesn't. 
I meticulously followed the steps in the link above only to not be able to run ATIConfig or open xorg.conf. I guess I am right back to where I started?

Is editing the xorg.conf file directly any different than sudo dpkg-reconfigure xserver-xorg and selecting the driver? Is there a way to detect which xorg.conf file Ubuntu uses?

Thanks again.

---

### Post by pryan75 on 2007-11-24
I changed the ATI entry when running reconfigure xorg.conf. As coached to do by:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_.22restricted.22_Repository)

Upon reboot the screen flickers and I get pushed to safe graphics mode when I start up.

I tried the following: GLXGEARS
```

patrick@pryan75:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
Segmentation fault (core dumped)
```

GLXINFO
```

patrick@pryan75:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)
patrick@pryan75:~$ 
```

DIRECT INFO

```
patrick@pryan75:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
patrick@pryan75:~$ 
```


Can someone help? I'll upload any output, post files, anything. Just need to get ATI Radeon 9250 up and running. The goal is YES to direct rendering. 

Thanks.

> Is it possible to become even more new than you were before? A newer than new. That's how new I feel.

---

### Post by overdrank on 2007-11-24
I suggest if you are running Gutsy is get some sleep and we can attack it in another day. It took some work to get my 9600 running that I can not remember at the moment. So do not worry about the 26 xorg files and get some rest it will be there tomorrow. :)

---

### Post by pryan75 on 2007-11-25
Best solution I've seen posted.
I'm on tilt. Good night.

---

