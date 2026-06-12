---
title: "Help - lost Ubuntu !!"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-10
I am new to Ubuntu and Linux.
In order to install a system sound for the new mail notifier - I was directed to install Gnome-audio in Synaptic. When I did this it indicated it would remove Ubuntu-sound and another application I didn't write down - 3 letters beginning with 'G'
After this when I went back to my desktop the system crashed and when I re-boot I go into a balck login screen:

"Ubuntu 5.10 Breezy Badger" Ubuntu TTY"
and when I attempt to log in with my username and password nothing happens.
I tried the recovery mode - but don't know where to go from the prompt it leaves me at.
What to do ?!! Your help would be appreciated getting back the system I have spent the past 2 weeks configuring. Cliff

---

### Post by trent dillman on 2006-04-10
sudo apt-get -y install gdm

---

### Post by x5452 on 2006-04-10
mr dillman, where do you guys all learn this stuff!! lol where can I go, or a good book to get, ( a dummies book?) for linux learning?  I would like to learn the commands, what to type in the terminal, and when, and what it does...if you have suggestions please tell, you guys saved me yesterday from my blank screen when i accidentally uninstalled my desktop, id like to know how to fix stuff like that in future, so where do you learn it!!! :mrgreen:

---

### Post by cliff0108 on 2006-04-10
Thank you SO MUCH !!
I thought I'd have to spend the next few days re-installing re-configuring etc.

Instead I'll take a little time to try and figure out what the heck happened.
When I invoked the sudo apt-get -y install gdm command - it removed the Gnome sound and re-instated Ubuntu sound - and lo and behold when I rebooted I had my Desktop back.
But what the heck does a change in sound effects have to do with losing the desktop?

---

### Post by x5452 on 2006-04-10
probably everything...I uninstalled evolution MAIL client and it took my gnome desktop with it...apparently,  a lot of things are intertwined that we wouldnt think would be...ive learned now to be careful and double check

---

### Post by cliff0108 on 2006-04-10
I think uninstalling Evolution was my nest step ..
I think I'll wait a bit :o)

---

### Post by eriefisher on 2006-04-10
When ever installing or removeing packages in either synaptic or using apt, you should get a message if there are other dependencies to be installed or removed. If you are unsure what these are I would do a search before you commit. This is why you are asked (y/n) in the terminal or accept changes with Synaptic. A leap of faith could be [terminal].

eriefisher

---

