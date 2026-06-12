---
title: "pc spec"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2007-02-11
Is there a command I can type to get a print out of my machine specs.

---

### Post by moshuptrail on 2007-02-11
I don't think so, but there are a number of specific commands that show parts of the system:

lspci
shows eveything on the pci bus for example
lsusb 
shows everything attached by USB

---

### Post by laidback on 2007-02-11
I installed a routine called lshw from synaptic. Search synaptic for lshw.

You can run it from a terminal to get the output or a Gui front end. The Gui doesn't appear to have a print facility.
# sudo lshw

or for the gui

# sudo lshw-gtk

---

### Post by AirAshby on 2007-02-12
Thank you the lshw command work just as I needed it to.

---

### Post by laidback on 2007-02-12
Glad to be of help.
How are things at the Uni?

As it happens you're not a million miles away.

laidback

---

