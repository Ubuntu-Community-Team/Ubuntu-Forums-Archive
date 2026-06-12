---
title: "some general questions about ubuntu 7.04"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-04-21
Hi
Thank you for reading my post
Please let me have answers for following questions if you know.

- Does 7.04 come with Beryl or we should install it ourself?

- How does 7.04 compare with OpenSuse 10.2 in term of new bundled software and stability?

- I will recieve a DVD of Ubuntu 7.04, does it has glassfish and netbeans as pointed?

- How i can install Kubuntu desktop on my ubuntu ? I prefer KDE.

- What will happen to my boot sector (I have two hard disks) if I install Ubuntu on my current OpenSuse 10.2 installation?
and finally I heard that Ubuntu 7.04 has all propriatery drivers like Nvidia inside its DVD, is that correct?


Thanks

---

### Post by Iceni on 2007-04-21
> **legolas_w said:**
> Hi
Thank you for reading my post
Please let me have answers for following questions if you know.

- Does 7.04 come with Beryl or we should install it ourself?

- How does 7.04 compare with OpenSuse 10.2 in term of new bundled software and stability?

- I will recieve a DVD of Ubuntu 7.04, does it has glassfish and netbeans as pointed?

- How i can install Kubuntu desktop on my ubuntu ? I prefer KDE.

- What will happen to my boot sector (I have two hard disks) if I install Ubuntu on my current OpenSuse 10.2 installation?
and finally I heard that Ubuntu 7.04 has all propriatery drivers like Nvidia inside its DVD, is that correct?


Thanks

I can answer some:

1. Feisty comes with Compiz. You can easily install beryl from synaptic, tho.

2. You can install KDE from synaptic as well. 

3. From my own experience grub will simply add your new install.

4. Feisty comes with nvidia drivers, just eneable restricted drivers.

---

### Post by raja on 2007-04-21
I will answer the ones I know about.

You will have to install beryl - it is not pre-installed.

Installing KDE is as easy as ```
sudo aptitude install kubuntu-desktop
``` However, if you have tried them before and have decided to use kde over gnome, it would be better to install kubuntu itself.

Ubuntu should recognise the suse installation and add it to the grub menu, but I am not sure. Sorry, but I dont know what is contained in the DVD.

---

