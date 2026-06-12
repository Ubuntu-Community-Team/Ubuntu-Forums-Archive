---
title: "New profile with access to default applications only?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Cesa on 2007-05-29
I am new to Linux, but not to programming or computers in general.

I have created an application that depends a couple of different sources (glut, glew, CG, some .h-files etc. etc.), and before I distribute it I need to know what the user must install to get the application running. There are some I am sure are needed, but then there are some I'm not sure about.

What I need is a clean Ubuntu installation (preferably, profile) to test on. But when I create a new profile it has access to things I installed on the original profile.

I don't have access to another computer with the needed hardware, and I don't want to just try to uninstall things and test the applications, partly because some of the things were a pain to install for a newbie like me and I don't want to do it again, and partly because I cannot be sure everything will be uninstalled properly.

How can I test my application on a "clean" Ubuntu installation on the same computer?

---

### Post by starcraft.man on 2007-05-29
Well, sounds to me like the easiest solution is to make a VM for dedicated testing purposes. I have multiple myself for when I dabble in a bit of web page making and a few other things.

Have a look at [virtual box]("http://www.virtualbox.org/wiki/Downloads"), just download the Feisty deb and off you go. You will of course have to install Ubuntu into the VM, but it will be a great help to a coder. You can install more linux distros if you want to test it across more than just Ubuntu :).

VMs are very helpful when it comes to testing, hope that helps. Just seems the easiest solution to me. Just remember a VM will run 3d apps (beryl for instance) very poorly, otherwise it works just as good as an install.

Whats the app btw?

---

### Post by Cesa on 2007-05-30
Thanks for the help, I ran in to more problems though.

I am running Virtual Box, I have installed Edgy on it (need to test Edgy before upgrading to Feisty). The files I need are on a NTFS partition. I am using NTFS-3g to access those partition on my regular system, so I installed it on the box as well, but I can't seem to find the partitions (I guess they are not accessible from the box unless I make them, but I don't know how). I also cannot access my USB memory stick. I enabled USB in the settings for the box, but when I try to access it I get:

"Not permitted to open the USB device. Check usbfs options."

I tried to read the "USB not working"-section in the user manual, but it goes way over my head... ;) There is a reason why I posted in this particular subforum :)

You asked about the application, it is a GPGPU application for my master thesis work at the university. It is more or less done, but I need to test it on a "clean" system.

---

