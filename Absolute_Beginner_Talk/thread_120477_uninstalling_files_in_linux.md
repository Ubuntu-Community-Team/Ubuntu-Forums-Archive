---
title: "uninstalling files in linux"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by alek on 2006-01-21
Hello,

As a windows user all my life (and linux user for the past two weeks) I am getting into a (perhaps bad) habit of making some comparisons between the two.

I have not noticed a linux equivalent of the action "Add/Remove programs" in windows...
My question is basically this: how do I uninstall programs in linux? For instance, in windows, if I manually delete the program files, without removing them the "right way" (by actually uninstalling them) bits and pieces of the program are still left in windows, as it has not undergone a complete uninstallation procedure.

In Linux, I have not seen any way to uninstall... other than simply deleting the files, but I am affraid of doing that...

Perhaps I am just confused... any help would be greatly appreciated,

Thank you,
Alek

---

### Post by s6dalane on 2006-01-21
You can uninstall programs via synaptic.
Or if you want to use the terminal:
For example
> sudo apt-get remove xmms

And if you compiled from the source, simply type in the main tree:
> sudo make uninstall

I am not an expert myself, but hopefully this helps. :)

---

### Post by wolfmaniac on 2006-01-23
in terminal tye

sudo dpkg -r <package name.deb>

---

### Post by mwanafunzi on 2006-01-23
If you don't want to go through the terminal, you could always use the package managers found under menu>system..
There are a number of them that come with ubuntu (they may differ depending on whether you use gnome or kde).
Here are the names of the package manager I have on my system
menu > system > package manager(add application)
menu > system > package manager(kpackage)
menu > system > package manager(synaptic package manager)
menu > system > update manager

They more or less have the same functionality of adding and removing programs.

---

### Post by juantxorena on 2006-01-23
There are many ways for installing a program in linux, therefore there are many ways for uninstalling it:

1.- If you installed a program via repositories (syntapic, apt-get, aptitude...) you can uninstall it by typing sudo apt-get remove name_of_program or by selecting it in synpatic.

2.- In you installed it by downloading the deb package and tyiping dpkg -i name_of_package, you can uninstall it the same way as above.

3.- If you installed it compiling from the sources (./configure && make && sudo make install) it's harder. In some cases, you can uninstall it by typing sudo make uninstall in the source directory.
The best way is to install a program called checkinstall (it is on the repos). Then, you can do sudo checkinstall instead of sudo make install. Then the program will create a deb package and install it. Then you can uninstall it via apt-get, dpkg, synpatic, or whatever.

4.- If the program has a special way of installing it (games like quake, doom, neverwinter nights, non open-source programs, graphic drivers), they have a special way of uninstall it. You should read the manuals, readmes and documentation of the program.

---

