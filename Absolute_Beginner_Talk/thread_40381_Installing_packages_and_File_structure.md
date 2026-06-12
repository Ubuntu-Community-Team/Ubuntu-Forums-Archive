---
title: "Installing packages and File structure"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by SpaceWolf on 2005-06-08
Greetings!

I've recently installed Ubuntu and am very impressed so far.  I'm new to Linux, but I've had plenty of experience in the Windows world.  I have two basic 'n00b' questions (I've run a few searches, but have not found anything that answered my questions).
 
The setup - I've installed Ubuntu on my laptop, it is not connected to the internet.  I've downloaded a number of packages and put them on a zipdisk to transfer to my laptop.

1.  I've opened up package manager and understand what it is for, but how do I get the packages from the zipdisk to show up in package manager? 

2.  When a package is installed, will it create an icon or icon group in the toolbars or does it need to be run from a command line?



Bonus question: Can anyone recommend a good book to read to get a basic understanding of the layout of the file system and operations of Linux?

---

### Post by Kyral on 2005-06-08
well, I'm gonna assume the packages are .deb

you don't need Synaptic. just open a terminal and cd to the zipdisk mount point (or whereever the packages are) and type "sudo dpkg -i <packagename>"

Most of them make icons, some dont and have to be run from commandline

---

### Post by keithpeter on 2005-06-10
[QUOTE=Kyral]well, I'm gonna assume the packages are .deb

you don't need Synaptic. just open a terminal and cd to the zipdisk mount point (or whereever the packages are) and type "sudo dpkg -i <packagename>"

Most of them make icons, some dont and have to be run from commandline[/QUOTE]
 Hello Kyral and all

Does this mean that I can download a package and any dependent libraries that I don't alread have using apt-get with the -d option, save all the .deb files somewhere, perhaps on a CD-ROM and then install them later, and keep a backup?

---

### Post by Kyral on 2005-06-10
I guess so, but I have no clue where apt downloads packages too

---

### Post by Keyser on 2005-06-10
[QUOTE=keithpeter]Hello Kyral and all

Does this mean that I can download a package and any dependent libraries that I don't alread have using apt-get with the -d option, save all the .deb files somewhere, perhaps on a CD-ROM and then install them later, and keep a backup?[/QUOTE]

yes you can. the .deb files are stored in /var/cache/apt/archives

like kyral said, most packages install an icon in the menu, but some dont. and just in case you cant find the proper command to start a program thats not in the menu (its usually the same as the name of the package, but sometimes not), you can look up the package in synaptic, click properties then 'installed files' to see what exactly it installed.

---

### Post by xmastree on 2005-06-11
[QUOTE=Keyser]yes you can. the .deb files are stored in /var/cache/apt/archives

like kyral said, most packages install an icon in the menu, but some dont. and just in case you cant find the proper command to start a program thats not in the menu (its usually the same as the name of the package, but sometimes not), you can look up the package in synaptic, click properties then 'installed files' to see what exactly it installed.[/QUOTE]
 One major difference between the way Windows installs applications, and the linux way is that in Windows, the app tends to get its own directory. The executable, ini files, documentation etc. all go there.
With linux it gets split up. The executable usually goes in /usr/bin whereas the documentation will go in /usr/share/docs/<app_name> or wherever the program maker wants it to be. Ini files will end up in a hidden directory in your home directory, so that each user can have their own settings.

---

### Post by keithpeter on 2005-06-11
Hello

Yup - this works, only one 'gotcha', and could be very useful for those of use on a dial-up connection.

I installed Scribus the dtp package. First I used

sudo apt-get -d install scribus

to download the packages (only one required library)

Then, to test out the idea of saving packages as a backup, I copied the packages from /var/cache/apt/archives to a folder under my home directory.

I cd'd into that folder and ran

sudo dpkg -i <library name>.deb

and then

sudo dpkg -i <scribus package name>.deb

and it worked. I'm using XFCE window manager but with gdm running, and Scribus landed in the 'office' menu.

The 'gotcha' is that if there were a lot of dependencies with sub-dependencies, I'd have to sort out the right order to run the dpkg commands in,

Thanks

---

