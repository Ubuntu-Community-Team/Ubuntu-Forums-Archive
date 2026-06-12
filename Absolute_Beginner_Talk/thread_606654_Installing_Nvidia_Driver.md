---
title: "Installing Nvidia Driver"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by MaDeX on 2007-11-08
Someone tell me the DECENT and working way to install driver - none of this envy rubbish....


nvdia 8800GTS card...

using feisty - can upgrade to gutsy if needed.

Restricted drivers causes a problem - cannot start X server.

Any takers?

---

### Post by AlexenderReez on 2007-11-08
search **nvidia-glx-new** in synaptic....install it with its** restricted modules** for your kernel....btwn...if you can't start xserver...run 

[PHP]sudo dpkg-reconfigure -phigh xserver-xorg[/PHP]

first.....

---

### Post by MaDeX on 2007-11-08
Thank you for the reply- could you now explain for someone who has no brain and is microsoft brainwashed.

Oh and stoooopid.

:)

---

### Post by alienexplorers on 2007-11-08
Run from terminal:
> sudo apt-get install nvidia-glx-new
Once loaded run in terminal:
> gksudo nvidia-settings
Use this program to setup your Nvidia Card.

---

### Post by AlexenderReez on 2007-11-08
relax..everybody start from noob....  :) 


system --> administration --> synaptic


 we need to have nvidia driver (ofcouse) ..and it is call nvidia-glx-new (in synaptic , search using = ctrl + f )......and to support that driver..we need to have its restricted modules..if you search linux restricted modules in synaptic...you will see a list of kernel restricted modules based on kernel...means you need check which kernel you are running....

i think this way is even better --> [PHP]http://www.psychocats.net/ubuntu/nvidia[/PHP]

---

### Post by MaDeX on 2007-11-08
I'm concerned theres not set way to install nvidia drivers?

i'm the only one?!

---

