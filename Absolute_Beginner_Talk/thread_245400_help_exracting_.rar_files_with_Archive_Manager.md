---
title: "help exracting .rar files with Archive Manager"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-08-27
I have some old backup files that are .rar's  from my previous windows install, when I try to extract them with Archive manager it says, "archive type not supported." Does anyone know how to get support for .rar's with Archive manager or what other tool one could use to extract them? Thanks in advance

---

### Post by toasted on 2006-08-27
Open Synaptic and install unrar  :)

---

### Post by cptjaben on 2006-08-27
is unrar command line only? or does it have a graphical interface also?

---

### Post by annda on 2006-08-27
the archive manager should be able to extract rar files after you install unrar, because it acts as a frontend to underlying programs. so you'd be using your familiar graphical interface and it will take care of deploying unrar on its own. you don't need an extra gui.

---

### Post by cptjaben on 2006-08-27
Okay everything seems to be working now, Thanks for the help.

---

### Post by Sabrage on 2006-09-04
i have the same problem with rar using archive manager but i have changed the user settings so that i no longer have synaptic in the menu.](*,) 

how can i get synaptic back so i can install unrar?

---

### Post by skymt on 2006-09-04
Right click on the Applications menu and choose Edit Menus. Choose System > Administration in the left panel, and check Synaptic in the right panel.

If it's not there, choose File > New Entry. Name is "Synaptic", Command is "gksudo synaptic".

Then you can get to Synaptic from System > Administration > Synaptic.

---

### Post by Sabrage on 2006-09-04
thanks skymt,

this is strange. in the menu editor synaptic was already listed and checked visible, along with some other apps that no longer show in my system > administration menu after i disabled administrator mode in system > administration > user/groups a few days ago. i did this because i read somewhere that normal users should not have these priveliges. 

will i have to change back my user settings to see synaptic and user/groups on my desktop menu? of course, one of the items i lost was system > administration > user/groups.:-D

---

### Post by skymt on 2006-09-04
Usually, if you want to run as an unprivileged user, you make sure you also have a privileged account for this kind of administration. Are you saying you don't have any accounts with administrator privileges?

If this is the case, here's what you do to get your rights back:

* Reboot, and choose recovery mode from the boot menu
* Enter the following commands: ```
adduser *username* admin
reboot
```Note that if you do this, you should write the commands down first. You'll boot to a command prompt, so you won't have a web browser to look them up.

---

### Post by Sabrage on 2006-09-04
thanks again skymt. i had no idea i needed another user for admin purposes, but i sure makes a lot of sense now. 8)

i'm gonna enter recovery mode now, and i'm doing this for all the unprivileged users out there. viva la revolution!

---

### Post by Sabrage on 2006-09-04
i'm back. i installed the unrar-free package with synaptic but archive manager still says archive type not supported?

any ideas anyone?

---

### Post by IcebergDK on 2006-09-14
Well I think this'll do it. It worked for me anyway

In Synaptic Package Manager click Settings -> Repositories then click Add and  then Custom and paste this line:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

Then you should be able to see another unrar in the Synaptic Package Manager

---

### Post by transient on 2006-09-21
Or you can just get the deb package from here:
[http://packages.ubuntu.com/dapper/utils/unrar](http://packages.ubuntu.com/dapper/utils/unrar)

And then install it.

.
e

---

### Post by CatKiller on 2006-09-21
> **Sabrage said:**
> i'm back. i installed the unrar-free package with synaptic but archive manager still says archive type not supported?

any ideas anyone?
I can make and extract .rar files using Archive Manager, and I don't have either the **unrar** or **unrar-free** packages installed. I do have the **rar** package installed though, so maybe that will help you.

---

### Post by itguy on 2006-09-28
Installing the rar package solved the problem for me.  Thanks for the help!

---

### Post by CatKiller on 2006-09-28
No worries. Glad it worked for you.

---

