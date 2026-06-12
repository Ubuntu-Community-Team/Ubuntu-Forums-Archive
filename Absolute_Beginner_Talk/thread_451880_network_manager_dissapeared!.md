---
title: "network manager dissapeared!"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-05-22
the default network manager that comes with 7.04 disappeared!
if you don't know what i'm talking about it's the indicator that tells you the strength of your wireless connection, and makes it easier to connect to wireless, and so the wireless roaming options is not working for some reason!
any help?
thanks

---

### Post by %hMa@?b&lt;C on 2007-05-22
if you are on gnome, right click on any gnome-panel you will see it in the "add to panel" menui

---

### Post by Mazen on 2007-05-22
yes and there there is network manager, but that's not the one i mean, the one i want is the one that comes with ubuntu by default, you can click on it and it will display all  the connection in range right away and u just have to click on the connection to get to it.

---

### Post by RomeReactor on 2007-05-22
Hi. Mazen, what you're looking for is "Notification Area".

---

### Post by Mazen on 2007-05-22
i added that, but it's an empty separator

---

### Post by RomeReactor on 2007-05-22
make sure the graphical applet is installed; look for **network-manager-gnome** in Synaptic. If it *is* installed, try launching it manually through the terminal:
```
nm-applet
```

---

### Post by Mazen on 2007-05-22
this is what i get when running this in terminal> error while loading shared libraries: libnm-util.so.0: cannot open shared object file: No such file or directory


---

### Post by RomeReactor on 2007-05-22
Looks like you're missing a library; from the terminal:
```
sudo apt-get install libnm-util0
```
Once it's installed, run nm-applet again.

---

### Post by Mazen on 2007-05-22
already installed!!!!

---

### Post by Mazen on 2007-05-23
any other suggestions!??!?

---

### Post by ugm6hr on 2007-05-23
Might be worth going to Add/Remove... and then uninstalling and reinstalling Network Manager.  Then reboot, and try running nm-applet again.  

Looks like something unusual has happened to that requested lib file - so if you can find how to just reinstall that, it might be quicker.

Sorry if it doesn't help.

---

### Post by Mazen on 2007-05-23
thanks for the help but doesn't seem to change much!!
at first it took time to load this thing at startup and then it went out for some reason!
i don't think it's network-manager i'm looking for!

---

### Post by Mazen on 2007-05-23
??

---

### Post by ugm6hr on 2007-05-23
Maybe try uninstalling "libnm-util0" from Synaptic (just search for it) - and then reinstall?  There is clearly an issue with this lib if nm-applet won't run and gives an error regarding not finding files related to this lib.

In case you want to check - the i386 components of libnm-util0:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libnm-util0&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libnm-util0&version=feisty&arch=i386)

---

### Post by Mazen on 2007-05-24
Got it!

---

### Post by fain on 2007-05-29
ya i have the same problem. i just booted up tonight and it was gone :(


oops didnt see page 2 mabad

---

