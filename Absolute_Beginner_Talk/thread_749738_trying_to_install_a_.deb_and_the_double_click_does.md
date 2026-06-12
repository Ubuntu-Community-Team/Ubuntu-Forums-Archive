---
title: "trying to install a .deb and the double click doesn't work"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by rick3878894 on 2008-04-08
I am running Xfce (does that stand for some thing?) I don't have gnome because it is way to slow. I try to just open it and I get that select what program to open with. How do I install it? Is there a simple command that I use?

---

### Post by stchman on 2008-04-08
> **rick3878894 said:**
> I am running Xfce (does that stand for some thing?) I don't have gnome because it is way to slow. I try to just open it and I get that select what program to open with. How do I install it? Is there a simple command that I use?

Try to see if the gdebi package installer is installed.

---

### Post by click4851 on 2008-04-08
I've always wondered the same thing....Xfce....what does that stand for.and why not XFCE? Good question, .

So debs are usually loaded using apt, or aptitude, or synaptic, which are all software package management systems. In the very beginning, If its loaded for Xfce, Add/Remove software is probably a better choice for loading software. gdebi might work as well, or when you are comfortable, I highly recommend synaptic for managing your loaded deb software.

---

### Post by PeterJS on 2008-04-08
> **rick3878894 said:**
> I am running Xfce (does that stand for some thing?)
When XFCE was first written it stood for XForms Common Environment. But xfce hasn't used XForms for at least two major revisions, so these days xfce just stands for xfce.
>  I don't have gnome because it is way to slow. I try to just open it and I get that select what program to open with. How do I install it? Is there a simple command that I use?

To install a deb from the command line you can use:
```

sudo dpkg -i debfile.deb

```
The -i is for install.

If you want to set up the graphical installer for deb packages, it's named gdebi and can be installed with synaptic.

---

### Post by red_Marvin on 2008-04-08
You could always install it from the terminal (there should be an icon on your program menu, I'm no xfce user so I can't tell exactly where).

When the terminal starts, it will be looking at your home directory, if that's not where you have downloaded the file, you can go there with the *cd* (change directory) command:
Example: if you downloaded it into the folder "downloaded/stuff/programs/" simply type *cd downloaded/stuff/programs/* and press enter.

To check that the file is there type the command *ls* which should print a list of the files.
If you can't see your deb in the list check that you are in the right directory.

To install the deb use *sudo dpkg -i **filename***

D'oh, ninja'd

---

### Post by stchman on 2008-04-09
> **PeterJS said:**
> When XFCE was first written it stood for XForms Common Environment. But xfce hasn't used XForms for at least two major revisions, so these days xfce just stands for xfce.


To install a deb from the command line you can use:
```

sudo dpkg -i debfile.deb

```
The -i is for install.

If you want to set up the graphical installer for deb packages, it's named gdebi and can be installed with synaptic.

Only problem with dpkg command is that it does not install dependencies.  TO install a package that needs dependencies use the CLI version of gdebi.

```
gdebi <.deb package>
```

This will install the package and all needed dependencies.

---

### Post by PeterJS on 2008-04-09
> **stchman said:**
> Only problem with dpkg command is that it does not install dependencies.  TO install a package that needs dependencies use the CLI version of gdebi.

```
gdebi <.deb package>
```

This will install the package and all needed dependencies.
Didn't even know that existed, I'll file that under g for good to know.

---

### Post by stchman on 2008-04-09
> **PeterJS said:**
> Didn't even know that existed, I'll file that under g for good to know.

Neither did I until I needed to install a package from the command line that needed to have dependencies installed.  I lost X and therefore had no GUI to install packages.

dpkg crabbed about needing dependencies but did nothing about it.  I then did some poking around and turns out gdebi is the CLI version and gdebi-gtk is the GUI version.

---

### Post by SunnyRabbiera on 2008-04-09
well you can use synaptic to fetch gdebi as well.

---

### Post by bodhi.zazen on 2008-04-09
dkpg will not install dependencies, but apt-get will

SO ...

sudo dpkg -i foo.deb

will install foo without checking for dependencies, but the dependencies are tracked.

Resolve them with 

```
sudo apt-get -f install
```

apt-get will download and install dependencies.

If you do not have an internet connection you will have to find the packages manually.

---

