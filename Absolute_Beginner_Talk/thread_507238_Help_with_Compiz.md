---
title: "Help with Compiz"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-22
Im following this guide> [http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)

to install compiz-fusion, but Im stuck on step 2

I typed and got this:

ryan@Ted:~$ sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

The next two commands after that give me similair results. Whats causing this?

---

### Post by AlexenderReez on 2007-07-22
have you reload your sour source list or update it?if you have already update then it should be in the repo?

> sudo apt-get update -->did you miss this?

---

### Post by ukulele_ninja on 2007-07-22
How do i check?

---

### Post by AlexenderReez on 2007-07-22
open synaptic , search for compizconfig-settings-manager or compiz fusion ...you should found it if you have already update your source lists :)

---

### Post by ukulele_ninja on 2007-07-22
yes i did do the update

i just re-ran it so ill se if that works

---

### Post by ukulele_ninja on 2007-07-22
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages


Thats what I get after the second command in step 2.

---

### Post by AlexenderReez on 2007-07-22
you should see like this -->

---

### Post by AlexenderReez on 2007-07-22
add this repository -->

in terminal 
>  gksudo gedit /etc/apt/sources.list


add this in that text editor!!
> deb [http://debs.vorian.org](http://debs.vorian.org) feisty extras

in terminal

> gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

make sure you enable all line in ubuntu software column....then reload...

install compiz fusion again:)

---

### Post by ukulele_ninja on 2007-07-22
[QUOTE=AlexenderReez;3063826]add this repository -->

in terminal 


add this in that text editor!!


in terminal



make sure you enable all line in ubuntu software column....then reload...

install compiz fusion 

ryan@Ted:~$ gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device









I tried it from the link provided in that guide and got it all installed but when I tried to run it it says:


ryan@Ted:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
ryan@Ted:~$

---

### Post by AlexenderReez on 2007-07-22
make sure you have enable your graphic card support...which card are you using?nvidia or ati?or else?

:)

---

### Post by ukulele_ninja on 2007-07-22
Its an ATI and it is enabled...ugh....so discouraged...

---

