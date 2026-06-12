---
title: "Can you load Ubuntu and Kubuntu on the same CPU?"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2005-10-16
new to ubuntu.....

---

### Post by ltmon on 2005-10-16
Hi,

Ubuntu and Kubuntu are exactly the same operating system, but just with some different programs being used by default.  Ubuntu uses the Gnome desktop and associated programs, Kubuntu uses the KDE desktop and associated programs.

You can switch between these two options without even shutting down the computer.

You can run KDE applications when using the Gnome desktop with no problem.

Hope this answers your question.

L.

---

### Post by ecobuntu on 2005-10-16
and you can run xubuntu, which is xfce4

---

### Post by poofyhairguy on 2005-10-16
Install Ubuntu. Then go put in this command:

sudo apt-get install kubuntu-desktop

To get KDE too.

---

### Post by qiezi! on 2005-10-17
If you have the Kubuntu install disc (same release as Ubuntu), is it possible to get KDE off that CD rather than downloading it from the repositories?

---

### Post by ltmon on 2005-10-17
[QUOTE=qiezi!]If you have the Kubuntu install disc (same release as Ubuntu), is it possible to get KDE off that CD rather than downloading it from the repositories?[/QUOTE]

Unfortunately no.

To keep the install disc to one cd only you get either Kubuntu or Ubuntu.  To get the other you either have to download the other install disc and get the needed pacakges off of it, or do the repository download thing.

To get Ubuntu available once Kubuntu is installed type:

sudo apt-get install ubuntu-desktop

at a command prompt.

L.

---

### Post by qiezi! on 2005-10-17
[quote=ltmon]Unfortunately no.

To keep the install disc to one cd only you get either Kubuntu or Ubuntu. To get the other you either have to download the other install disc and get the needed pacakges off of it, or do the repository download thing.

To get Ubuntu available once Kubuntu is installed type:

sudo apt-get install ubuntu-desktop

at a command prompt.

L.[/quote]

Yeah, oops, sorry that's what I meant, I have both CDs, and have installed Ubuntu, but would like to install KDE aswell.  How do I get desired packages off the Kubuntu CD?

---

### Post by funkydan2 on 2005-10-17
There's probably a GUI way to do this ...

Pop the Kubuntu CD into your CDROM drive.  Open a terminal and type
'sudo apt-cdrom add'

This will enable you to use the packages on the Kubuntu CD.

Now open Synaptic and install kubuntu-desktop (or run 'sudo apt-get install kubuntu-desktop' from the command line).  It'll ask for the appropriate disks.

---

### Post by qiezi! on 2005-10-17
Cheers funkydan2!  I also found in Synaptic you can add a CD to get packages from, so blind! ;)

---

### Post by dwessell on 2005-10-17
How do you set which one is your default?

Or even better, how do you have it boot to a command prompt?

I know startx from a command prompt starts Gnome, what would start KDE?

Thanks
David

---

