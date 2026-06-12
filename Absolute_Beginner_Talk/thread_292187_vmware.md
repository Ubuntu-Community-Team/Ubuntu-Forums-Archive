---
title: "vmware"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by kornoholio on 2006-11-03
can anyone tell me how to run winxp virtual machine in ubuntu usin vmware?
a step by step installation :-k

---

### Post by igknighted on 2006-11-03
what version of VMWare are you using?  I would recommend you use VMWare server, it is free and you can download it from their website.  The install is fairly easy, just press enter lots of times and accept the defaults.  Once VMWare is installed, all you need to do is put your MS Windows disk in the drive and turn on the virtual machine, and from there on out it is just like any other windows install.  One exception, there is an option in the vmware window to install vmware tools... once windows is fully installed do this and your mouse will move smoothly.

Your alternative is VMWare player.  You can install this from the repo's, but it has given me nothing but trouble, and it is only for playing virtual machines, you have to find other more complex ways to create the virtual windows machine before you can use it.

---

### Post by Bachstelze on 2006-11-03
[Here](https://help.ubuntu.com/community/VmwareServer) you go :)

---

### Post by kornoholio on 2006-11-03
i got VMware server 1.0.1 .. my problem is that when i run vmware , it asks for a .vmx file .... i got a .iso of winxp .... i dunno wat to do , i really need to run xp on my ubuntu for testing purpose

---

### Post by igknighted on 2006-11-03
what if you burned the iso and installed winxp from the cd?

---

### Post by kornoholio on 2006-11-03
how will i install it from a cd ? it asks for a .VMX file ! i only got .ISO !can anyone recommend a manual for vmware or a howto?

---

### Post by forger on 2006-11-03
I think there's an option with which you can point your vmware cd-rom to an iso file, but I'm using the workstation, so I don't really know

---

### Post by distroman on 2006-11-03
If you got vmware server up and running, then “create a new virtual machine” follow the setup. 

When that's done you can “edit virtual machine settings”. 
Here you can set the specs, RAM, floppy etc, have a look through it.
If you want sound you have to "add" it here as well. 

You can install from a iso on your harddrive. Go to “CD-ROM” then “Use iso image” and browse it. 
Then vmware should pick it up, once you power it on.

---

### Post by funrider on 2006-11-03
> **kornoholio said:**
> how will i install it from a cd ? it asks for a .VMX file ! i only got .ISO !can anyone recommend a manual for vmware or a howto?

u need to first create a virtual machine by vm workstation or whatsoever. .vmx is the configuration file of the virtual machine and you need that file to boot it up. 

once you have the new vm machine, you need to set it so that it can recognize your real CD rom (I am not sure if VM is smart enough to find virtual CD drive, please google it yourself). you will also need to add a virtual harddrive large enough to house your xp installation. when it is all done, boot up the VM with your winxp CD in the CD rom and run through the regular XP installation.

pm me if you need further help:KS

---

### Post by doctorberen on 2006-11-03
kornoholio,

It seems to me you downloaded the wrong file. It seems like you are talking about the VMWare Player instead of the VMWare Server, which are two different things.

In the VMWare Server Console there's a button that will ask you to create a new virtual machine. From there, it will ask you for your windows CD.

---

