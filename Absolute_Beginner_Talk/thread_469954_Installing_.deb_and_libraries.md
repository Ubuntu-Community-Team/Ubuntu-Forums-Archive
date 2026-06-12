---
title: "Installing .deb and libraries?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by zwchten on 2007-06-10
Hello,

I am trying to clone a machine with no net connection. How do I install a .deb and its library without using Synaptic or apt-get install?

For example, I have file1.deb and the additional package libfile1. Do I do 

$sudo dpkg -i file1.deb libfile1

? Thanks for helping.

---

### Post by ajgreeny on 2007-06-10
What you suggest should work, if you navigate to the folder where the files are, but may have difficulties with dependencies, if I remember correctly.  It will  also depend on the libfile1 also being a .deb file as dpkg will not work with other file types, I think.

In gnome, also, I think you can just double click the deb file and it will be installed, or in kde you can right click the file and use the Kubuntu package menu in the context menu that appears.

Finally, if you copy the .deb files to your **/var/cache/apt/archives** folder (you'll have to do this as root so open up a root nautilus with **gksudo nautilus** or use the terminal) you can then use synaptic to install the files as usual.  If the libfile1.deb is a dependency of the file1.deb file, it will be installed as needed.  This method of working is useful if you have more than one machine and one or some are not internet enabled, as you can just update the one that is and then do all the rest by copying these files which apt downloads to that folder by default.

---

### Post by zwchten on 2007-06-10
I copied the .deb files into /var/cache/apt/archive then used Synaptic, and it seems to work correctly now. It's great that Synaptic took care of the configuration. Thanks a lot for the idea.

---

