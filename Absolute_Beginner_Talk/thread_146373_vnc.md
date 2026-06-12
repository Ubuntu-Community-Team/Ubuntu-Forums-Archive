---
title: "vnc"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-03-18
i know vncserver is installed but i would like to know how to make it run, as i have tryed vncserver but nothing happens

---

### Post by kmi on 2006-03-18
Ubuntu is simple : "System" menu, then "Preferences" and choose "Remote desktop (or Remote access or... I have a French install running, so...), then you just have to choose to activate it or not by a simple click and configure options in the same window if necessary...
:)

---

### Post by ice.man on 2006-03-18
but will remote desktop work from linux to windows and windows to linux?

---

### Post by mlind on 2006-03-18
[QUOTE=ice.man]but will remote desktop work from linux to windows and windows to linux?[/QUOTE]

Yes :mrgreen: 

try TightVNC. it has client & server for both platforms, windows & linux.

---

### Post by garner_nc on 2006-03-18
mlind,

   Thanks for the TightVNC recommendation. This was just what I was looking for to connect to my Windows desktop machine from my laptop. Very easy set-up.

All the best,
Doug White
Garner,NC USA

---

### Post by ice.man on 2006-03-18
is there away to set up linux so i don't have to login on that side so i can access the desktop from my computer (becoz i'm sick of unpluging monitor and kb to setup stuff on my linux box from my windows box)

---

### Post by dermotti on 2006-03-18
you should look into FreeNX , much faster than VNC. At times forget i am connected remotely!

---

### Post by ice.man on 2006-03-18
see my linux boxs will be used at lan's so i i make this FreeNX a service or even TightVNC so all i have to do is boot up my linux box and just login from my pc

---

### Post by WoodyMahan on 2006-03-19
[QUOTE=dermotti]you should look into FreeNX , much faster than VNC. At times forget i am connected remotely![/QUOTE]


Is yhis available through the repositories?  I really don't know how to install without Synaptic or apt-get.

apt-get install freenx  ????

---

### Post by dermotti on 2006-03-19
add

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx 

to your sources.list, then refresh synaptic and you should see freenx in there, and you can install it.

You can get the windows/linux client from [http://www.nomachine.com](http://www.nomachine.com)

---

### Post by ice.man on 2006-03-19
could u give us the long way of how to do that as that just flew over my head

---

### Post by WoodyMahan on 2006-03-19
[QUOTE=ice.man]could u give us the long way of how to do that as that just flew over my head[/QUOTE]


OK Ice,  When dermotti says:
add

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

to your sources.list, then refresh synaptic and you should see freenx in there, and you can install it.

Here's how you do that:

Open the erminal by going Applications - Accessories - Terminal

type this line directly into the terminal:  sudo gedit /etc/apt/sources.list

This will open a text editor with a alot of stuff in it.   Scroll to the bottom and copy/paste:   deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

Click Save and close.

Then open synaptic and hit the reload button.  THen you can search for freenx and mark it for installation.  Hoe this helps.

---

### Post by ice.man on 2006-03-19
W: GPG error: [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466



Sorry all is good but now how do i set it up?

---

### Post by ice.man on 2006-03-19
all is good i have it working and thank guys and girls

---

