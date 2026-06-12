---
title: "Difference is VMware and WINE"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by planemanx15 on 2008-03-04
To my understanding WINE lets me install some windows programs and VMware can install windows in Ubuntu?

---

### Post by Oldsoldier2003 on 2008-03-04
> **planemanx15 said:**
> To my understanding WINE lets me install some windows programs and VMware can install windows in Ubuntu?
yep in a nutshell thats the difference.

---

### Post by PeterJS on 2008-03-04
Programs running in wine will are able to access the physical system just like any other program. With VMware, only VMware itself has access to the physical hardware, and everything operating inside VMware has access to virtual hardware provided by it by VMware. Also programs running in VMware are completely unaware of anything that is happening outside of the VM, or there there is even a VM for there to be an outside of.

---

### Post by slughappy1 on 2008-03-04
WINE allows you to install some windows software in linux. Not all windows programs can be installed and not all that can be installed work fully. You can find out more about what programs can be installed and how well they work.

VMware lets you not only install windows in linux, but it is a program that can be installed on multiple operating systems and can have multiple operation systems installed in it. For example, you can be running Ubuntu and have an installation of VMware on it. In VMware you could have Windows XP, Windows Vista, Gentoo Linux, and others installed. Or you could be running a Windows (XP or Vista) machine and have several distributions of linux installed in it.

---

