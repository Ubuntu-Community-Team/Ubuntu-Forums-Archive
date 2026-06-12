---
title: "Ktorrent2.2.4 installation help."
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by b.jonkers on 2007-12-17
Hi all.  

I am not sure if this should be here or not.  I am fairly new to linux but i understand how to do most stuff.

I was trying to install ktorrent.  I started but using the add/remove but when i click on ktorrent   it says.

The List Of Applications Is Not Availible.
Click on reload to reload it.  You need a working internet connection. bla bla.

There is no reload button but there is a refresh button.  I click on it and it says

Downloading package information.

then there is like 6 files and the progress bar moved across and then it shuts doen the list refresh's.  So i click on ktorrent again and it does it all again.  I then figured i would give it a go manually.  So i download and extract the .tar.gz.

I head for the terminal window and i cd over to the place i have it ./configure but then i get an error

configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

if anybody can help with me installing this it would be great

---

### Post by renzokuken on 2007-12-17
are you using gnome or KDE as a desktop?

installing ktorrent from source in gnome is going to be a lot of work.

open up the terminal and have a go with

```
sudo apt-get install ktorrent
```

---

### Post by b.jonkers on 2007-12-17
that did not work either.  i get this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ktorrent


also i am using gnome.  I figured i could install the kde desktop and it would work.

---

### Post by renzokuken on 2007-12-17
you dont need the whole kde desktop, just the libraries

do you have universe and multiverse repos enabled? if not do the first part of this [http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

then run ```
sudo apt-get update
``` and again try ```
sudo apt-get install ktorrent
```

---

### Post by b.jonkers on 2007-12-17
thanks heaps for the help.  That did the trick.

Since i am only new to this how thing.  When i changed the settings on the synaptic packet manager.

Did that just allow apt-get to get programs from other places? and

```
sudo apt-get update
```

just updated the new packages that where availible?

---

### Post by renzokuken on 2007-12-18
> **b.jonkers said:**
> thanks heaps for the help.  That did the trick.

Since i am only new to this how thing.  When i changed the settings on the synaptic packet manager.

Did that just allow apt-get to get programs from other places? and

```
sudo apt-get update
```

just updated the new packages that where availible?

thats about the sum of it yeah.......congrats

---

