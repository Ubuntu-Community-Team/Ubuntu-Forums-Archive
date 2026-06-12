---
title: "Need a basic install of Ubuntu with Firefox and PDF viewer???"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by aw-pi on 2007-03-01
I am trying to create a very simple workstation for viewing PDFs for use in a manufacturing environment that employs people with disabilities. I am currently using DSL installed on a HDD inside an older Wyse Winterm thin client that has a PC based main board (AMD 400MHz [processor and 256MB RAM). It runs well, but I am having trouble moving the install to a CF card so the station can be diskless. Also, DSL has too many things added on and I don't have the expertise to tweak the install or remove items from the menus (like the games for example). Here is what I am looking for:

Linux based OS to run on a PC based AMD board.
Ethernet/DHCP capability
Firefox Browser
PDF viewer
nothing else, that's it

My Linux knowledge is extremely limited so any help would be greatly appreciated.  

thanks
Andru

---

### Post by khedron on 2007-03-01
You could probably try a server install, and then just install the packages you need at the command line using apt-get or aptitude.

Just from a glance at the package manager, you could try installing gnome-core, firefox and gpdf after you have the server install.

As for networking, I believe Ubuntu should support what you need out of the box, assuming your setup isn't too exotic.

Edit: as for installing it on a CF card, I am afraid I have no idea.

---

### Post by aw-pi on 2007-03-02
Thanks, that sounds like it's start, but I have a couple questions:

By server install, I assume you mean I would install the full package on a server system, then somehow connect the workstation to the server to due the partial installs? How do I get to a command line on the workstation that enables me to have networking ability to talk to the server?

I also believe the networking should be ok out of the box. I will be using a Wyse Winterm WT8440XL which is a PC based board running a K6-400 processor. The winterm runs Windows NTE SP6 (NT Embedded service pack 6 which is basically a stripped down version of NT4) that is inside a disk-on-chip. Adobe reader cannot be added to the install, that is why I am trying to go the Linux route.

As for the CF, DSL can be installed to a HDD, CF, USB drive, etc and have the entire system loaded into RAM by a boot option. I am hoping of doing something similar with Ubuntu.

---

### Post by afljafa on 2007-03-03
Download the alternate cd and do a base install. It will be minimal with networking and no x-server.

You would then use apt to install openbox, gpdf or kpdf and firefox.

Use the [Mythtv howto]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend") as a guide to setting up the base install and modify as needed.

---

### Post by hyper_ch on 2007-03-03
With 256mb ram I'd rather advice to use xubuntu instead of Ubuntu...

---

