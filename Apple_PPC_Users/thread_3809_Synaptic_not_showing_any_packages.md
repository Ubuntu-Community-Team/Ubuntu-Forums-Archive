---
title: "Synaptic not showing any packages"
date: 2004-11-09
forum: Apple PPC Users
---

### Post by brainchill on 2004-11-09
I have Ubuntu installed on 3 or 4 machines right now and they are all working perfectly. I tried installing it on my Tibook last night and everything looked like it was working ok but when I try to use synaptic to search for a package it shows nothing.

I did a reload and made sure that it was getting a fresh list and it was. 
It appears to have the package list and be able to search it but on the right hand
pane where it would display the results you see nothing. If you look at the bottom it says x number of packages found but the list isn't displaying.

The number of packages found match up with another machine I have .. doing a search for "tux" it says that it's got 19 or 20 found but they are not displayed.

If I use apt-get at the command line it finds what I am looking for and installs it no problem.

---

### Post by guido on 2004-11-09
[QUOTE=brainchill]I have Ubuntu installed on 3 or 4 machines right now and they are all working perfectly. I tried installing it on my Tibook last night and everything looked like it was working ok but when I try to use synaptic to search for a package it shows nothing..[/QUOTE]

There's a bug in the PowerPC version of Synaptic (already solved in the new 0.55 version): after you have modified some preferences (i.e. "Show package properties in the main window") the right panel remains empty.

Just delete the configuration files with "sudo rm -r /root/.synaptic".

---

