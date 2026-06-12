---
title: "Best Way to Run Windows In Parallel"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by TrompeLaMort on 2007-07-20
Hi,

I'd like to install windows alongside Linux.

Ideally, I'd like to run it in a virtual machine most of the time (e.g. for school work), but when I'd like to play games, I'd like to be able to boot into a normal copy so I don't have to lose performance (Halo would be pretty laggy under a vm)

What's the best way to go about this?  It appears I could run Xen, Qemu, or VMWare, but can I run in parallel and run in a VM?

Thanks,

Dan

---

### Post by kevin11951 on 2007-07-20
i use [http://www.virtualbox.org/](http://www.virtualbox.org/) because it is a virtual machine made for ubuntu... but i dont know about the rest. you could try reformatting with windows, and then re installing ubuntu over that with grub (someone else please explain how).

---

### Post by saadakhtar on 2007-07-20
try [VMware]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html"). I have used it and it works pretty well with ubuntu but i would certainly suggest a host machine over 2.0 Ghz with 1.0 GB RAM (or over would be even better).
I deployed vmware with FreeNx to acces my office server and then run windows on VMware and it works without a problem.
If you do a kernel update you will however need to update your kernel headers to get VMware to work again. You can follow[ this link]("http://ubuntuforums.org/showthread.php?t=328480") to fix this problem.

cheers

---

### Post by kyphi on 2007-07-20
I don't understand what you mean by 'run Windows in parallell'.

If you want to have an installation of Windows as well as Ubuntu, then, yes, that can be done.
You can also run Windows in a virtual machine on Ubuntu.  As kevin11951 pointed out, VirualBox is an excellent choice.

To have two operating systems on one hard drive works but is not the best solution.  Better to separate them onto separate hard drives.  If one drive fails or if your Windows drive becomes corrupted, you can effect repairs from the working drive.

To run too many programmes in Windows via VirtualBox is not 100% effective either.  I run a graphics programme in VirtualBox and that works fine.

Perhaps it might be wise to map out exactly what you would like to accomplish and then you can ask how your wishes can be realised.

---

