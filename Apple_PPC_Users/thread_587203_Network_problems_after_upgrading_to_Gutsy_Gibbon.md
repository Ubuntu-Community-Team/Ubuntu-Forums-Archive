---
title: "Network problems after upgrading to Gutsy Gibbon"
date: 2007-10-22
forum: Apple PPC Users
---

### Post by delucious on 2007-10-22
I was using my iBook G4 with Feisty Fawn with a wired connection, but no being able to connct wireless. I upgrade to Gusty Gibbon hoping to solve my wireless problems, but now I don't have any kind of connection!!:confused:
I can't find any network device when I go to Network Tools, just a Loopback interface (lo) 
Any help will be appreciated.

---

### Post by ego1 on 2007-10-23
begining, I uninstalled network manager. it the cause for all our problem.
I am trying to find a substitute.
with the gnome network connection along, you can work, but it is no easy.
if somebody know a substitute for network manager, I will appreciate that opinion.

---

### Post by aantn on 2007-10-24
I've heard that wicd works, but I've had some trouble with it personally.

---

### Post by dynamicv on 2007-10-24
You're definitely on the right track by uninstalling Network Manager when it comes to getting the Airport interface up and running.  When your ethernet interface is running again look into getting the Wi-fi side of things working.  First things first though:-

When you open the terminal and type "ifconfig eth0" what does it come back with?  Is an interface recognised?

---

### Post by Mattyb_uk on 2007-10-24
Hey Guys

I had the same problem, so I went and got the latest version of Network-Manager and Network-Manager-Gnome from Debian.

Do this at your own risk. There is a bug ticket on launchpad for this with a quick fix,
but they've only offered the fix in i386 and x64 packages :-(

Install Network Manager first from Debian Testing (lenny)
[http://packages.debian.org/lenny/network-manager/powerpc/download](http://packages.debian.org/lenny/network-manager/powerpc/download)

then install Network manager gnome
[http://packages.debian.org/sid/network-manager-gnome/powerpc/download](http://packages.debian.org/sid/network-manager-gnome/powerpc/download)

Download them both at once. There's a bug in the code for Network-Manager Gnome that will
display an error that says the nm-applet can't find resource or something, so open up a terminal and cd to /usr/share/icons and run:

gtk-update-icon-cache

that should fix it. not elegant - but it worked for me.don't know how or why, as I'm a noob, but it did.
matt

---

### Post by delucious on 2007-10-25
Tnaks Mattyb_uk
Do I need to uninstall Network Manager first?

---

### Post by Mattyb_uk on 2007-10-26
Yeah - and Network-Manager-Gnome, Bounce them both using Synaptic.

---

### Post by Mattyb_uk on 2007-10-27
Mr moderator, can we make this Network manager problem sticky? Affects everybody installing out of the box or upgrading on a G4 ibook pretty much?

---

### Post by aldous on 2007-11-03
I had the same problem with my prism2 based wireless card, but eventually solved it.
[http://devinvenable.blogspot.com/2007/11/wireless-problems-upgrading-ubuntu-to.html](http://devinvenable.blogspot.com/2007/11/wireless-problems-upgrading-ubuntu-to.html)

---

