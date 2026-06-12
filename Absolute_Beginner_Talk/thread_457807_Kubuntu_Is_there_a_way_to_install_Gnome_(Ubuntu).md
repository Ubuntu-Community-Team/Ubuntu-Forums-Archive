---
title: "Kubuntu: Is there a way to install Gnome (Ubuntu)"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-05-29
Hi,

I have installed Kubuntu but would like to go to Ubuntu (Gnome) to try out the Beryl Manager and other eye-candy there.

Is there an easy way to install Ubuntu (Gnome) on top of my KDE (Kubuntu)?

---

### Post by Martin on 2007-05-29
Yes, use your favourite package manager or command line to install ubuntu-desktop

---

### Post by mikewhatever on 2007-05-29
check this page for Ubuntu installation [http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome)
To summarize, the following command installs Ubuntu desktop
> sudo aptitude install ubuntu-desktop
and the following removes Kubuntu desktop
> sudo aptitude remove kubuntu-desktop

---

### Post by eentonig on 2007-05-29
Open a terminal and type

> sudo apt-get ubuntu-desktop

Or GUI
System\Administration\Synaptic ...
hit 'Search'
Enter ubuntu-desktop
click on the little white box in front of the package you desire.
Select install
hit the "Apply" button.

Either way, reboot after install.(Although, <ctr>+<alt>+<backspace> might do the trick as well.

---

