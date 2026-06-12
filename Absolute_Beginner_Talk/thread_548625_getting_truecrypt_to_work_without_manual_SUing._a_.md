---
title: "getting truecrypt to work without manual SUing. a group permission question!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-11
hey all.

i'm trying to get Forcefield to work for my truecrypt, and i noticed that it's failing to function because truecrypt needs root permission to mount volumes. i tried running truecrypt from the command line as root and it worked fine. so i after some looking i found this ([http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user](http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user)) guide on how to give normal users the ability to mount - and use - volumes from truecrypt.

but i don't think that it's a guide for ubuntu, as i couldn't find the bashrc file it says to edit, but instead found bash.bashrc    there seem to be further differences between the walk-through and my machine, and i really don't want to mess anything up. 

basically it gives a group permission to run truecrypt as root without having to enter the root password, which seems like a security risk. would it be easier to reinstall truecrypt as a user? or does truecrypt always need root permissions?

running fiesty 7.whatever

---

### Post by dwhitney67 on 2007-09-12
> **ijason said:**
> hey all.

i'm trying to get Forcefield to work for my truecrypt, and i noticed that it's failing to function because truecrypt needs root permission to mount volumes. i tried running truecrypt from the command line as root and it worked fine. so i after some looking i found this ([http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user](http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user)) guide on how to give normal users the ability to mount - and use - volumes from truecrypt.

but i don't think that it's a guide for ubuntu, as i couldn't find the bashrc file it says to edit, but instead found bash.bashrc    there seem to be further differences between the walk-through and my machine, and i really don't want to mess anything up. 

basically it gives a group permission to run truecrypt as root without having to enter the root password, which seems like a security risk. would it be easier to reinstall truecrypt as a user? or does truecrypt always need root permissions?

running fiesty 7.whatever
The bash.bashrc file (in /etc) is the correct file for Ubuntu.  Alternatively you can put the aliases in the .bashrc file in your home directory.  If you plan to allow multiple users to run truecrypt then the bash.bashrc is your best choice where to make the changes.

---

