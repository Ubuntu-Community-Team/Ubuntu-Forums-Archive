---
title: "Ubuntu at work"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by saucy on 2007-12-04
I have been using Edgy for the past month on my home PC and absolutely LOVE it!  I would like to use it on my work PC, however I have several programs that are necessary for my work  that will not run on Linux (per my IT dept anyway).  I am considering installing Edgy and running a virtual windows program for the applications I need in Windows.  My question is whether or not this is possible to do, which virtual windows machine is the best to use, and if I would need to re-install all of my programs when I make the switch.  I am sorry for being so ignorant, however I do appreciate any advice someone can give me!  My husband thinks that it is possible, however I would need to re-install all of the programs and might lose some data such as my email in Outlook (since I won't be using Outlook if I go to Ubuntu).  Thank you all for your help!

---

### Post by PeterJS on 2007-12-04
I'm an ardent Ubuntu supporter, and would love to see it adopted more widely in both work and home user environments, but there is no way I'd let somebody in a network I'm administrating and supporting install the OS of their choice. Even if it is possible I don't think it would count as a good idea in any way shape or form.

---

### Post by Paqman on 2007-12-04
The most popular virtualisation options are VMWare and Virtualbox.

You can get either from the repos. After installing you then create a "virtual machine" and install the guest OS onto it just like a real PC. So yes, you'd need an install CD and a Windows license key, and you'd need to reinstall all your software and any data you backed up before wiping the original Windows install.

One disadvantage of VMs is that they can't see anything on the hard drive of the host machine. So in order to share data between a host and guest OS you need to put that data on a network location.

---

### Post by baxterdog on 2007-12-04
What you want to do here is practice this on a home machine. I've got a laptop with just Ubuntu on it that I can take back and forth from home and work. My home desktop is dual boot on its way to being only Ubuntu, and my work desktop is winxp.

I'll make the complete switch if I can get the hardware license key to work that is necessary for my workware.

I do agree that your IT crew may not want people choosing their own OS's, but it depends on where you work! At my place it is an individuals choice in so far that the work they have been hired to do can be done with that machine. My primary software is only made for Windows so it would be unwise for me to just flagrantly choose a mac or Ubuntu as my primary system.

---

