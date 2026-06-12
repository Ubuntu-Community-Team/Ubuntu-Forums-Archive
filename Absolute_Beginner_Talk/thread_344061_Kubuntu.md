---
title: "Kubuntu"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by ces1939 on 2007-01-22
I am a very unlearned newbie. I chose Kubuntu because it works flawlessly with my HP Photosmart printer, and made it very easy to setup. I have tried Ubuntu-CE because I want a linux distro with BibleTime and/or Sword. Dan's Guardian service blocked Adobe download for Flashplayer, and blocked my address book in Yahoo. I tried to configure Dan's but found myself buried in a sea of commands I know nothing about. I don't understand linux commands at all, so I need help to get BibleTime and/or Sword downloaded and installed on Kubuntu with Adept. If that is not possible, I need to know how to download Synaptic Package Manager, and get those with it. I need the instructions in language I can understand, step by step. If someone has the time, or is interested in helping a 67 year old man learn something new, please respond.

---

### Post by arochester on 2007-01-22
Open Konsole. Put in it: sudo apt-get install synaptic

---

### Post by petersjm on 2007-01-22
Ces, you should already have synaptic installed. I can't remember the KDE (Kubuntu) menu structure, but check under "Administration" if you have that menu option. I'm not sure if Synaptic is Gnome-only thing? Alternatively, if you can open a terminal window (in KDE/Kubuntu it's "Konsole"). Anyway, open Konsole and type "sudo aptitude install bibletime" (without the quote marks), then enter your password and it should automatically find and install it for you. It might ask you to confirm [Y/n] - just type Y and press enter. Hope that helps

---

### Post by CroEragon on 2007-01-22
I think that having GNOME can't hurt....
Either way, instaling gnome will install Synaptic. To install gnome just copy/paste each line separatly in Konsole:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
It will not overwrite your current setup or change any of your settings. It will just install GNOME and with it bunch other GNOME programs; one of them is Synaptic.
After installing it hit Ctrl + Alt + Backspace and in login choose GNOME if you want it. Even without opening GNOME at all you should be able to use Synaptic, Gaim and many other GNOME programs in KDE.

Just im not sure that Kubuntu have apt-get (should have). If you do not have apt-get you can change apt-get to aptitude in all commands.

---

### Post by youthforlinux on 2007-01-22
kubuntu should have apt-get:D :D

---

### Post by ces1939 on 2007-01-22
This is what I get from Konsole. I am going to try the Ubuntu Desktop sugestion, and will post a reply after that is done.
ces1939@ces1939-desktop:~$ sudo aptitude install bibletime
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "bibletime"
The following packages have been kept back:
  locales
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
ces1939@ces1939-desktop:~$

---

### Post by konst88 on 2007-01-22
You must have the universe enebled in the software sources.

---

### Post by ces1939 on 2007-01-22
I got this and do not know what to do now. Iclicked OK and nothing happened
Ubuntu Configuration


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring gdm &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; A display manager is a program that provides graphical login              &#9474;
 &#9474; capabilities for the X Window System.                                     &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Only one display manager can manage a given X server, but multiple        &#9474;
 &#9474; display manager packages are installed.  Please select which display      &#9474;
 &#9474; manager should run by default.                                            &#9474;
 &#9474;                                                                           &#9474;
 &#9474; (Multiple display managers can run simultaneously if they are configured  &#9474;
 &#9474; to manage different servers; to achieve this, configure the display       &#9474;
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,     &#9474;
 &#9474; and disable the check for a default display manager.)                     &#9474;
 &#9474;                                                                           &#9474;
 &#9474;                                  <Ok>                                     &#9474;
 &#9474;                                                                           &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Arisna on 2007-01-22
That's a text interface, so you hit enter to make the selection, tab/arrows to navigate.  You'll probably want to use KDM, which you'll be able to choose at the next screen.  It's KDE's login manager.

Also, the graphical package manager in Kubuntu is Adept.  You can use it to do nearly anything you could do in Synaptic.

---

### Post by ces1939 on 2007-01-22
OK I followed instructions and tried to go the Ubuntu Desktop route. Don't know where, but something did not work. I tried to use Adept to get BibleTime and it says no package available. Used Adept to get Synaptic and tried it. Same response, no package available. Went to BibleTime web site, and found I first need CLucene> 0.1.19 or something like that, plus need Sword. Went the SourceForge route and got lost in the command lines. Went to the binary download sites offered, did not know which I need so tried Alpha. Saved that to my home/desktop, or thought I did.
Now I can't find it. Please consider possibly looking at the BibleTime and give me a step by step download and install procedure. I am learning, and if I can get better at this, I could possibly help others get out from under the grip of Microsoft, too.
Thank you so very much.

---

