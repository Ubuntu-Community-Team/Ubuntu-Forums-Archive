---
title: "upgrading from feisty to ubuntu studio?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-06-15
so i'm using feisty, and i was wondering if i could upgrade to ubuntu studio, and still keep all my current settings, i just got ubuntu around 3 weeks ago, and am finally set up the way i want it, but studio looks VERY nice as i'm doing audio work

---

### Post by Seisen on 2007-06-15
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")

There you go, have fun.:)

---

### Post by Killtown on 2007-06-27
Ok, #1 is throwing me for a loop.  Do I just paste the "sudo su -c 'echo..." line in the terminal and ignore the part before that?  I assume 2-4 you run through terminal.


1.  Add the following repository to your sources.list file:

> deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

OR run the following command:

> sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

2.  Add the repository GPG key by running the following command:

> wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add -

3. Update your repository information:

> sudo apt-get update

4. Install Ubuntu Studio:

> sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video

---

### Post by LancerDragoon on 2007-06-27
You kinda can't ignore the first part. What the first line wants you to do is edit your /etc/apt/sources.list and add the line into that file.

```
gksudo gedit /etc/apt/sources.list
```

Paste the line in and save it. It should work fine.

EDIT: Didn't notice the boolean operator OR there. :P I suppose you can ignore the first one, although that is the general method of adding sources to your system.

---

### Post by CherenkovBlue on 2007-06-27
yes, you can skip first part in number one and just type the second part in your terminal, and everything else there you type in to the terminal. 

there is a GUI to add  repositories and it can be found under system>administration>software sources

---

### Post by wolfen69 on 2007-06-27
why dont you just install the packages you need? then download the theme from gnome-look.org. why do people have to make things harder than they have to be?

---

### Post by Killtown on 2007-06-27
> **CherenkovBlue said:**
> yes, you can skip first part in number one and just type the second part in your terminal, and everything else there you type in to the terminal. 
Ok cool, did that and Studio is up and running!

Now, how do I change these god awful grey colors?  Yuck!  :x

---

### Post by LancerDragoon on 2007-06-27
System -> Preferences -> Themes

---

