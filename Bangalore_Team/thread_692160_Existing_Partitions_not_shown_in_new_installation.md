---
title: "Existing Partitions not shown in new installation"
date: 2008-02-09
forum: Bangalore Team
---

### Post by sourabhsharma149 on 2008-02-09
Hello Friends,

I am trying to install kubuntu on  my existing partition scheme as

1) Primary Partition : 30 GB ( Vista)

2) Extended Partion:         i)   25 GB ( D Drive)
                                          ii)   25 GB ( E Drive)
                                         iii)   10 GB ( F Drive)
                                         iv)   /boot ( Gnome ubuntu)
                                         v)   / ( Gnome ubuntu)
                                         vii) FREE PARTITION 7 GB <---

I want to do it on 7 GB free partition.
BUT when I try to install from  live cd of kubuntu then it doen't show my existing partition but a complete 120 GB disk and ask to create new partion table...
I am sure by this i will end up with spoiling my existing scheme...
Please help how can opt from my exiting partion the / for kubuntu..

Thanks

---

### Post by aiser on 2009-12-01
;)

---

### Post by kalasoka on 2010-03-16
When you are trying to install, the entire hard disk will be shown. You can select the 'Advanced' option, and add (or delete) new (or existing) partitions according to your need. So, there you can delete your 7 GB partition and recreate with necessary disk space and a file system type. And then you can install your Linux there.  This is the general concept for all Linux distros, including Ubuntu and XUbuntu.

---

### Post by msaravanan77 on 2010-10-26
can you please paste the output of 
fdisk -l

---

### Post by tushar maroo on 2010-12-30
> **sourabhsharma149 said:**
> Hello Friends,

I am trying to install kubuntu on  my existing partition scheme as

1) Primary Partition : 30 GB ( Vista)

2) Extended Partion:         i)   25 GB ( D Drive)
                                          ii)   25 GB ( E Drive)
                                         iii)   10 GB ( F Drive)
                                         iv)   /boot ( Gnome ubuntu)
                                         v)   / ( Gnome ubuntu)
                                         vii) FREE PARTITION 7 GB <---

I want to do it on 7 GB free partition.
BUT when I try to install from  live cd of kubuntu then it doen't show my existing partition but a complete 120 GB disk and ask to create new partion table...
I am sure by this i will end up with spoiling my existing scheme...
Please help how can opt from my exiting partion the / for kubuntu..

Thanks
i think you are not installing manually......it is the last option in the setup.......so try that

---

