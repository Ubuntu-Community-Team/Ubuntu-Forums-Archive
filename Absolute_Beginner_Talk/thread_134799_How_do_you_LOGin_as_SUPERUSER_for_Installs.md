---
title: "How do you LOGin as SUPERUSER for Installs?"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by LateNighter on 2006-02-22
I've been trying to "INSTALL" the Module pkg, that I downloaded from Ati Website,
For my Radeon 9600 Pro Graphics Card.

 I have their Auto Installer and the Module pkg "rpm form", But when I go into Kate and try to install it, the pkg will Start to instal, then STOP:mad:  In the middle and say I Must be Running in Super User mode in order to continue.

 I went into Konqueror/Applications/System/run as different User, BUT No Soap:confused:   I logged into ati-driver-install pkg as the root user, But all it comes up with is the process has been terminated.
 And will go no farther.

 Can anyone tell me How to get into Super User mode so that I can get this set of Drivers install, I need the 3D Modules that aren't provided in the Synaptic fglrx Modules. "TuxKart" stinks without the 3D Modules.
 As well as the other Tux Games.

 I paid almost $100 for this card and it's going to run in 3D mode wither it likes it or not....:p 

 Also is it Terminal that I run my sudo commands?
 Or is it another program specific to Ubuntu?

 I can just hear my 9600 Pro saying is this the Best you can do?
 
 Any and all HELP Welcome...\\:D/

---

### Post by carlosqueso on 2006-02-22
Yes, you run sudo in a terminal, and sudo -i will make you a superuser here in good old ubuntuland, but you'll have to do it in CLI.  If you don't want to do that, you can create the root user with ```
sudo passwd root
``` but this is not reccommended for reasons covered here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-02-22
I don't know how you were able to log in as root, unless you did an expert install or asked somehow how to create a root login.

You're supposed to use *sudo* to temporarily gain root privileges. If it really came in .rpm form (say, something like pkg.rpm), then you would just go to the directory (let's say it's your desktop) and type these commands: ```
cd Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i pkg*.rpm
```

There are some packages in the Universe repositories that have *pkg* in them:

pkg-config
pkgsync
pkglist

None of those is what you're looking for? If you don't know what repositories are, see the second link of my signature.

---

### Post by steve.horsley on 2006-02-22
[QUOTE=carlosqueso]Yes, you run sudo in a terminal, and sudo -i will make you a superuser here in good old ubuntuland, but you'll have to do it in CLI.  If you don't want to do that, you can create the root user with ```
sudo passwd root
``` but this is not reccommended for reasons covered here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

Yes, sudo stands for SuperUser DO, or Set User DO since you can use it ti cnange to any other user (root is the default if you don't name the user).

You don't **create** the root user with sudo passwd - you just unlock his password. And do **NOT** delete root later, this is slightly disastrous. To re-lock the root password, use **sudo passwd -l**.

---

