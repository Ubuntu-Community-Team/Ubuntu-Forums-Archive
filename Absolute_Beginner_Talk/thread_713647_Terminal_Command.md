---
title: "Terminal Command"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Fying_Hgh on 2008-03-02
I downloaded ndiswrapper to my desktop. Does anyone know the command to install it from terminal?
I am not really sure of the path to type in and what the file name to tell it to install.

---

### Post by wednesday allfather on 2008-03-03
I'll save you some trouble.  Open Synaptic Package Manager.  System=>Administration=>Synaptic

Search for ndiswrapper and install the correct package.  If you aren't comfortable with command line, you may want to find the GUI for ndiswrapper.  

There are many tutorials on how to install programs in Ubuntu.  Starting out, i would play with Synaptic and if I was going to download something, it would be a .deb package.  They are basically the same deal.  Double-click and gdebi or whatever installs it for you.

---

### Post by amingv on 2008-03-03
Did you download the source file or a deb? Have you tried synaptic?

If you wish to install from source anyway extract the contents in a folder, cd to that folder; for example, if it's on your desktop, in a folder called ndiswrapper1.5, type in

```
cd ~/Desktop/ndiswrapper1.5
```
and type in these commands:

```
make
sudo make install
```

Of course, make sure you have build-essential first:

```
sudo apt-get install build-essential
```

---

### Post by Fying_Hgh on 2008-03-03
I have found both of those articles helpful! 2 very great lessons.
Thank You for helping me get to my goal.( Never going back to MS. )
I am learning more everyday in these forums. 
Hopefully one day I can help out here.

---

