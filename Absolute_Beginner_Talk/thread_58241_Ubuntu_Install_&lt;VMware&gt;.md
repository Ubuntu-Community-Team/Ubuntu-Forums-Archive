---
title: "Ubuntu Install &lt;VMware&gt;"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by arunpawar on 2005-08-19
Hi there!
I got pack of 5 CD's of ubuntu Hoary Hedgehog 5.04 on my mailbox Today.Then I started VMware 4.5.2 on windows, and i powered on the machine and installation begins,when i jumped to partitioner step then i found error of "Please check that hard disk is connected" when i continued partition step failed , i got one step back at previous then it said no filesystem found.and it forced me to move to main menu.Whenever i tried to parttion in installer process it is failing with above error.I m completely lost,What can i do?

If you want to know what is on VMware -Here goes
Simplymepis kernel 2.6x (Space allocated 6 GB)
Windows XP professional Service pack 1 (Space allocated 8 GB)

Each guest operating system is kept alone,to avoid conflict.I have  about 15 GB space for any other Guest OS for install on same drive,so i dont think there is any problem for Vmware.
Do i need to create partition for ubuntu on Vmware with boot floppy or else?Is my CD ok? or there is trouble with it.
I am not allowed to install any Linux on Real hardware so i m installing Ubuntu on VMware.Is there anyway where someone can help me step by step install 'ubuntu' on VMware 4.5.2 ?

---

### Post by tonysathre on 2005-08-22
during partition did u specify a root directory?

---

### Post by jiiim on 2005-08-24
Try using IDE disk in VMWare instead of SCSI. You may have to Edit your guest and remove the existing disk, then just Add a new and choose IDE for that disk.

---

### Post by lao_V on 2005-09-07
Does anyone know if Hoary works with SCSI drives (on VMware or otherwise)?

---

### Post by mlomker on 2005-09-14
[QUOTE=lao_V]Does anyone know if Hoary works with SCSI drives (on VMware or otherwise)?[/QUOTE]

I just installed it today using the SCSI option (VMWare v5 Workstation).  I'm having another problem, though--the keyboard acts like it's stuck if I type at more than about 1 character per second.  It's extremely irritating.  I've already experimented with kbdrate but it doesn't seem to help.  I wonder if this problem is unique to my laptop or a general issue with Hoary as a VMWare guest?

---

### Post by lao_V on 2005-09-15
[QUOTE=mlomker]I just installed it today using the SCSI option (VMWare v5 Workstation).  I'm having another problem, though--the keyboard acts like it's stuck if I type at more than about 1 character per second.  It's extremely irritating.  I've already experimented with kbdrate but it doesn't seem to help.  I wonder if this problem is unique to my laptop or a general issue with Hoary as a VMWare guest?[/QUOTE]

Do you remember which controller you used? LSI or BusLogic?

---

### Post by mlomker on 2005-09-16
[QUOTE=lao_V]Do you remember which controller you used? LSI or BusLogic?[/QUOTE]

I don't even see an option in any of the VMWare screens for that, which is odd because I know you can choose when running on a Windows host.  

It is using the LSI, though.

---

### Post by lao_V on 2005-09-16
In VMWare for Windows when you create a new VM, it gives you a SCSI HDD with BusLogic controller which will fail to install Ubuntu.

However, if you chose "Custom" and change the controller to LSI then Ubuntu will install without problem.

---

### Post by overcast on 2005-09-16
This problem is solved at
suggestafix.com

---

