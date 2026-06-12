---
title: "cant install ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-06-25
I try to boot off of the cd and it starts loading but then it just says "can't access tty; job control turned off". I burned the cd using k3b. Any help?

---

### Post by ThinkBuntu on 2007-06-25
> **jeff00z28 said:**
> I try to boot off of the cd and it starts loading but then it just says "can't access tty; job control turned off". I burned the cd using k3b. Any help?
Did you check the md5sum of the disk image before burning? Did you verify / checksum the resulting disc also?

---

### Post by miguelangelo1986 on 2007-06-25
Try to burn it with InfraRecorder at 4x speed.

---

### Post by cogadh on 2007-06-25
There is a known problem with the current kernel and certain CD/DVD drives that produces this error and will prevent installation of Feisty. It will also prevent upgrading from Edgy to Feisty. If re-burning the CD at a slower speed or using a different app doesn't work, try using the 6.06 LTS install.

---

### Post by BobCFC on 2007-06-25
Are you using IDE drives by any chance?  I had this same problem using IDE or PATA drives on Core2Duo motherboards because they don't have native IDE.  I have an extra Marvel controller other people have issues with Jmicron.

The way it works for me is pressing F6 for boot options and adding **generic.all_generic_ide=1**

You have to make this permanent after install.  If it works come back I will explain.

---

### Post by jeff00z28 on 2007-06-25
6.06 startsup from the disk but when trying to install it freezes on detecting file systems

---

### Post by jeff00z28 on 2007-06-25
nvm gave it a second try and it worked. hopefully vmware will be as easy to install as it was in 7.04

---

