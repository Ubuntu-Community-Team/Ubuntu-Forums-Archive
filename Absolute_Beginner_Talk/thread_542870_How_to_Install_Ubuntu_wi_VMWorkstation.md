---
title: "How to Install Ubuntu w/i VMWorkstation"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by c5vetter on 2007-09-04
I am running a Windows machine with XP and becasue there are some applications that are not available within Linux, I bought and installed VMWorkstation in anticipation of installing and running Ubuntu - how do I accomplish this with the LiveCD which I also purchased?

Do I start my computer, then start VM, and then what?

---

### Post by irish_flu on 2007-09-04
Your VMWare manual should walk you through installing any OS.

If I'm remembering correctly, you start up the VMWare Console and select "new virtual machine".  You insert the CD, boot the new VM, and you're on your way.

---

### Post by bakaotaku85 on 2007-09-04
> **c5vetter said:**
> I am running a Windows machine with XP and becasue there are some applications that are not available within Linux, I bought and installed VMWorkstation in anticipation of installing and running Ubuntu - how do I accomplish this with the LiveCD which I also purchased?

Do I start my computer, then start VM, and then what?

You should be able to load the live disk normally in a created virtual machine environment, but you may run into one snag.

If your live CD is unable to install to a VMWare Virtual Machine, pull up the machine's properties after you have created one. Delete the virtual SCSI drive and "Add a new device", this time a virtual IDE drive. For some reason, Anaconda has trouble locating virtual SCSI drives on some distros, and I think Ubuntu is one of those.

---

### Post by dpj23 on 2007-09-04
Building a vm Ubuntu machine is no different than any other OS that can be install in VM workstation.  With that said, I would make these as my minimum requirement for installation.

512mb memory allocated towards - Ubuntu guest

10 GB hard drive minimum

I always allocate space prior to installation.  As VM workstation will advise you, it does take a couple of minutes to do so... However, this way has been 100% successful for me... So I stick with what works...

Lastly, do not try and run Beryl on a VM quest...  It just plays all kind of games with the machine and will more than likely crash it once it is attempt to start...

---

