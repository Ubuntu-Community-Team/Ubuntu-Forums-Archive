---
title: "newbie question..."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by jardeeser on 2006-09-09
I just installed a copy of ubuntu 6.06 LTS and I can't figure out why I can't use "make", I'm trying to install ndiswrapper and in the install file it says to run "make uninstall"...

when I try to do this is says that the command isn't found
"sudo: make: command not found"

I also tried running:
sudo make uninstall
I gave it my password, still the command wasn't found.

I've been using ubuntu for only a few hours... I love it but I can't get Internet...

HELP?? Thanks
Joe

---

### Post by jordanmthomas on 2006-09-09
Insert your installation CD and use it to install the package "*build-essential*"
You should be able to make after that.  (I'm not sure what else you may need though as I don't need ndiswrapper)

---

### Post by bernied on 2006-09-09
You don't need to compile your own ndiswrapper. There is a package in the repositories. See next post (from me)...

---

### Post by Floren on 2006-09-09
Hi,

You probably haven't installed the 'make' utility.

Go System/Administration/Synaptic PM and search for 'make' Look for it in the list and install it.

That should solve your problem.

    Floren

---

### Post by bernied on 2006-09-09
I was wrong - the package is actually on the installation cd. Start by reading this:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jardeeser on 2006-09-09
thanks guys! you've helped a lot... let me see if I can figure it out from here...

---

