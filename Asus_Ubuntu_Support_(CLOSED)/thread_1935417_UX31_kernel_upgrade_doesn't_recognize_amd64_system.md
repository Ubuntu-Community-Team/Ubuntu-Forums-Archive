---
title: "UX31 kernel upgrade doesn't recognize amd64 system"
date: 2012-03-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by missfroguk on 2012-03-04
Hi, I have an Asus UX31 and I am trying to go through the many post installation configurations for the functionalities to improve with Ubuntu 11.10. 

I am going through the steps advised in [https://help.ubuntu.com/community/AsusZenbook]("https://help.ubuntu.com/community/AsusZenbook")

but I am having trouble with the kernel upgrade. As advised I downloaded 

```

linux-headers-<version>-<other stuff>_amd64.deb
linux-headers-<version>-<other stuff>_all.deb 
linux-image-<version>-<other stuff>_amd64.deb

```

where the version was 3.2.2. from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

but I am getting the following error messages:

```

Preparing to replace linux-headers-3.2.2-030202 3.2.2-030202.201201252035 (using linux-headers-3.2.2-030202_3.2.2-030202.201201252035_all.deb) ...
Unpacking replacement linux-headers-3.2.2-030202 ...
dpkg: error processing linux-headers-3.2.2-030202-generic_3.2.2-030202.201201252035_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
dpkg: error processing linux-image-3.2.2-030202-generic_3.2.2-030202.201201252035_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Setting up linux-headers-3.2.2-030202 (3.2.2-030202.201201252035) ...
Errors were encountered while processing:
 linux-headers-3.2.2-030202-generic_3.2.2-030202.201201252035_amd64.deb
 linux-image-3.2.2-030202-generic_3.2.2-030202.201201252035_amd64.deb

```

I do know that the system is 64 bits so does anybody know where the problem comes from?

Thanks in advance!

Anybody please...?

---

### Post by matt2053 on 2012-03-05
What is your output of:

```
uname -r
```

?

---

### Post by missfroguk on 2012-03-06
> What is your output of:
```
uname r
```

It is now 
```
3.2.2-030202-generic-pae
```
because I used 
```
dpkg -i --force-architecture *.deb
```
as suggested here: [http://www.linuxquestions.org/questions/debian-26/how-do-you-install-a-custom-kernel-in-debian-897531/]("http://www.linuxquestions.org/questions/debian-26/how-do-you-install-a-custom-kernel-in-debian-897531/")

It was 3.0.0. before I did this. I don't really know if I did what I wanted to do in the end...

Basically all I want is to be able to get a longer battery life with my UX31 following this advice:
> To get the most power efficient system with longer battery life and cooler CPU temperatures, the configuration recommended so far is to disable VT-d in the BIOS and boot kernel 3.2-rc6 or newer with the boot options: ```
i915.i915_enable_rc6=1 i915.semaphores=1 pcie_aspm=force
```

found on [https://help.ubuntu.com/community/AsusZenbook]("https://help.ubuntu.com/community/AsusZenbook")

---

