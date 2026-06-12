---
title: "problem with gnomebaker"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-04-08
hey when i try to burn ISO images with gnomebaker it freezes, and doesnt do anything. i burned a data cd and it worked though. heres the output:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.

---

### Post by Sef on 2006-04-08
I have had problems with Gnomebaker too.  What I did to solve the problem was download and use K3b.  It works just fine in Gnome.

System > Administration > Synaptic Package Manager > Search > Highlight K3b > apply

---

### Post by StefanoCole on 2006-04-10
malavar, do you have the package mkisofs installed?

Stefano

---

