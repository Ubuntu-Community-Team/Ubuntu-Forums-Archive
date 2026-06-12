---
title: "gtkpod install"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-05-17
I would like to install gtkpod.  I have downloaded it and tried reading through the directions that I found in the downloaded file, but I didn't get very far at all.  What is the best way to install this?  I have never installed anything on this PC since my Ubuntu install a few weeks ago.  I am not too familiar with terminal commands so please be specific if that's what the installation of this program involves.

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=abbrew]I would like to install gtkpod.  I have downloaded it and tried reading through the directions that I found in the downloaded file, but I didn't get very far at all.  What is the best way to install this?  I have never installed anything on this PC since my Ubuntu install a few weeks ago.  I am not too familiar with terminal commands so please be specific if that's what the installation of this program involves.[/QUOTE]
In terminal (Applications > Accessories > Terminal) type:
> 
sudo apt-get install gtkpod

Start it from under Applications > Sound & Video > Gtkpod.

Edit: Are you trying to compile it from source ? If so go to [ here ](http://www.psychocats.net/ubuntu/installingsoftware.php) and follow section 4, compile from source.

---

### Post by benuski on 2006-05-17
It works just fine if you download it from the Synaptic Package Manager under the administration tab under the system menu.  Thats how I got it and it works perfectly.

---

### Post by abbrew on 2006-05-17
Maybe I didn't download it?  Terminal displays  
[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod[/I]
With the Synaptic Package Manager I couldn't even find the program.  I am a very confused Ubuntuer!  Sorry!  Thanks for the help so far.

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=abbrew]Maybe I didn't download it?  Terminal displays  
[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod[/I]
With the Synaptic Package Manager I couldn't even find the program.  I am a very confused Ubuntuer!  Sorry!  Thanks for the help so far.[/QUOTE]
Check out [ this ](http://www.psychocats.net/ubuntu/sources.php) tutorial. It shows you how to add extra repositories. Read the tutorial carefully because it has the sources.list for both breezy and dapper.

---

### Post by abbrew on 2006-05-17
Terminal read:
[I]alex@ubuntu:~$  sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update
cp: `update': specified destination directory does not exist
Try `cp --help' for more information.
[/I]

Uh . . . is this OK?  I think I have done something wrong!  Yikes!  Thanks for your assistance thus far.

---

### Post by abbrew on 2006-05-17
Thank you all!!!!!!!!!  It works, and I am very glad.  I really appreciate the help.

---

### Post by shortsellyhoonow on 2006-11-05
Boy is this distro terrible.

Where the **** is the C compiler in this damn distro???

---

### Post by taurus on 2006-11-05
> **shortsellyhoonow said:**
> Boy is this distro terrible.

Where the **** is the C compiler in this damn distro???
You need to calm down and relax a little...

```
sudo aptitude install build-essential
```

---

