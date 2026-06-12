---
title: "Resizing Ubuntu Partition &amp; Dual Boot With KUbuntu"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-15
Hi, I'm interested in trying out [LinuxMCE]("http://linuxmce.com/") (Linux Media Center) and my first idea was to just install it on my Ubuntu box. But then I read about it on their website, and it rewrites some conf files and delete the nVidia driver and the beta version has fixed some of these issues, but it only runs on KUbuntu at the moment.

I have Ubuntu taking up all the space on my harddrive (1partition) Can I (maybe during the live cd install) resize the Ubuntu partition and free up some space where I can then install KUbuntu, and then dual boot?

thanks.

P.S. Please mention if you know of any problems or issues I should be aware of during the process.

---

### Post by dbbolton on 2007-06-15
> **kasperbs said:**
> Hi, I'm interested in trying out [LinuxMCE]("http://linuxmce.com/") (Linux Media Center) and my first idea was to just install it on my Ubuntu box. But then I read about it on their website, and it rewrites some conf files and delete the nVidia driver and the beta version has fixed some of these issues, but it only runs on KUbuntu at the moment.

I have Ubuntu taking up all the space on my harddrive (1partition) Can I (maybe during the live cd install) resize the Ubuntu partition and free up some space where I can then install KUbuntu, and then dual boot?

thanks.

P.S. Please mention if you know of any problems or issues I should be aware of during the process.
you can install KDE inside your existing ubuntu installation. go to System > Administration > Synaptic. search for 'kubuntu', and mark the package 'kubuntu-desktop' for installation.

---

### Post by candtalan on 2007-06-15
after installing the kubuntu-desktop you wil have the choice to run either the ubuntu (gnome) or kubuntu (kde) environment - at the time when you are asked for your login password - there is a menu with Session choice.

---

### Post by kasperbs on 2007-06-17
Thanks I will giv that a rty, sounds like the best solution..

---

### Post by dptxp on 2007-06-17
Maybe just install kde-core should do your job.

---

### Post by kasperbs on 2007-06-19
Ok that completely screwed up my system. Apparently using that method is still using some of the configuration files from my Ubuntu machine, which I hoped to save from being rewritten. i wouldn't advice this to anyone trying to install LinuxMCE on a KUbuntu box. This will not save your original configuration files. You will end up with broken packages, changed conf files etc.

Thanks for your suggestions anyway.

back to the original question now ;)

> Can I (maybe during the live cd install) resize the Ubuntu partition and free up some space where I can then install KUbuntu, and then dual boot?

Any help greatly appreciated

---

### Post by ggaaron on 2007-06-19
Boot from a live cd (maybe not Ubuntu because it tries to mount partitions all the time and you can't work, I've used [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) and use gparted - it's very easy to use and can do many things with partitions.

---

