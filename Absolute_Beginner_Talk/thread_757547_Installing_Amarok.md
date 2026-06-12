---
title: "Installing Amarok"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by SigmaHog on 2008-04-17
I'm trying to download Amarok but it keeps giving me an .iso for Kubuntu? Do I have to download Kubuntu to use it?

---

### Post by kbless7 on 2008-04-17
Just install it through synaptic

applications>>Add/Remove

then search for amarok. put a check next to it and install. real easy

---

### Post by sharks on 2008-04-17
Or type in terminal:

sudo apt-get install amarok

---

### Post by SigmaHog on 2008-04-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok

this is what i get when i type in sudo apt-get install amarok

---

### Post by northern lights on 2008-04-18
You have to enable the respective repositories -

open Synaptic and navigate to "Settings > Repositories". Mark universe/multiverse also.

---

### Post by misfitpierce on 2008-04-18
[quote=TERMINAL]sudo apt-get install amarok[/quote]

That should do it.

---

### Post by SigmaHog on 2008-04-18
new update....

 sudo apt-get install amarok
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


grrrr.... help me!!!!

---

### Post by enigmaniac23 on 2008-04-18
Do you still have synaptic open when trying to run the command to install?

You just need to make sure synaptic is closed when you run:

sudo apt-get install amarok

---

### Post by SigmaHog on 2008-04-19
grrr...

Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

did i get a back version of ubuntu? lol

---

