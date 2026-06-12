---
title: "install kde"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-09-05
Hi all..
Ijust tried to install kde sudo apt-get kubuntu-desktop as the ubuntu guide says to do.

Now next to my system tray i am getting an orange update icon that says

An error ocucred please run package manager from the right click menu or apt-get terminal to see what is wrong The error message was 'Error broken count > 0'

Any idea how to fix this?

---

### Post by bakert on 2006-09-05
Not seen that before.  My rather simpleminded suggestion is to try this in a terminal:

    ```
$ sudo apt-get remove kubuntu-desktop
```
    ```
$ sudo apt-get clean kubuntu-desktop
```

You might then check and see if the problem has gone.  If it has you probably want to do this:

    ```
$ sudo apt-get install kubuntu-desktop
```

Which may of course bring the problem back.

No idea if this will work, but it's something to try if you don't get more educated answers!

---

### Post by bruce89 on 2006-09-05
DO NOT install kubuntu-desktop with apt-get, if you want to remove it see this - [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

You should install it with this command:
```
sudo aptitude install kubuntu-desktop
```
If you install/remove it with apt-get, it won't actually uninstall KDE, only the meta-package.

---

### Post by cjnkns on 2006-09-05
Thanks! it seems to be acting better now. 
When I intially attempted to install i was told there were a handfull of packages that would not be installed and to try and to a sudo apt-get -f install or something like that. But ran through your suggestion it seems to be working now.. 

Thanks.

---

