---
title: "installing apps?"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-04-29
Hello,

I finally got my wireless working....woohoo and thanks for all the help! So now I want to install programs. How do i do that in Ubuntu? Specifically i am trying to intstall XMMS but it would be good to know the general procedure... or if someone knows some good tutorials that's great too (i must be typing in all the wrong key words). I already downloaded the "package" (tar.gz) and extracted it.

Thanks,

Maria

---

### Post by halfvolle melk on 2006-04-29
You can use Synaptic for that rather than downloading tars.
Click "System -> Administration -> Synaptic Package Manager" and search for stuff.
XMMS is in the Universe rpository if I'm correct. Check this link to add the repository: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

edit: I am mistaken. It appears to be in Main. When this repo is enabled, you can also type this in a terminal:
```
sudo apt-get update
sudo apt-get install xmms
```

---

### Post by cilynx on 2006-04-29
The whole glory of Ubuntu is the package management system (borrowed from Debian).  For most anything a normal user would want, you don't have to go get the tar.gz from the developer.  If you like the graphical world, Applications->Add/Remove is a simple front end to installing applications.  System->Administration->Synaptic Package Manager is a more advanced GUI.  If you like the command line, "apt-get" is your friend.  Installing xmms on the command line is as simple as:
```

sudo apt-get install xmms

```
If you find .deb packages (Debian / Ubuntu formatted software packs) out on the net, you can download them then install with dpkg on the command line or GDebi in the GUI.

Good luck and welcome to the fold...

---

### Post by garner_nc on 2006-04-29
By far, the easiest way to install new programs is to use Synaptic. You'll find it under System > Administration >Synaptic Package Manager. Most programs you need will be listed there. Simply mark the desired program for installation and then apply changes. 

All the Best,
Doug White

---

### Post by Maria_Firewire on 2006-04-29
WOW, command line is way better than double-clicking and gettting an install wizard in windows...that was fast and COOL.

Thanks again! I think I'm starting to like this whole linux thing. :D 

Maria

---

### Post by garner_nc on 2006-04-29
Don't hesitate to ask questions! This is the friendliest Linux forum I've ever been on. It's a great group of people.

All the Best,
Doug White

---

### Post by halfvolle melk on 2006-04-29
[QUOTE=Maria_Firewire]WOW, command line is way better than double-clicking and gettting an install wizard in windows[/QUOTE]
Yeah, the command line is all that. Be sure to check out these:
```
sudo apt-get search [whatever type of program you want to search for]
sudo apt-get policy [a specific package name]
apropos [whatever type of command you want to search for]
man [a specific command name]
```

---

