---
title: "[SOLVED] Could not find package checkinstall"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by mlentink on 2007-07-20
I just successfully compiled and installed syncevolution-0.5 on my notebook, so I thought I'd do the same on my desktop, both per the instruction in [this post]("http://ubuntuforums.org/showpost.php?p=2532774&postcount=55"). 
However, trying to install 'checkinstall' fails with a 'Could not find package "checkinstall"' error.
Universe is enabled in my sources.lst file, in fact I made sure the sources.lst files on my desktop was exactly equal  to that on my notebook (I copied it over).

Can anybody point me in the right direction?

---

### Post by meborc on 2007-07-20
did you do a "sudo apt-get update" after the sources.list file copy? and before doing "sudo apt-get install checkinstall"?

---

### Post by kidcharles on 2007-07-20
I have checkinstall available in Synaptic, it says it is in "Section: System Administration (universe)" if that helps at all.

---

### Post by mlentink on 2007-07-20
> **meborc said:**
> did you do a "sudo apt-get update" after the sources.list file copy? and before doing "sudo apt-get install checkinstall"?


AAAARRRRRGGGGGHHH!!!!!!
Stupid mlentink! Stupid Stupid mlentink!!!

Thx meborc!

---

