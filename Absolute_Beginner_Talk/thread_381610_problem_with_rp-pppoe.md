---
title: "problem with rp-pppoe"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by dineshs on 2007-03-11
I am new to linux/ubuntu.i tried to install rp-pppoe as per the instructions in ubuntu guide.i see rp-pppoe under the heading internet , it asks for PW when clicked but nothing happens.(I installed this believing that this would work as a pppoe dialler for my ADSL connection.Am I right) >kindly help

---

### Post by Draku on 2007-03-11
I don't know exactly but i think pppoe it's installed by default in Edgy. Just type sudo pppoeconf in terminal and configure your connection.

---

### Post by dineshs on 2007-03-11
At present i am using this method but i want to get a gui based icon with which i can connect/disconnect

---

### Post by kvonb on 2007-03-11
Use synaptic and search for "gpppon", it is a simple GUI connection tool.

You really should run pppoeconf first though I believe, as that sets up the backend config files.

In the configuration window, don't select autoconnect or it will conflict with gpppon.

Also make sure you ask your ISP what MTU they use, you will need to know that other wise you will find that secure web-pages and some things won't work properly.

---

### Post by Irid on 2007-03-11
A bit off-topic, but how can I remove RP-PPPoE? It didn't work for me, I simply use pon dsl-provider and poff -a in the terminal to control my DSL connection. I have also Network Manager and it does some kind of work, I suppose. You can disable/enable Internet within a click with it, for example.

---

### Post by dineshs on 2007-03-12
I tried to install gpppon using synaptic.It says installed but i dont find any icon anywhere .pl help

---

### Post by kvonb on 2007-03-12
Yes, sorry, it's not an "Ubuntu-ised" app :)

Right click on one of your  panels, select "Add to panel", click on "Custom application launcher", in "Name" put whatever you want to call it, in "Command", put gpppon, click on the little box "No icon" and select any icin you like, then click on "OK".

The process is virtually the same for a shortcut on your desktop, just right click and select "Create Launcher".

---

### Post by dineshs on 2007-03-12
Thank you very much.This works perfectly.Thank you very much

---

### Post by kvonb on 2007-03-12
No worries :)

---

