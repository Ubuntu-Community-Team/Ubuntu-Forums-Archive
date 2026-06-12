---
title: "Windows based Programs in Ubuntu"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by Npenguin on 2008-07-10
I use The Adobe Creative Suite CS 3, Rhino 3-D_4, Corel Painter X, Autodesk 3-D Studio Max 9, and light Wave. 

Unfourtunatly, I have already bought all this software which I need and I am use too and use daily. In my search on ebay for windows XP I've found a version of ubuntu that says it is windows-based linux is that true?

What really is the benifit if Linux can't run any or much windows based software? 
Industry standard software is just that standard. I don't mind learning new programs my school is picking up Blender in addition to 3d studio max. 
As an Industrial Designer there are set programs in the field that we need to be highly skilled in, I'm sure that goes for graphic design, visual communications and illustration fields as well. 

How do people in the creative fields find the balance of Linux and industry standards (mac or win based)? student or professional.

---

### Post by mabovo on 2008-07-10
You can use virtualization. Try XEN.

---

### Post by Npenguin on 2008-07-10
Ive also heard wine,virtual machine, qemu as options. I good of a gurrentee of working do these programs have? 

I use The Adobe Creative Suite CS 3, Rhino 3-D_4, Corel Painter X, Autodesk 3-D Studio Max 9, and light Wave. Will these have issues?


thanks for your help that was FAST!!!!

---

### Post by cyberdork33 on 2008-07-11
Wine is completely different than a VM. Wine brings windows APIs to Linux. thus you are literally "translating" the software calls into linux native versions. since this relies on someone creating the translators, and the windows OS is closed, there is a lot of reverse engineering applied which does not always match the windows functions exactly. So not EVERY application will work. There is a database of applications that will work with wine on their website:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

A virtual machine, on the other hand, is more like a "machine emulator". You have to setup the machine config, then boot the machine with the windows install cd in your computer and install windows, etc. once that is done with that, you can install your applications, etc.

VMs work quite well, though there are limitations (3D graphics), and they require a full-install of windows. Commercial solutions such as VMWare are used so that one "real" machine can host several virtual servers on a network. VirtualBox is an excellent open source VM and runs Windows quite well.

---

### Post by snowpine on 2008-07-11
Hi Npenguin, the simple truth is that Windows applications are going to run best on Windows. If you have specific applications that you need to use every day, you are best off running Windows. I do not think that reflects poorly on Linux; after all, Linux apps will run better on Linux than on Windows, right?

There are ways to get Windows apps running in Linux (WINE and VirtualBox are two of them), and if your particular app may work great in Linux if you are lucky. But the easiest thing to do is set up a "dual boot" where Windows and Linux co-exist on separate partitions on your hard drive. That way, you can choose the best tool for the job each time you log in.

I use Adobe all day long at work, running on Windows XP. But when I get home, it's all Linux baby!

---

