---
title: "Vmware server - trying to run Windows in LInux"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-19
After having tried Vmware player and Virtualbox with the same problem when Windows tries to start up, I downloaded VMware server and the patch so I can run it in 7.04.  Just a little background:

I have a Gateway MX3215 laptop which I have dual-booting Windows and Ubuntu 7.4.  I can pretty much find what I want in Linux with a couple of exceptions - Family Tree Maker 10 and (you can chuckle here;)) shockwave so I can play the daily jigsaw.  

So, I got VMware server installed and created a Windows VM with a 13 gig virtual disk.  I thave  the system restore cd (I don't have an actual XP cd, but the operating system recovery CD from Gateway).  When I put that CD in and start the virtual machine, it goes through the recovery process and then reboots.  As soon as Windows tries to come up (I briefly get the Windows XP screen), I get a blue screen (it's so quick but I got lucky after many tries and got a screen capture of it).  The window says "A problem has been detected and Windows has been shut down to prevent damage to your computer".  It then goes on to suggest running a virus scan, removing any new drives and controllers and running chkdsk.  First I can't do any of those since I can't boot the Windows vm, not even in any form of safe mode.

Any help would be greatly appreciated:)

---

### Post by headcronie on 2007-06-19
I doubt the recovery cd install will work.  Running that version in a virtual machine, will crash, as it's not really running the hardware.  VMware server is, and thus, it's reporting different hardware specs than the restoration cd says it needs.

---

### Post by gcos7 on 2007-06-19
I'm thinking that since the recovery procedure also creates a recovery "partition" in the virtual disk.

Is there any way to copy my existing Windows XP partition to a virtual disk for VMware server?

Thanks!;)

---

### Post by suhanduman on 2007-06-19
vmware converter: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by gcos7 on 2007-06-19
Looking at the vmware converter documentation, it ONLY runs in windows and requires some sort of backup medium, and looks to prefer backing up across a network.  I am running a single laptop and want to copy the existing Windows installation in to VMware server in Ubuntu Linux.  Is there any tool which runs in Linux which will create a VMware virtual machine from an existing Windows installation on the same disk (i.e., dual boot)??

Thanks;)

---

### Post by suhanduman on 2007-06-20
1. Yes converter is running on Windows.
You have to boot into windows and run the program there. It will convert your existing Windows to a vmware machine. (You have to have a free space or external hdd at least the size of your windows.)
2. It really does not need any tape or something.

I have used it several times to convert windows to VM.

---

