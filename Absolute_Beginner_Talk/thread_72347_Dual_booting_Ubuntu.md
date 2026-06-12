---
title: "Dual booting Ubuntu"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Alpha_Cluster on 2005-10-06
Ok i installed ubuntu after i reformated my computer and got a 
NTFS partition for storage, a Ubuntu Partition, and a Windows partition.  Now the last thing i installed was the windows partition.  and now at the boot select screen though all i get for boot options is the NTFS partition and Windows.
Is there anyway i can get this to show Ubuntu in the boot prompt?

---

### Post by mättä on 2005-10-06
Windows automatically overwrites the bootloader of ubuntu (GRUB). To install GRUB in the master boot record (= the part of your harddrive that contains the information necessary to boot) you will need the Ubuntu install CD again. You will find detailled information on how to set up GRUB after a Windows install here: 
[http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by matthewv on 2005-10-06
If you still have Ubuntu installed, you should then be able to boot it using the install cd (use the recovery option) and then reinstall the boot loader from there...

EDIT: sorry, matta beat me to it

---

### Post by quattroman on 2005-10-07
I saw one time a link to a page that explained how to partitinate and install dual boot. I forgot to bookmark it, and I wanna use it now...anybody knows which site I am talking about?

---

