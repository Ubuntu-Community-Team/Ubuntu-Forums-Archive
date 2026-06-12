---
title: "I've done something a little silly..."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by collierd45 on 2007-12-07
...again :p

I've removed the Add/Remove item from the Applications bar, any idea what the command is or how to get it back? I know I can use the Synaptic one in admin but it isn't nearlly as pretty haha

Ta

---

### Post by lamalex on 2007-12-07
right click on the menu => edit menus => select applications => check Add/Remove

---

### Post by banewman on 2007-12-07
The control center has a listing for"main menu"
you can click that and add it to the menu again.
:)

---

### Post by collierd45 on 2007-12-07
Can't find it, see the attached screenshot please ;)

God I miss windows sometimes [/blasphemy]

---

### Post by banewman on 2007-12-07
You might have to open synaptic and reinstall it.
it is under   control center-main menu - applications    for me
:)

---

### Post by collierd45 on 2007-12-07
Isn't there :(

---

### Post by banewman on 2007-12-07
I don't know what you did to remove it but since it isn't under control center-main menu-applications -... I can only suggest again that you open synaptic package manager and reinstall it.
:)

---

### Post by SeanHodges on 2007-12-07
```
sudo apt-get remove gnome-app-install
sudo apt-get install gnome-app-install
killall gnome-panel
```

---

### Post by hyper_ch on 2007-12-07
that's the perfect time to learn how to use apt-get through the terminal instead of using the gui version. What do you think? ^^

Basically you'll need two know two commands:

(1) Search the packages
```

apt-cache search KEYWORDS

```
That will search the package names and descriptions for your keyword.
e.g.
```

apt-cache search apache

```

As this will output a lot of info. The information to the left of the dash is the package name and the one on the rigth is the description.
You may want to save that into a text file:
```

apt-cache search apache > output.txt

```
That will create the output.txt file and all results will be stored there.

(2) Installation of programs
```

apt-get install PACKAGENAME

```
e.g.
```

apt-get install firefox

```
If you don't know the package name, search for it as in step 1.

You can install multiple packages at once:
 ```

apt-get intall rtorrent firefox kontact gaim

```

INSTEAD of apt-get for installtion you can also use "aptitude". The main difference is, that aptitude will also install, by default, the recommended additional packages while apt-get only installs the ones asked for and their dependencies.

---

### Post by Scarath on 2007-12-07
> **collierd45 said:**
> 

God I miss windows sometimes [/blasphemy]

If you were running windows you wouldnt have all that wondrous free software to 'add/remove' anyway :)

---

### Post by Teknyk on 2007-12-07
System > preferences > main menu.
Make sure "Applications" is highlighted
Click "New Item"
Name: Add/Remove
Command: /usr/bin/gnome-app-install

---

