---
title: "how do i add a repository"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-24
Hello i am trying to install beryl everything is going well until i get to the part when i am supposed to add the beryl repository to the /etc/apt/sources.list

how do i do this, need exact commands to write in the terminal. this is the repository that i want to add

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by shareMenaPeace on 2007-02-24
open the file from the terminal with

```
gksudo gedit /etc/apt/sources.list
```

Add the line somewhere on the bottom and close/save.

---

### Post by hempa on 2007-02-24
> **shareMenaPeace said:**
> open the file from the terminal with

```
gksudo gedit /etc/apt/sources.list
```

Add the line somewhere on the bottom and close/save.
 
i am using kde. do i still use gedit??

---

### Post by shareMenaPeace on 2007-02-24
Oops, well its diffrent and i dont know what exactly :/

Another way no grafical editor.
> 
sudo nano -B /etc/apt/sources.list
-B creates a backup file.

---

### Post by FyreBrand on 2007-02-24
> **hempa said:**
> i am using kde. do i still use gedit??If you want to edit your sources.list manually:  Start Konqueror and navigate to /etc/apt/.  Right click the sources.list file and select Actions --> Edit As Root, from the context menu.  This should fire up a dialog box asking for your password and then start kwrite in root mode.

You can also edit from Adept Package Manager if you use that tool.  I like to edit it manually because, well I just do.

Here is a thread in the Ubuntu Customization Guide forum that talks about adding repositories: [**Ubuntu_Demons Edgy Customization Guide (A Work In Progress)**]("http://www.ubuntuforums.org/showthread.php?t=281825").

Have fun.

---

### Post by shareMenaPeace on 2007-02-24
Or use

System -> Administration -> Software Sources

Add the repository under the 3rd party tab.

And dont forget to add the key aswell - as stated in the tutorial.

---

### Post by FyreBrand on 2007-02-24
> **shareMenaPeace said:**
> Or use

System -> Administration -> Software Sources

Add the repository under the 3rd party tab.

And dont forget to add the key aswell - as stated in the tutorial.
There isn't a Sys->Admin->Software Sources in Kubuntu.  Adept Package Manager is in the Sys->Admin menu and that is how you manage your repos in gui in KDE.  I suppose you could go to add/remove programs and then enter advanced mode, but that is just starting Adept a different way.

I looked around at some obscure info and configuration tools in the menu and I don't see any other way to manage the repos graphically outside of Adept.  If you find one post it.  It would be nice to know.

---

