---
title: "running dapper in vista with qemu"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by robertc1985 on 2008-02-16
:confused:
i have qemu for windows, and i want to run ver 6.06 of ubuntu within windows vista, it comes with a really simple version of red had with no GUI

i already have the live disc of 6.06 dapper, i just want to know how to make a disc image or whatever i i need to do to run ubuntu in vista, and i also require to run the whole OS and not just the live cd option, and it must be 6.06 because i don't think easyubuntu works with any other version! sorry for being so picky, this is just what i need for my setup

it will be a very long time before i return to this post, so my other contact options are email, robert@robertc1985.com and Yahoo! Instant Messenger ID RobertC1985

thanks tons for at least trying, and who knows, i may get to break murphy's law this time and actually accomplish what i set out to do

by the way, i grew up with microsoft my whole life, i know very little about linux! so please keep that in mind

---

### Post by candtalan on 2008-02-18
I do not really know how to do it in windows, let alone vista, but what you ask is just to create an image from the cd. The process is  I think basically the process to copy the complete cd but save the information after the copy process, not throw it away as would usually happen. In the app I use (k3b in kubuntu not windows) the settings options for copy cd include
simulate, create image, only create image, and remove image. Your cd burning application will hopefully have similar options.

The cd image you are hoping for will be an iso file  filename.iso  Note that although this is your desired end result, you are not 'creating' an iso, you already have the iso (image) on the cd.

consider also:
Latest versions of ubuntu can easily have codecs installed, they are much more functional that 6.06 was. 6.06 is close to obsolete now.

If you have two cd drives in the machine, a cd rom that you can boot the machine from, and a separate cd writer, then using a live cd (ubuntu, kubuntu, whatever) by booting from the cd rom drive then you can use the cd writer as you wish in ubuntu while still running the live cd.

also: 
wubi project allows an install of ubuntu from windows into a windows file. When install is complete you can choose to start in windows or ubuntu. Later you can simply uninstall wubi, and the folder goes.
[http://wubi-installer.org/index.php](http://wubi-installer.org/index.php)

---

### Post by robertc1985 on 2008-06-03
thanks anyway, this was all before i discovered wubi

---

