---
title: "How do I get permission to edit sources.lst ?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Revmann on 2007-01-31
I screwed up installing Automatix and it tells me I have an error on line 34 of sources.list in apt folder. Ok, thats no problem. I found it and am trying to edit the file so I can remove the line, then remove the screw up I made while fixing the line :P Anyways, it tells me I don't have the permissions to save the file. I just put Edgy on this comp a few hours ago and am the only user. How do I get the permission to edit this file back to original? Or how do I fix it if I can't?

---

### Post by jocheem67 on 2007-01-31
sudo gedit /etc/apt/sources.list.

Now you're administrator thanks to "sudo" and you can edit your sources.

---

### Post by randomnumber on 2007-01-31
sudo nano filename

or 

gksudo gedit filename

in a terminal

you probibly want the  second

terminal is located in applications->assescories->terminal

---

### Post by ComplexNumber on 2007-01-31
> **jocheem67 said:**
> sudo gedit /etc/apt/sources.list.

Now you're administrator thanks to "sudo" and you can edit your sources.
don't use sudo for a graphical application. gksudo should be used for ALL graphical applications.  Revmann should type in the following instead:
**gksudo gedit /etc/apt/sources.list**

---

### Post by 23meg on 2007-01-31
> **jocheem67 said:**
> sudo gedit /etc/apt/sources.list.

Now you're administrator thanks to "sudo" and you can edit your sources.For graphical applications such as Gedit, *gksudo* should be used instead of *sudo*.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mjm115 on 2007-01-31
If you are using Ubuntu, in a terminal type:

> sudo gedit /etc/sources.lst


If you are using Kubuntu, in a terminal type:

> kdesu kate /etc/sources.lst


Either way, in order to edit this file, you must have super-user privileges.

---

### Post by randomnumber on 2007-01-31
> **jocheem67 said:**
> sudo gedit /etc/apt/sources.list.

Now you're administrator thanks to "sudo" and you can edit your sources.

i understand that you are not supposed to use sudo on graphic applications, that you are supposed to use gksudo

Anyway, i would recommend gksudo for gedit.

---

### Post by saadakhtar on 2007-01-31
open your terminal
Applications ==> Accessories ==> Terminal

type in:
sudo nano /etc/apt/sources.list

changes the repository sources is critical change so you need to be root to do that. the sudo command gives to root access to the system.
after the above command you will need to type in the root password to proceed.

enjoy your ubuntu

cheers

---

### Post by 23meg on 2007-01-31
[QUOTE= saadakhtar
]after the above command you will need to type in the root password to proceed.[/QUOTE]Not the root password (there's none by default), but your user password.

---

### Post by ComplexNumber on 2007-01-31
**revmann**
another point to note. make a backup copy of the original file first. call it something like:
**sources.list.bk1**

---

### Post by Revmann on 2007-01-31
Thanks all. I appreciate the help.

---

### Post by saadakhtar on 2007-01-31
> **23meg said:**
> Not the root password (there's none by default), but your user password.

sorry typo in a hurry.
and please dont forget to make a backup copy of the sources file.
it is usually a good practice becuase it can save you a lot of time and frustration if something goes wrong.
the copy command is "cp".

---

