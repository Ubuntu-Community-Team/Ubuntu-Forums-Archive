---
title: "Installing Network-Manager-Gnome"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by bourne- on 2006-10-18
How do you install network manager gnome? I have checked synaptic but I couldn't find it. What is it named as?

Using lately version of Ubuntu

thanks
todd

---

### Post by Super King on 2006-10-18
I believe the package name is called **gnome-network-manager**. Or you can just search Synaptic for 'gnome' and it should show up in the list.

---

### Post by testube_babies on 2006-10-18
Are you sure you have all of the repositories enabled?
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

The packages you need are network-manager and network-manager-gnome

---

### Post by bourne- on 2006-10-19
> **Super King said:**
> I believe the package name is called **gnome-network-manager**. Or you can just search Synaptic for 'gnome' and it should show up in the list.

Yeah I looked for it under that, but no such luck. I looked up networking as well and it wasn't their either. So I don't know whats goin on with that

---

### Post by sgornick on 2006-11-01
On a related note, once the network-manager-gnome package is installed this applet will be displayed in the notifier panel.  The package installer will add the app, nm-applet, to the "startup programs" (System -> Preferences -> Sessions, then select Startup Programs tab).

It took me a few more minutes than it should have to figure that part out so I am documenting it here in case it helps anyone else.

---

### Post by ciscosurfer on 2006-11-01
Try **network-manager-gnome**

---

### Post by 87esir on 2007-11-12
I have no net connection on my laptop and need to download networkmanager and the gnome networkmanager. I downloaded them from here [http://packages.debian.org/etch/network-manager-gnome](http://packages.debian.org/etch/network-manager-gnome) as someone above said those two files were all that were needed.

I transferred them to my laptop and unpacked them and when I do that it tells me dependency is not satisfiable:libatk1.0-0. I'm assuming if I loaded that then there would be another to follow until I downloaded about 30 files. Is there a package I can install that has all this in it?

I run ub6.06 i386/i686

thanks

---

### Post by jerrynewt on 2007-11-12
Go to System>Administration>Synaptic Package Manager and hit the search button. Enter network-manager. There are a lot of selections available.

---

### Post by 87esir on 2007-11-13
for some reason my package manager isn't working. see my thread at
[http://www.linuxforums.org/forum/ubuntu-help/108230-gees-please-help.html](http://www.linuxforums.org/forum/ubuntu-help/108230-gees-please-help.html)

---

