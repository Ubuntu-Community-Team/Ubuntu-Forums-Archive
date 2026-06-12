---
title: "install window manager"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-02-26
How to install flux box, ice wm and enlightenment from net so that it also automatically configures the gdm to have them as sessions?

pls tell in steps briefly

---

### Post by raevin on 2007-02-26
Download the package(s)....install them.

Log out (aka: end session), click "Options", choose whatever DM you want to use.

That's the brief way.

---

### Post by sankarv on 2007-02-26
i need the commands to donwload/install them. pls help

---

### Post by halitech on 2007-02-26
check here

[http://www.ubuntuforums.org/showthread.php?t=20216]("http://www.ubuntuforums.org/showthread.php?t=20216")

and here

[http://seerofsouls.com/ubuntu.html]("http://seerofsouls.com/ubuntu.html")

---

### Post by Luk0r on 2007-02-26
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install fluxbox
sudo apt-get install enlightenment
sudo apt-get install icewm
```

---

### Post by energiya on 2007-02-26
> **Luk0r said:**
> ```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install fluxbox
sudo apt-get install enlightenment
sudo apt-get install icewm
```

better replace "apt-get" with "aptitude". It will be more easy to uninstall, because aptitude also removes unused packages, so if you want to uninstall just
```

sudo aptitude purge package_name

```

---

### Post by Luk0r on 2007-02-26
Or just do
```
sudo apt-get autoremove
```
;)

---

### Post by tcrroadie on 2007-02-27
> **sankarv said:**
> How to install flux box, ice wm and enlightenment from net so that it also automatically configures the gdm to have them as sessions?

pls tell in steps briefly

Additional window manager such as Fluxbox, icewm, and Enlightenment can easily be intalled with apt.  Example code would be as follows. 
 
To install Fluxbox 
```

sudo apt-get install fluxbox
``` 

To install icewm
```

sudo apt-get install icewm
```

Apt will create a menu entry in GDM for any additional window managers or Desktop environments that you install.  If you would like to also install the KDE desktop or XFCE you would run
```

sudo apt-get install kubuntu-desktop
```

```
sudo apt-get install xubuntu-desktop
```

As an added note, if you would like to try Enlightenment E17 please do not try installing E17 using the guides listed in the previous post.  If you would like to install E17 please use the guide I created.  Installation is simply copy and past in a terminal.  You can find my guide for installation of E17 here or in my signature. 

[http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17)

---

### Post by bodhi.zazen on 2007-02-27
> **Luk0r said:**
> Or just do
```
sudo apt-get autoremove
```
;)

I think this is true of Edgy and higher, but not dapper.

> **tcrroadie said:**
> As an added note, if you would like to try Enlightenment E17 please do not try installing E17 using the guides listed in the previous post.  If you would like to install E17 please use the guide I created.  Installation is simply copy and past in a terminal.  You can find my guide for installation of E17 here or in my signature. 

[http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=319336&highlight=e17)

And thank you for that guide.

As as off-topic If you would like to see Enlightenment take a look at Elive or  AUSTRUMI

[http://cyti.latgola.lv/ruuni/index_en.html](http://cyti.latgola.lv/ruuni/index_en.html)

---

