---
title: "E: Couldn't find package"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by OceanSized on 2006-05-08
I'm having difficulty wrapping my head around installing some things on Ubuntu. I go to the terminal and type 'sudo apt-get install sos_4.1.deb' figuring that it'll work fine, but then after that line I get:

     Reading package lists... Done
     Building dependency tree... Done
     E: Couldn't find package

Do I need to indicate the link location of the .deb file? Or download the package first and then use my root address? I've been following various directions and I don't get what is wrong. The package exists so I'm not sure why it isn't being found.

Thanks for any help and understanding.

---

### Post by dave9191 on 2006-05-08
Well I just searched the repoistories for a package named "sos" (apt-cache search package_name) and it didn't find anything. The repositories are online servers from which apt-get can download the file and install it for you. You don't spesify a version number or extention. 

Since you are typing a full name for a deb package, Im guessing that you have already downloaded the package file yourself and are trying to install it. In which case you want to use Debain PacKGe to install the file. 

sudo dpkg -i filename.deb

Hope that helps, 

--
Dave

---

### Post by Al3xanR0 on 2006-05-08
[QUOTE=OceanSized]I'm having difficulty wrapping my head around installing some things on Ubuntu. I go to the terminal and type 'sudo apt-get install sos_4.1.deb' figuring that it'll work fine, but then after that line I get:

     Reading package lists... Done
     Building dependency tree... Done
     E: Couldn't find package

Do I need to indicate the link location of the .deb file? Or download the package first and then use my root address? I've been following various directions and I don't get what is wrong. The package exists so I'm not sure why it isn't being found.

Thanks for any help and understanding.[/QUOTE]

It is not necessary to include the .deb extension when using apt-get, just ```
apt-get install sos
``` that should suffice. To make things easier yet search for sos in Synaptic (the graphical representation of apt-get).

---

### Post by Rinzwind on 2006-05-08
Are you sure it's the correct package?

sos_4.1.deb  doesn't even show up in google!?!?

---

