---
title: "Speeding up the boot process"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bobd104 on 2007-11-09
Hello Anyone with knowledge of how to change file permissions in UBUNTU.  I need to make a change in the menu.lst system file but obviously don't have the correct owner privileges.  How can I get permission to make the change in this file to speed up the boot process if I'm not the owner?  The owner is "root".  Thanks. . .

Bob D.

---

### Post by kevinatkins on 2007-11-09
Hi,

I'm not quite sure what you want to achieve here.. By speeding up the boot process, what do you mean?

---

### Post by bobd104 on 2007-11-09
When I initially boot the computer it takes so darn long to get to the username and password.  I read in a thread that if you remove certain elements of the menu.lst file it speeds this process up significantly.  Problem is, I don't have permission to make changes to this file? ? ?

---

### Post by Paul820 on 2007-11-09
From the teminal
> sudo gedit /boot/grub/menu.lst
It will ask you for your pasword. Enter the password you use to login. **Don't** change the file permission, it's a security risk.
**Be very careful** what you change in there or you could wreck your sytem. Make a backup:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

---

### Post by Paul820 on 2007-11-09
You can also try this to speed up the boot process. From synaptic, search for **startupmanager**
Then go to System->Administration->Startup-Manager and in the screenshot where it is highlighted, find the resolution that closely matches your monitor resolution and select it. Close the app and reboot.

---

### Post by Kitsun on 2007-11-09
Keep a Live CD handy in case things go wrong.

Paul80: That is known to cause problems in Gutsy, what happens is that the consoles (ctrl-alt-1etc) don't display anything.

Just change the resolution back to the default if you have problems.

---

### Post by bobd104 on 2007-11-09
Paul, your suggestion worked fine.  I thank you very much.  I've been a windows user all my life and getting used to using Linux has added fun to my computing experience again.  A lot like the old DOS days. . .

Bob D.:)

---

### Post by Paul820 on 2007-11-09
No problem bobd104, maybe you can get on with messing with linux now it doesn't take ages to boot. Have fun :)

---

### Post by genbuntu on 2007-11-09
> **Paul820 said:**
> You can also try this to speed up the boot process. From synaptic, search for **startupmanager**
Then go to System->Administration->Startup-Manager and in the screenshot where it is highlighted, find the resolution that closely matches your monitor resolution and select it. Close the app and reboot.

Just curious, is there an equivalent of startupmanager for fiesty? Couldn't find it in my synaptic repos.

---

### Post by skymera on 2007-11-09
[www.getdeb.net](www.getdeb.net)

---

### Post by boriquajake on 2007-11-10
> **skymera said:**
> [www.getdeb.net](www.getdeb.net)

As I am becoming more and more aware, I am an idiot. I have no idea what your post means. I went to [www.getdeb.net](www.getdeb.net) and I don't see anything related to my issue. Help

---

### Post by genbuntu on 2007-11-10
Select your distribution (e.g. fiesty, gusty ...) , and search for the package you need (e.g. startup manager) . Personally, I didn't find startup manager helpful (and now am figuring out how to remove it).

---

### Post by Paul820 on 2007-11-10
To remove it > sudo apt-get remove startupmanager

---

### Post by jaybombalous on 2007-11-10
> **Paul820 said:**
> To remove it


i'd use..

```
sudo dpkg --purge remove startupmanager
```


yep

just do a 

```
dpkg --help
```

to see all the commands u can throw it or maybe understand what I just typed ^^^

---

### Post by Paul820 on 2007-11-10
You missed **remove** from the middle of --purge and startupmanager :)

---

### Post by jaybombalous on 2007-11-10
duh :)

---

### Post by Paul820 on 2007-11-10
A
> sudo apt-get --purge startupmanager
on it's own will not work, it has to be
> sudo apt-get --purge remove startupmanager
to remove the program and config files.

---

### Post by genbuntu on 2007-11-11
No guys, it won't work. (I think these commands work only if the package is installed via "./configure> make>make install" procedure). 
But I installed it from source file by typing ```
python setup.py install
``` , and so am wondering how to uninstall it . :confused:

See my other thread where I ask this question:
[http://ubuntuforums.org/showthread.php?t=608411](http://ubuntuforums.org/showthread.php?t=608411)

---

