---
title: "Installing Ubuntu On Vmware"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by nicluc on 2005-09-22
I can install hoary hedgehog fine in vmware workstation but breezy always fails at the base system installation screen....initrdtools.....Ive redownloaded breezy, created a new bootable cd disk.....even changed hard drives to host the virtual hdd. Keeps failing at base install....not exactly sam error.....Any ideals...thx

---

### Post by kassetra on 2005-09-22
[QUOTE=nicluc]I can install hoary hedgehog fine in vmware workstation but breezy always fails at the base system installation screen....initrdtools.....Ive redownloaded breezy, created a new bootable cd disk.....even changed hard drives to host the virtual hdd. Keeps failing at base install....not exactly sam error.....Any ideals...thx[/QUOTE]

Since Breezy hasn't been released yet - it's possible that the code that would make setting up a system on vmware work isn't finished yet.

Let me check around a bit.

---

### Post by jreymol on 2005-11-07
Same problem here.

VmWare 5.5 on Windows XP. Cannot install Ubuntu 5.10.

Ubuntu 5.4 is working fine.

---

### Post by lanceh on 2005-11-07
i've installed ubuntu, 5.10 and 5.10RC, on both VMWare 5.0 and VMWare 5.5RC. no problems at all during installation except for picking the proper resolution. do yourself a favor and select the resolution you're running your host machine at or lower.

since ubuntu isn't fully supported in vmware the installation of vmware tools is a bit tricky. after a day or so of poking around i found this install guide and it finally worked. 

[http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

---

### Post by jreymol on 2005-11-08
Hi, lanceh!

I think my problem (and nicluc's) isn't about resolution. I got this message during instalation:

Install the base system
The debootstrap program exited with an error (return value 1).
Check /target/var/log/bootstrap.log for the details.

I click continue and then I get:

Install the base system
The base system instalation into  /target/ failed.
Check /target/var/log/bootstrap.log for the details.

When I get my hands into /target/var/log I find it empty

---

### Post by jreymol on 2005-11-08
I have just re-downloaded ubuntu 5.10 cd image and now it works.

Maybe I just had a download error. But I had try with both CD image and DVD image with the same error. 

Now it works and I'm happy :)

---

