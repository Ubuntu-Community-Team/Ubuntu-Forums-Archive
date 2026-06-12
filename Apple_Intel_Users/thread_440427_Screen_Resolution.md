---
title: "Screen Resolution"
date: 2007-05-11
forum: Apple Intel Users
---

### Post by liberalist on 2007-05-11
I know this has been asked before, but none of the proposed solutions helped on my iMac Intel Core 2 Duo machine. I have installed fglrx on my Xubuntu 7.04 installation, but I still can't get the resolution higher than 1024*768 (in the display settings). My graphics card is an ATI Radeon X1600 and I have 128 MB video memory.

How can I solve this problem? The highest resolution of my screen is 1440*900, but I prefer 1152*720 for readability. Thank you very much in advance.

---

### Post by Greywhind on 2007-05-11
I don't know a definite solution to your problem, but my resolution worked once I had FGLRX installed correctly. Open a terminal and try the command:
glxinfo | grep direct

If it says Direct Rendering: Yes, then you have FGLRX installed right.

Also, what method did you use to install the driver? I used the "Restricted Manager" that's found in System->Administration. It worked, and it was easy.

---

### Post by liberalist on 2007-05-12
> **Greywhind said:**
> I don't know a definite solution to your problem, but my resolution worked once I had FGLRX installed correctly. Open a terminal and try the command:
glxinfo | grep direct

The terminal could not find this command. 

> **Greywhind said:**
> Also, what method did you use to install the driver? I used the "Restricted Manager" that's found in System->Administration. It worked, and it was easy.
I used the Synaptic Package Manager. When I use the Restricted Driver Manager, it says that my system does not need any restricted drivers. Now, the Restricted Driver Manager is gone too.

---

### Post by kelvin spratt on 2007-05-12
their is a program loosely called resulution switcher its in synaptic manager this will give an icon in the top
panel when activated from acessories this gives all screen resulution uptions for your curent set up give it a try before ghanging reg entries

---

### Post by liberalist on 2007-05-12
> **kelvin spratt said:**
> There is a program loosely called resolution switcher its in synaptic manager this will give an icon in the top
panel when activated from acessories this gives all screen resulution uptions for your curent set up give it a try before changing reg entries

I searched for both resolution and resolution switcher, but it yielded no results in the synaptic package manager. Thank you very much anyway.

Installing FGLRX from the command line might solve my problem, but how do I do this? Other solutions are appreciated as well.

---

### Post by heimo on 2007-05-12
What do you see if you run xrandr on terminal? Could you show us Device, Monitor and Screen sections from /etc/X11/xorg.conf?

---

### Post by nicfagn on 2007-05-12
I read somewhere about displayconfig-gtk for changing display parameters. I did not try it myself though.

---

### Post by liberalist on 2007-05-12
> **heimo said:**
> What do you see if you run xrandr on terminal? Could you show us Device, Monitor and Screen sections from /etc/X11/xorg.conf?

```
ubuntu@ubuntu:~$ sudo xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 372mm x 232mm )  *61
 1    800 x 600    ( 372mm x 232mm )   61
 2    640 x 480    ( 372mm x 232mm )   61
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ cd /etc/X11/xorg.conf
bash: cd: /etc/X11/xorg.conf: Not a directory
```

Thanks again for all your kind help.

---

### Post by heimo on 2007-05-12
> **liberalist said:**
> ```

bash: cd: /etc/X11/xorg.conf: Not a directory
```

less or cat will give better results (instead of cd)

---

### Post by liberalist on 2007-05-13
The results of less /etc/X11/xorg.conf and cat /etc/X11/xorg.conf are attached in the documents below.

---

### Post by svenand on 2007-05-14
Here is what I did to change the screen resolution when using Parallels Desktop.
[http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html)  Look for Changing screen resolution.

Sven

---

### Post by liberalist on 2007-05-14
Thank you, but this method failed in my case, svenand.

---

### Post by kaveh1000 on 2007-05-17
I also tried this, but my maximum res is still 1024.

---

### Post by heimo on 2007-05-17
Sometimes you get good information from log file (especially look at lines with EE or WW):
```
/var/log/Xorg.0.log
```

---

### Post by nicfagn on 2007-05-17
Have you tried this?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
The above should allow you to select the resolutions you want from a list (leave the rest as it is).

---

### Post by liberalist on 2007-05-23
Yes, I have tried the above, but then Ubuntu fails to start. It also fails to start if I try the method described in the post [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) . What should I do?

---

