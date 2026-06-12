---
title: "Ndiswrapper question."
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by m@dm@x on 2005-10-04
All,
     I know this has been discussed at great length but, I'm having a hard time getting my DWL-g122 to work.  I'm trying to use Ndiswrapper to get this to work.  I know there are several distos out there that have this app installed allready, and I did install it with Synaptic but, I'm having a hard time finding it after, "Applying" it.  My question is, where in the heck do I find Ndiswrapper after I've applied it?  Should I use Terminal to use this app or is ther a Gui that I can use to get this task started?

    On a side note.... I'm sure you can tell I'm pretty new to this and Ubuntu is the reason why I'm trying to utilize Linux (Wonderful user community to work with).  Thanks everyone for being so awesome.

---

### Post by loupy on 2005-10-04
There is a GUI for ndiswrapper.  In the synaptic package manager install ndisgtk.  This will install it to system -> administration -> Windows Wireless Drivers.

Make sure you have both ndiswrapper-source and ndiswrapper-utils installed.

From the command line you can configure it with the following commands:

sudo ndiswrapper -i xxxx.inf (windows inf file)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

if all went well you can go to system -> administration -> networking and see your wifi card in the list.

---

### Post by az on 2005-10-05
[QUOTE=loupy]
Make sure you have both ndiswrapper-source and ndiswrapper-utils installed.[/QUOTE]


You do not need to have the source.

If you can get on the internet and install the graphical interface to ndiswrapper, then you should use that.  If wireless is the only way to get on the net, you will need to set up ndiswrapper by hand.

Install ndiswrapper-utils (it is on the cd)
and follow this:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

### Post by m@dm@x on 2005-10-05
Thanks a ton for the help.  I'll try this tonight after work and let you know how it goes.

---

### Post by m@dm@x on 2005-10-21
Ok, I've at least got this to show up in the device manager but it still doesn't show under networking.  Is there something I'm missinger here?

---

