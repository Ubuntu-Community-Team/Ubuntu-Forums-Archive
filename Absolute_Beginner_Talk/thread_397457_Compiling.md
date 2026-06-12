---
title: "Compiling"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-03-30
I can't use the repositories for the programs I've wanted to download so far, GimpShop and Avant-Window-Navigator.

I've downloaded the .tar files for them and every single post and tutorial I have read errors when I try it.  Is there any applications that make this easier?  I can't seem to grasp the whole terminal thing.

---

### Post by bodhi.zazen on 2007-03-30
> **c-breakdown said:**
> I can't use the repositories for the programs I've wanted to download so far, GimpShop and Avant-Window-Navigator.

I've downloaded the .tar files for them and every single post and tutorial I have read errors when I try it.  Is there any applications that make this easier?  I can't seem to grasp the whole terminal thing.

LOL

Open a terminal.

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```

download the source code, unpackage.

Open a terminal, cd into the package directory.

Now, 

[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
[*]List the options: ```
./configure --help | less
```You may scroll through the outoput with up and down arrows, page up, page down ... 
Type q to exit less.


[*]./configure --prefix=/usr
[*]make
[*]sudo checkinstall[/list]

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by c-breakdown on 2007-03-30
I followed your directions exactly, and it said that it did install it, however the program errors when I try to load it. 

So can you tell me how I go about uninstalling this non-working application now?

Those links you gave don't even help me in the slightest.  I've tried multiple things off of there only to get errors.  There is no application that makes this possible for people new to linux to do?

---

### Post by fenian on 2007-03-30
[This page]("http://www.cutlersoftware.com/ubuntuinstall/") might be of helpto you.

---

### Post by bodhi.zazen on 2007-03-30
> **c-breakdown said:**
> I followed your directions exactly, and it said that it did install it, however the program errors when I try to load it.

So can you tell me how I go about uninstalling this non-working application now?

LOL

Error message ?

To uninstall, assuming you used checkinstall :

```
sudo aptitude uninstall <program_name>
```

Or open synaptic, search for the program name, uninstall via synaptic.

---

### Post by c-breakdown on 2007-03-30
I uninstalled it then reinstalled it and when I try to launch it nothing at all happens.  I rebooted and tried to launch it again, same thing.

---

### Post by bodhi.zazen on 2007-03-30
For Avant-Window-Navigator : [http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

I downloaded "gimpshop" and it looks like gimp. It unarchived to "gimp-2.2.11"

Try typing gimp into a terminal.

---

