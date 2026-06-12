---
title: "Add/Remove question"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-04-06
Hi guys,

I have a quick, potentially silly question:

How does Add/Remove... in the Applications menu link up with Synaptic? 
For example, will all applications in Synaptic show up in there when I add new repositories etc?

G

---

### Post by mac.ryan on 2007-04-06
AFAIK, not. There are 20.000+ packages in my Synaptics present configuration (ok, not all of them are programs, yet...), while I can just handle a few dozens from add/remove.

Anyhow I am unable to say if the one showing up in add/remove is a "selection" done by Canonical or if any packages that also has a defined location for its launcher in the menu will show automatically up in add/remove.

Applications installed by add/remove will be however "seen" from synaptics.

---

### Post by gh0st on 2007-04-06
I thought they were both just graphical front ends for Apt-Get but I might be wrong. It certainly seems that Synaptic has a lot more packages in it than "Add/Remove". I think "Add/Remove" is supposed to be a bit more friendly for new users and doesn't show everything in the repositories, maybe Canonical think that it would be a bit overwhelming but I'm only guessing there. 

I'm pretty sure they both work off the same sources list on your system though. Synaptic just seems to dig a bit deeper. I could be wrong about that but thats just what I thought. Others may disagree :)

---

### Post by zorkerz on 2007-11-05
Add/Remove uses the same repositories and all changes should be reflected in synaptic, apt-get, even aptitude I believe.

Im trying to figure out when I add something from add/remove what actual packages does it install. 

For instance when I installed the "gstreamer extra plugins" from add/remove what new packages will show up as installed in synaptic package manager?

Is there a way in general to find out what packages are being installed with the add/remove app?

---

