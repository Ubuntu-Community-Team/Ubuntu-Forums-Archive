---
title: "Using/Installing a Virtual Machine"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-08-04
Hello,
I know there is a lot of documentation about installing and using Virtual Machines on Ubuntu but I want a few quick answers and didn't find them on here quickly.

I want to install a Virtual Machine and I am looking at VirtualBox.

1) I already have XP installed and dual boot. So do I have to install the XP again?

1b) If I need to install XP again, do I need to create a partition?

Thanks for the help in advance.

---

### Post by benx009 on 2007-08-04
virtualbox would be a good virtualization solution for you.  you would have to create a new virtual drive on your ubuntu partition (or you could use your windows partition if it is fat32, but the virtual drive size will be limited to 4 gigabytes) and install windows on that virtual drive.  the virtual drive will appear as a file in ubuntu.   sorry, but you can't use virtualbox to boot the windows installed on your windows partition.

---

### Post by ajgreeny on 2007-08-04
Virtual Box produce a great pdf of full instructions on their site.  Download it and it will tell you all you need to know and more.

---

### Post by wolfen69 on 2007-08-04
actually there is a workaround to use virtualbox to boot a windows partition. but it seemed VERY lengthy and not worth the effort.

---

### Post by MrFSL on 2007-08-04
I have had bad luck with the stability of VirtualBox. I use VMWare Server. It works for me.

---

### Post by deserthowler on 2007-08-04
I am running a Dell 1420n with Virtual Box.  I run Win2K in a 256 memory 10GB hard drive and it works well so far.  I disabled ACPI.  I don't seem to have very good multi-media support.  I can do what I need to do so far with no problems.

The installation and setting up of virtual box is quite easy, at least in Ubuntu.  The instructions are useful but not necessary to make a preliminary install.  There is a lot of useful information in the instructions though and they are well worth reading.

My problem comes when I try to install Linux distros for testing.  So far I tried Xubuntu and Wolvix.  The problem is in getting the screen to fit into my laptop screen.  I'm having disasters with  video drivers.  I haven't tried Debian Etch yet but will tonight. 

Earl

---

### Post by MatthewAPeters on 2007-08-05
I use VMWare at work, and Virtualbox at home - I like Virtualbox better.  The ability to resize the client window (or go fullscreen) and have Windows resize to utilize all of the space available is a very nice feature.  I find that XP boots and shuts down a little faster in Virtualbox - probably because I don't need to load it up with as many applications - more and more of my apps are in Linux.

---

