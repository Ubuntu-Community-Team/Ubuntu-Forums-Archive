---
title: "Every file is Read Only, Unable to write files"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by shof on 2008-02-03
I am trying to edit a couple files so i can make a couple of programs to work, including the vmware sharing folders.  I manage to get the tools program installed, however when i try to install the driver using this guide: [http://www.debuntu.org/how-to-vmware-tools-hgfs-module-on-ubuntu-gutsy-gibbon-7.10](http://www.debuntu.org/how-to-vmware-tools-hgfs-module-on-ubuntu-gutsy-gibbon-7.10) i get stuck at the part of were i have the edit the compat_slab.h. Now the problem is, that the file is deeply read-only meaning there is no way to write to the file. I have try using sudo/vim, logging into root, changing file premssions. No matter what i am doing, i am getting not getting file access

So my problem, how do i make it system wide to write to files and prevent this problem or atleast write to this stupid file

(When i use the vim method as stated in the guide, i get like locked out saying the file is read error and unable to save even when i am logged in as root and root in the terimanl



(note: its a bit strange that a root user account cant change files...um...what the....?)

---

### Post by dcstar on 2008-02-03
> **shof said:**
> I am trying to edit a couple files so i can make a couple of programs to work, including the vmware sharing folders.  I manage to get the tools program installed, however when i try to install the driver using this guide: [http://www.debuntu.org/how-to-vmware-tools-hgfs-module-on-ubuntu-gutsy-gibbon-7.10](http://www.debuntu.org/how-to-vmware-tools-hgfs-module-on-ubuntu-gutsy-gibbon-7.10) i get stuck at the part of were i have the edit the compat_slab.h. Now the problem is, that the file is deeply read-only meaning there is no way to write to the file. I have try using sudo/vim, logging into root, changing file premssions. No matter what i am doing, i am getting not getting file access

So my problem, how do i make it system wide to write to files and prevent this problem or atleast write to this stupid file

(When i use the vim method as stated in the guide, i get like locked out saying the file is read error and unable to save even when i am logged in as root and root in the terimanl



(note: its a bit strange that a root user account cant change files...um...what the....?)

Well, if you are working on a pseudo-cdrom then it can be difficult to write things.....

That HOWTO assumes you have extracted the vmware-tools files to your Home directory, have you?

---

### Post by shof on 2008-02-03
> **dcstar said:**
> Well, if you are working on a pseudo-cdrom then it can be difficult to write things.....

That HOWTO assumes you have extracted the vmware-tools files to your Home directory, have you?

yes..the files and everything are in the home folder. When i try to edit the file in the home folder, i get that message that its read only and cant save even thru i am using root

---

### Post by The Cog on 2008-02-03
Files copied off CD always come out read only. You need to change the file permissions. You can right-click the file in nautilus and go to the permissions tab, or in a console use **chmod +w filename**.

---

