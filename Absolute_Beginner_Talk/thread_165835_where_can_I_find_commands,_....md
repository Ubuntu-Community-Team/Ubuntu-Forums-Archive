---
title: "where can I find commands, ..."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-04-25
... for example - what command to use in order to install an sh file or a bin file?

---

### Post by jazzmuzik on 2006-04-25
It's best to install binary files that end in .deb made specifically for Ubuntu. Use the Synaptic program or the debian package manager for that: dpkg

In a terminal type:

man dpg 

to get a list of options.

Or try this:

dpkg<tab><tab>

That will show all the other dpkg programs.

You can install things from online repositories with apt-get


To install an sh file, try:

./programname.sh

or 

sudo ./programname.sh  


But always try and utilize deb files first. A program installed via sh should be the last option. Use Synaptic (System, Administration, Synaptic Package Manager) to see what packages (programs) are available.

---

### Post by oakz on 2006-04-25
If you have downloaded an sh file, you can usually run it using the following command:

$ sh thescript.sh

If you downloaded a bin file, it is often meant to be executed directly (the java package from Sun is an example).

First make sure you have the file marked as executable
$ chmod u+x thefile.bin

Then execute it:
$ ./thefile.bin

Hope that helps

---

