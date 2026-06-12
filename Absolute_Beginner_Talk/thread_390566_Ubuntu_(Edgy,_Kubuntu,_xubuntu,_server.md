---
title: "Ubuntu (Edgy, Kubuntu, xubuntu, server"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Mutahir on 2007-03-22
Hello All,

I am new to Ubuntu and confused in different names, though I understand what a desktop version is and what a server version is.

I downloaded the Server Version and when I installed it, there was no GUI installed, it was all command prompt ? Did i missed on the option or does it just gives one the command line options to configure Ubuntu server?.

Also, On different forums and websites I have seen and read people writing 'Ubuntu Edy' and another name which I have forgotten.


I would be greatful if someone could clear these for me as I am keen to use Ubuntu as my main OS. I have two machines (Intel X86) one I would use as a Ubuntu Server and the other as desktop.

Kind Regards

Mutahir

---

### Post by Nythain on 2007-03-22
Ubuntu - Default Gnome Desktop installed
Kubuntu - Ubuntu with KDE Desktop instead of Gnome
 etc.

Dapper Drake 6.01 Long Term Support - older but reliable
Edgy Eft 6.10 - The Most Current non Testing Release
Fiesty Fawn - The Next Release

Server - No GUI because servers shouldnt have them, base distro with server specific software setup if chose LAMP install

hope that helps... you are probably looking for either ubuntu or kubuntu desktop if you are looking for a GUI... of course once you have any flavor installed you can install anythign else from there... its completely possible to install gnome and or kde onto the server install and its completely possible to install KDE on a standard Ubuntu install same as throwing Gnome on a Kubuntu install...

---

### Post by justleen on 2007-03-22
There are different version of Ubuntu, which have names like this:
Dapper Drake, Edgy Eft, and Feisty Fawn (and Hoary, which a bit older).

these names refer to different  version of ubuntu, for example, Edgy Eft is version 6.xx

The other names, Xubuntu, Ebuntu, Kubuntu etc. refer to different desktop versions of ubuntu. For example, Kubuntu is exacty the same as Ubuntu, but instead of Gnome as a dekstop manager, it uses KDE as a dekstop manager. Ebuntu is Ubuntu specific for Educational purposes.

All these version are avaiable for download.

The make thins simply, most versions offer an Alternate Install cd, which allows you to install a command line only system. eg. it will install a minimum amount off packages, and no GUI.
For your server, you hafve installed a command line only system.

---

### Post by mahy on 2007-03-22
If you understand what a server version is, you should've known servers don't have any graphics. :) (windows 2003 server is an anomaly)

If you can connect to the Net, just run commands:

sudo apt-get update
sudo aptitude install ubuntu-desktop (that's for Gnome)
OR sudo aptitude install kubuntu-desktop (for KDE)
OR sudo aptitude xubuntu-desktop (Xfce environment. Lightweight, but not so beginner-friendly)

If you can't get connected, the easiest way would be to run a clean install of either Ubuntu, Kubuntu or Xubuntu, depending on which desktop environment you like. Is it clear now?

---

### Post by Mutahir on 2007-03-22
> **mahy said:**
> If you understand what a server version is, you should've known servers don't have any graphics. :) (windows 2003 server is an anomaly)

If you can connect to the Net, just run commands:


If you can't get connected, the easiest way would be to run a clean install of either Ubuntu, Kubuntu or Xubuntu, depending on which desktop environment you like. Is it clear now?

First of All, Thanks to Justleen, Mahy, Nathiyan for a very quick response.

Now I understand about the flavours of ubuntu, i use a dsl connection for the internet, with command line only installed how would I configure it, if something you can explain here or to a online reference would be really appreciable.

Once again, Thanks alot for the quick responses...

I will be asking more as I start to get used to ubuntu:)

Kind Regards
Mutahir

---

