---
title: "What will happen if I click install while using ubuntu livecd in VMware"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-02-13
Ok, i am about to install Ubuntu within the VMware virtual machine. is this going to kill my computer?

I went to "partition" just in case, and the "VMware virtual drive" is larger than my real hard drive.

I just don't want to destroy everything

---

### Post by shareMenaPeace on 2007-02-13
When you start up vmware you can choose

create new virtual machine

a wizard starts click NEXT till it ask you for the operating system to install.

Choose linux and scroll down and choose here ubuntu.
Than have the ubuntu cd in the cdrom. Than point the install folder to your vmware folder or where you store the operating system
If vmware is huge than good. Make the new virtual partition with ubuntu maybe 10 or more gb huge if you got enough.

---

### Post by lamego on 2007-02-13
> Ok, i am about to install Ubuntu within the VMware virtual machine. is this going to kill my computer?
Before proceeding you should understand how VMWare works, the virtual machines don't have access to the hosting system so there is no way for a VM install to "kill" your computer,

> I went to "partition" just in case, and the "VMware virtual drive" is larger than my real hard drive.

This is only possible if you have selected a dynamic allocation policy, on such case you will get problems when VM tries to use this space, again, this is a VM problem which can't destroy any data.

---

### Post by derjames on 2007-02-13
> **lamego said:**
> Before proceeding you should understand how VMWare works, the virtual machines don't have access to the hosting system so there is no way for a VM install to "kill" your computer


Yeah, Everything is going to be clearer if you read the vmware documentation... please have a look at

[http://www.vmware.com/support/pubs/](http://www.vmware.com/support/pubs/)

cheers

---

