---
title: "VMware: Windows in 1280*800 Resolution not possible ?"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-07
I install vmware tools and my screen linux is 1280*800

the vmware doest accept the 1280*800 in fullscreen 
 
Is there a way 

thank you

---

### Post by jrjazzman on 2006-10-01
I have the same problem.  Anyone know if windows under Vmware can run at 1280x800?

---

### Post by NetworkGuy on 2006-10-01
I believe that resolution isn't supported with the VMware video driver you loaded with the VMTools.

---

### Post by mickymouse on 2008-03-11
You must go to /var/lib/vmware-server/Virtual Machines/*the name of your machine* . There edit the file *the name of your machine*.vmx and add the following lines 
svga.maxWidth = "1280"
svga.maxHeight = "800"

---

### Post by brett611 on 2008-03-18
Check this link out - seems to indicate that if you follow these instrux your vmware reso will match your native os res

[http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html](http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html)

---

