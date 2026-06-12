---
title: "basic Linux development tools?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by jadoo_iii on 2007-09-19
I downloaded the ntfs-3g-1.913 stable release driver for ntfs file system and when i read its readme file i discover that its pre-requisite is to have first the basic Linux development tools and the full FUSE package installed . How can i know when my system had already basic Linux development tools installed and where i can type the codes for installing this particular driver? Any help i kindly appreciate. Thanks.

---

### Post by qamelian on 2007-09-19
Which release of Ubuntu are you using? If you are using Feisty (7.04), you don't need to download anything as ntfs-3g and all it's dependencies are available through the official Ubuntu software repositories.

---

### Post by olejorgen on 2007-09-19
I guess it's a source release? (ie. it contains source code)

If it is you will need at least **build-essensial** and probably **libfuse-dev** and **libfuse2**

Then I'm guessing the build instructions are telling you to run **./configure** ?

Do this and paste the output

EDIT: But if you don't have a particular reason to use the latest version, you should just install in through apt

---

### Post by Maestro23 on 2007-09-19
If you have the source tarball, read the following:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.gz.22_.28Tar.2FGZip.29_Archives](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.gz.22_.28Tar.2FGZip.29_Archives)

---

### Post by jadoo_iii on 2007-09-19
> **qamelian said:**
> Which release of Ubuntu are you using? If you are using Feisty (7.04), you don't need to download anything as ntfs-3g and all it's dependencies are available through the official Ubuntu software repositories.

yes, i'm using Feisty 7.04 release but all my ntfs drives are still read-only disks .

---

### Post by Maestro23 on 2007-09-19
> **jadoo_iii said:**
> yes, i'm using Feisty 7.04 release but all my ntfs drives are still read-only disks .

Did you install "ntfs-config" (GUI Frontend) also?

> sudo apt-get install ntfs-config

Will put an entry in your Apps menu.  Check the box for write capabilities on the NTFS partition.

---

