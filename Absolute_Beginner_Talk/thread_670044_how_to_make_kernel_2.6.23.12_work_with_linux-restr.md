---
title: "how to make kernel 2.6.23.12 work with linux-restricted-modules 2.6.22.14.21"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-17
After compiling kernel to 2.6.23.12 following the instruction of [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) , My system runs into low graphic mode and can not access to restricted drivers manager. It keep saying that I need to install 
linux-restricted-modules-2.6.23.12 to use the program. But the problem is the latest version is 2.6.22-14.. there is not 2.6.23.12..!!

I guess it's because my previous kernel was 2.6.22-14-generic thus it wouldn't work with new kernel because of different version..    It seems to me that the version of kernel and the version of restricted drivers manager is normally same. 

What can I do to fix this? Make ubuntu access to the manager??

This has been bothering me for few days. Help me plz..!

---

### Post by luisromangz on 2008-01-17
Well the restricted manager works using the package system, and as you have installed a newer kernel from sources you implicitely have decided to do things manually so resctricted manager won't work. You know, it works downloading packages, and there are no gutsy packages for the kernel you have installed.

If you want to install your video card drivers etc, you will have to do so manually too, downloading the driver from the vendor's website, and running its installer.

---

