---
title: "How do I know where to access a program I just installed?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by caljohnsmith on 2008-03-19
If I just installed a program with the "Add/remove Applications" manager, how do I know where to look for it? I'm used to Windows where you can choose where in your Start menu you want to add the program (or not at all for that matter) when you install the program. 

In Ubuntu it seems some programs show in the Applications menu, while others don't. If I have to access the program from the command line, how do I know exactly what the command is? And how can I find out exactly where all the files for the application were installed? 

Thanks for any help!

---

### Post by (((X))) on 2008-03-19
In most cases application name and command are the same.
It is better you install applications via synaptic package manager, it lets you look at the output(when you install or delete an application).
This way you will know name of application.

---

### Post by 1875 on 2008-03-19
Once you know your apps name/launch command right click on your menu and edit menu. You can then create a launcher for the app.

---

### Post by jan quark on 2008-03-19
what is the name of your program?

when you have installed ti via synaptic ( but also via the add/remove thing) you can search for it in synaptic, then right click on the entry, go to properties and installed files

there you will see all locations where the files of the app were installed to

the executables are usually in 

usr/ bin
usr/ share

---

### Post by caljohnsmith on 2008-03-19
Thanks so much for the replies, (((X))), 1875, and Jan Quark! I will use Synaptic from now on so I can see where the app is installed. And thanks for the tip about adding a launcher for the app in the Applications menu, 1875. 

But if the application does install a launcher in the applications menu, is there a better way of trying to find that out other than by looking thru all the menu items? I'm just surprised there is no control over this when I install a program.

---

### Post by Oldsoldier2003 on 2008-03-19
> **caljohnsmith said:**
> Thanks so much for the replies, (((X))), 1875, and Jan Quark! I will use Synaptic from now on so I can see where the app is installed. And thanks for the tip about adding a launcher for the app in the Applications menu, 1875. 

[COLOR="Red"]But if the application does install a launcher in the applications menu, is there a better way of trying to find that out other than by looking thru all the menu items? I'm just surprised there is no control over this when I install a program[/COLOR].

Thats because the package mainatiners don't always set things up the way you would expect. some package maintainers don't even install their programs to the menus...

---

### Post by oldos2er on 2008-03-19
Nine times out of ten, when you use Synaptic or apt-get to install a program, the executable is installed to /usr/bin .

---

