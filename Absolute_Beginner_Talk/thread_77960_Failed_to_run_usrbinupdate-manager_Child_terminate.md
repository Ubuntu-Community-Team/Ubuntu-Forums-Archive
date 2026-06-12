---
title: "Failed to run /usr/bin/update-manager: Child terminated with 1 status"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by CaptainMorgan on 2005-10-17
I have no idea what this is... 

Im trying to install updates and when I do so I immediately get this error message prohibiting me from going any further. 

Any suggestions? 


Thank you

---

### Post by eivind on 2005-10-17
It's much simpler to see what's happening if you open a terminal and type in the following:

sudo apt-get dist-upgrade
(insert root password when asked for it)

because the update manager does the same thing as the command above, but it doesn't give the output that the apt-get line will give you. Post the error message here, and we will probably be able to help you!

Cheers,

Eivind

---

### Post by Redindian on 2005-10-17
I think i had the same problem......I'm not sure whether the following steps are going to work or not but give it a shot.

sudo apt-get -f install

sudo apt-get update

sudo apt-get install ubuntu-desktop


If the above still doesn't do it for you,

sudo apt-get install synaptic.

---

### Post by red_Marvin on 2005-10-18
EDIT: --- <.< oops, wrong thread...

---

