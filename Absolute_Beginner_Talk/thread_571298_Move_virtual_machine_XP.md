---
title: "Move virtual machine XP"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-10-09
I have my drive partitioned with Ubuntu so that my home folder is on a different partition.  I have a XP installed virtually using VMware and have allocated 9Gb for it.

How can I move the virtual XP from the boot partition to the home partition so that it is unaffected by the forthcoming upgrade to Gutsy Gibbon.

---

### Post by Joeb454 on 2007-10-09
As far as my experience with VMWare goes, 

Just move the folder where the vmx and vhd files and whatnot are, onto the /home partition.
As far as your system's aware, XP is just one big 9Gb file. Again this is just my experience, if anybody can confirm this I'd be grateful :)

---

### Post by luisromangz on 2007-10-09
The file the previous poster refers is probably located under /var/lib/vmware/Virtual Machines, if you didn't told the program otherwise when you created the virtual machine.

---

### Post by Joeb454 on 2007-10-09
I wouldn't know exactly where the filels default to, as I only used VMWare in Windows (funnily enough, to use Ubuntu before I did a proper install).

---

### Post by ushills on 2007-10-09
Thanks I have now moved the files to under my home partition.

However, how do I now advise Vmware of the revised location for Windows XP.

---

### Post by Joeb454 on 2007-10-09
I believe when you open it up, it brings up a Window saying Open or Download, and then below that a list of recently opened files.

Choose the option to open a file, and then navigate to where the file is now located.

* I'm not sure if this is the same for linux as i've only used VMWare on vista

---

### Post by anaconda on 2007-10-09
Yeah. just select open (if I remember correctly)

VMWare will notice that the path has changed and it will ask you has it been moved or copied.. And should vmware make a ned "some ID " for it. 

It doesn't matter which you choose.

---

### Post by Joeb454 on 2007-10-09
I figured it wouldn't really change too much from platform to platform :)

Always nice to have somebody else agree with me ;)

---

