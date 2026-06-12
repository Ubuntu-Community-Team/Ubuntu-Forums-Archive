---
title: "verify installed packages"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by civic_si on 2007-11-07
I want to verify all my installed files against all installed deb packages, just like the "rpm -Va" command in rpm-based distros.
 
is there an equivalent command like this in Ubuntu?

---

### Post by rsambuca on 2007-11-07
For those of us that haven't used red hat, perhaps you can explain what 'verify' means, and then we can give you an equivalent.

---

### Post by Maestro23 on 2007-11-07
> **civic_si said:**
> I want to verify all my installed files against all installed deb packages, just like the "rpm -Va" command in rpm-based distros.
 
is there an equivalent command like this in Ubuntu?

Have you dug around in the man page for dpkg?

---

### Post by smartalecks on 2007-11-07
debsums I think is what you want

---

### Post by Maestro23 on 2007-11-07
> **smartalecks said:**
> debsums I think is what you want

Might have to install it first.

> sudo apt-get install debsums

From the Syanptic Description:

> Verify installed package files against MD5 checksums.
debsums can verify the integrity of installed package files against
MD5 checksums installed by the package, or generated from a .deb
archive.

---

### Post by civic_si on 2007-11-08
I installed debsums last night and ran some stuff but it didnt fix my problem thanks for the help.

---

