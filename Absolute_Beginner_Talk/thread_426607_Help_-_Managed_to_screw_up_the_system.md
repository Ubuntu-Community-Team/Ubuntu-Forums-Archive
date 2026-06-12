---
title: "Help - Managed to screw up the system"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-04-28
Well... it had to happen... I managed to screw up Xubuntu. Don't really know what I did wrong, but ir started like this:

Tried to Update the opera browser

Then downloaded a file called "opera_9.20-20070409.6-shared-qt_en_i386"

Double clicked on the file.

Gave an error message saying that opera couldn't install, to check the Synaptic manager.

The synaptic manager gives me the following message:

An Error ocurred  -    E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I opened the terminal, and typed "dpkg --configure -a

The terminal then tells me I need a superuser permission





Tried to log in as root....  It doesn't  allow me to log in as root on the graphic log-in display.




Ok.... what did I do wrong???

How do I correct it?

What on earth is a superuser?

How can I log-in as root?


Please help me because I'm about to re-install xubuntu. And is't a pity because I spent quite some time perfecting it for my taste. I still have Firefox, but opera doesn't work any more. It can't be installed because it's already installed, and it cannot be un-instaled, because something missing.

---

### Post by deadgobby on 2007-04-28
open up the terminal and before the command use 
sudu dpkg --configure -a
 it will ask for a password. It should be the one you use to log into.
Gobby

---

### Post by Sef on 2007-04-28
before the dpkg, you need to type sudo.

CODE]sudo dpkg -configure --a [/CODE]

---

### Post by kerry_s on 2007-04-28
```
# Canonical Commercial Repository (Opera,Real Player10.. etc)

deb http://archive.canonical.com/ubuntu edgy-commercial main
```

sudo mousepad /etc/apt/sources.list

---

### Post by Ganda_Melga on 2007-04-28
Sudo worked really fine.

Problem is it seems I have a broken package

Java 5.0

Tried to remove - negative, the package is in very bad shape

(My xubuntu is in Portuguese, I'm trying to translate, but the words may be slightly different )


No removal possible, so I tried to update.

It freezed! The Pc functions, but the installation freezes completly!

---

### Post by Ganda_Melga on 2007-04-28
I am going to try to stop the process of installation. I think there's a process manager somewhere, hope it's as easy as the one on windows.

---

### Post by Ganda_Melga on 2007-04-28
No such luck. I'm just too dumb to understand what should be stopped or not....

---

### Post by annda on 2007-04-28
if you are unsure of what processes you need to stop, you can always stop them all by bringing the system down. reboot.

and add the commercial repository to get opera the easiest and safest way, just like kerry_s suggested.

---

### Post by Ganda_Melga on 2007-04-28
> **annda said:**
> if you are unsure of what processes you need to stop, you can always stop them all by bringing the system down. reboot.

and add the commercial repository to get opera the easiest and safest way, just like kerry_s suggested.


Right. I'll try to reboot.

---

### Post by Ganda_Melga on 2007-04-28
Ok.... rebooted.

Managed to remove opera ( I think)


Tried to reinstall opera.


Message: Cannot install because it conflicts with other software.



Still working to figure it out....

---

### Post by Ganda_Melga on 2007-04-28
No way I can re-instal opera. It seems to be removed from the system, but whenever I try to isntall it I get a weird message from the synaptic manager:

opera:
  Depende: libc6 (>=2.5-0ubuntu1) mas 2.4-1ubuntu12.3 será instalado
  Depende: libgcc1 (>=1:4.1.2) mas 1:4.1.1-13ubuntu5 será instalado
  Depende: libqt3-mt (>=3:3.3.8really3.3.7) mas 3:3.3.6-3ubuntu3.1 será instalado
  Depende: libstdc++6 (>=4.1.2) mas 4.1.1-13ubuntu5 será instalado

It's in portuguese, but I hope someone will understand the meaning of this. I surely can't

Anyone can help? Or should I realy re-install xubuntu?

---

### Post by eternalsword on 2007-04-28
Which version of Xubuntu are you using?  It seems to me the version of opera you are trying to install has been compiled for a higher version of Xubuntu than you have.  libc6 >= 2.5 is for Feisty, so if you're still on Edgy, that's the problem.

---

### Post by Happy_Man on 2007-04-28
Ok, first go into Synaptic and enable EVERY SINGLE repo except source repos (you don't want those). Then search for Opera and install. If it still throws up an error, run:

```
sudo apt-get autoclean
```

and see if that helps.

---

### Post by Ganda_Melga on 2007-04-29
> **Happy_Man said:**
> Ok, first go into Synaptic and enable EVERY SINGLE repo except source repos (you don't want those). Then search for Opera and install. If it still throws up an error, run:

```
sudo apt-get autoclean
```

and see if that helps.


Well, late last night I managed to install Opera again. The system doesn't install it, no way. But by clicking on the file wich I downloaded before, this time it did install, although it gave several error messages. I'm using Opera right now.

Anyway, the system is not clean, because if a create a shortcut of opera, it tries to execute the old opera files, and doesn't load. So I will keep an eye on the system, and if needed, I will execute command you just gave me (sudo apt-get autoclean). I'm still learning to walk in Linux, I have to take one step at a time.


Many thanks to all of you how came foward and tried to help me with this issue! :) :)

---

