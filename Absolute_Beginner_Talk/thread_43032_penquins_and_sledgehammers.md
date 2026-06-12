---
title: "penquins and sledgehammers"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by matthewworsfold on 2005-06-20
so, i've had ubuntu/linux for approximatley a day and a half.  it's a nice feeling when i finally get something to work, but that is rare. so anyway. i can't really do anything without the internet.  and the only thing my parents have at their house is juno dial-up. 

so i found a juno installation for linux.  juno.deb is the name of the package and i used my usb drive to transfer it to the desktop of the computer with linux. so then i searched around and found a dpkg command. so i did that to the file and it seemed to depackage it. and i go into the synaptics manager and it says it's installed.  i cannot, however, find an executable file (sorry if that's windows talk, but i don't know what else to call it).   

it's frustrating not having internet, especially since any thing i look for tells me to just find the repository and download it from there.   it's like i can't get the internet until i get the internet.  so if anybody knows a) where to look to find the juno file or b) any other way i can connect to the internet that would be appreciated.  also, if anyone can explain .deb files alittle bit more. 

thanks.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=matthewworsfold]so, i've had ubuntu/linux for approximatley a day and a half.  it's a nice feeling when i finally get something to work, but that is rare. so anyway. i can't really do anything without the internet.  and the only thing my parents have at their house is juno dial-up. 

so i found a juno installation for linux.  juno.deb is the name of the package and i used my usb drive to transfer it to the desktop of the computer with linux. so then i searched around and found a dpkg command. so i did that to the file and it seemed to depackage it. and i go into the synaptics manager and it says it's installed.  i cannot, however, find an executable file (sorry if that's windows talk, but i don't know what else to call it).   [/QUOTE]

try running the command "juno" in the terminal

> it's frustrating not having internet, especially since any thing i look for tells me to just find the repository and download it from there.   it's like i can't get the internet until i get the internet.  so if anybody knows a) where to look to find the juno file or b) any other way i can connect to the internet that would be appreciated.  also, if anyone can explain .deb files alittle bit more. 

thanks. 

Deb files are software package files for Ubuntu and Debian. They aren't like exes (as you can tell), but they do allow you to install 3rd party software.

---

### Post by matthewworsfold on 2005-06-20
what?  just type juno by itself in the terminal?

should i be in a certain directory?

---

### Post by matthewworsfold on 2005-06-20
i found a file in /root/Desktop/ called, well, in the terminal when i type dir it says

Juno\ Internet

but, when i look at it in the gui it's called 'No name'

when i left click and go to properties itsays that it's a desktop configuration file. i tried double clicking it and it didn't work. 

i don't know what's going on.

---

### Post by spedsta on 2005-06-23
I'm no expert but this i know, 

once the package has been installed, by just typing it in the terminal will launch it without having to be in the folder like in DOS, 

try that and then it should run the app. 
Sometimes you need to be a superuser to launch a certain app, then you use "sudo" and your app name. you will then be prompted for a password, this is your own password , and the app willl run, 

stick in there and you will definitely start seeing the power of Linux!
good luck \\:D/

---

