---
title: "trouble un-installing"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Redeyes_Gambit on 2005-12-13
}{i-o

I am trying to get a .deb package (originally a .rpm package but the alien-ed to a .deb) un-installed, and have encountered a little problem. I go to the terminal, change directories to the Desktop and type "sudo dpkg -r openmotif_2.1.30-1_i386.deb" then it gives me this:

"you must specify packages by their own names, not by quoting the names of the files they come in"

I also tried the "purge" option and get this:

"Package `openmotif_2.1.30-1_i386.deb' is not available."


I did at one point move this file, but then moved it back to the desktop to un-install. Was this a stupid move? It also has a red padlock on the icon on the desktop, what does this mean?

---

### Post by amohanty on 2005-12-13
How about:

> sudo dpkg -r openmotif

---

### Post by Mustard on 2005-12-13
Have you tried uninstalling via synaptic?

It should be listed in the local and obsolete section.

The red padlock would be indicating that it is not accessible by a normal user.  You are the superuser though, so using sudo, you shouldnt have any issues with manipulating the file.  I did read something yesterday in the forum somewhere about someone having an issue with uninstalling a .deb created from an rpm using alien.  I have no idea whether this is a common problem.  I suspect using synaptic to uninstall should work without any problems.

---

### Post by Redeyes_Gambit on 2005-12-13
Ah, thanks amohanty, that did it. And thanks Mustard too for the synaptic tric. took me a second to find the local thing but now I know two ways :D

---

### Post by amohanty on 2005-12-13
I think if you click on the status button at the bottom of the left pane, local and obsolete is one of the sections that comes up in the left pane.

HTH

---

