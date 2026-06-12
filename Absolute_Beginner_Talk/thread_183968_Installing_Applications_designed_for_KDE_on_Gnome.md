---
title: "Installing Applications designed for KDE on Gnome"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Souljah on 2006-05-29
I would like to know, if it is possible to install an application which was designed for the KDE environment for GNOME. Is that possible? Will it work or give me any problems? Basically, I'm looking for a download manager and there are so many, I don't know what to choose from. Can you guys give me some suggestions. I believe mine is the GNOME environment.

---

### Post by jimrz on 2006-05-29
[QUOTE=Souljah]I would like to know, if it is possible to install an application which was designed for the KDE environment for GNOME. Is that possible? Will it work or give me any problems? Basically, I'm looking for a download manager and there are so many, I don't know what to choose from. Can you guys give me some suggestions. I believe mine is the GNOME environment.[/QUOTE]

sure can...use synaptic, will get all the dependencies needed. You can also do ```
sudo apt-get update
``````
sudo apt-get install kubuntu-desktop
``` from the terminal. This will give you the choice of using either gnome or kde when you login.

---

### Post by Souljah on 2006-05-29
[QUOTE=jimrz]sure can...use synaptic, will get all the dependencies needed. You can also do ```
sudo apt-get update
``````
sudo apt-get install kubuntu-desktop
``` from the terminal. This will give you the choice of using either gnome or kde when you login.[/QUOTE]

Oh ok. Well I believe DAPPER is coming out next month so would you suggest I wait before I upgrade. I'm actually on hoary, 5.04.

---

### Post by akudewan on 2006-05-29
You can simply install apps from synaptic (or apt-get). Dependencies will be taken care of. I have used k3b, which is a CD burning app for KDE, in XFCE and Gnome with no problems at all :)

As far as download managers go, I like d4x. You can install it by using the command *sudo apt-get install d4x*

---

### Post by carverj on 2006-05-29
There are lots of download managers?
I didn't know that!! 
:D 

Can you name a few?
I have just been using apt get install
synaptic... thats about all i've used I think!!

---

### Post by jimrz on 2006-05-29
[QUOTE=Souljah]Oh ok. Well I believe DAPPER is coming out next month so would you suggest I wait before I upgrade. I'm actually on hoary, 5.04.[/QUOTE]

I would definitely go with dapper over breezy. Saturday I did a clean install of dapper rc on my laptop and, thus far, it really does seem to be a big step up. Dapper final is scheduled for release on Tuesday, so not too long a wait.

---

### Post by akudewan on 2006-05-29
[QUOTE=carverj]There are lots of download managers?
I didn't know that!! 
:D 

Can you name a few?
I have just been using apt get install
synaptic... thats about all i've used I think!![/QUOTE]

Synaptic and apt-get are not download managers, they are *package managers*

Download manager means programs like wget, d4x, etc, which will simply help you download any files from the internet, and help you pause/resume the download.

Package managers, on the other hand will help you download and install files from the Ubuntu repository. As far as package managers go, there are a few other options such as "aptitude".

---

### Post by carverj on 2006-05-29
What do you like about it?
sounds promising as I thought it would be much the same as breezy!!

---

### Post by Sef on 2006-05-29
> As far as download managers go, I like d4x. You can install it by using the command sudo apt-get install d4x


Use aptitude instead of apt-get.  It makes uninstalling easier if you decide to do that.

sudo apt-get update

sudo aptitude install d4x.

---

