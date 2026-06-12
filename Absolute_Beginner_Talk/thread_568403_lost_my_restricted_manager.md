---
title: "lost my restricted manager"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by mookie_jones on 2007-10-05
i ran an update and when i rebooted it told me it couldnt find the video card. I told it to continue with default but i rebooted to find the restricted manager was gone.. I got it back but when i try to tell it to start i get

 You need to install the package

  linux-restricted-modules-2.6.22-13-generic

for this program to work.


help please, im only a day into using ubuntu but i dont wanna go back to windows

---

### Post by kevdog on 2007-10-05
So type at the command line

sudo aptitude install linux-restricted-modules-2.6.22-13-generic

---

### Post by mookie_jones on 2007-10-05
thanks but i tried that


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for linux-restricted-modules-2.6.22-13-generic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by nick_h on 2007-10-05
Try installing linux-restricted-modules-2.6.22 or linux-restricted-modules-generic

---

### Post by mookie_jones on 2007-10-05
got more feedback this time



mookie@mookie-ubuntu:~$ sudo aptitude install linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-generic 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.3kB of archives. After unpacking 53.2kB will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.22-13-generic which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

---

### Post by rsidle on 2007-10-05
Same issue here, I think it has to do with a new kernel update. They've updated the kernel to -13 from -12 and have yet to upgrade the restricted modules. I'm using the restricted manager for the nvidia driver, so that's a real bummer. I was able to get xserver started using the NV driver (the open source one) at 1024x768. It's workable for the time being.

---

### Post by RomeReactor on 2007-10-05
Hi. The package seems to not have arrived at the repositories yet. Just wait until it hits them, or if you already did the other updates, boot using a previous kernel.

---

### Post by strigare on 2007-10-05
> **RomeReactor said:**
> Hi. The package seems to not have arrived at the repositories yet. Just wait until it hits them, or if you already did the other updates, boot using a previous kernel.

Yes that's the best solution, I lost all my screen configuration and had to manually change the xorg.conf so I'm staying away of 2.6.22-13 until the restricted modules arrive to the repos.

---

### Post by Hans5849 on 2007-10-05
Whats the name of the previous kernel so i can load into it

---

### Post by RomeReactor on 2007-10-05
When you turn your PC on, and grub is about to load, a message appears telling you that you have three seconds to press ESC to change the kernel it will boot; so press ESC, press the DOWN arrow twice to select the **linux-image-2.6.22-12-generic**.

---

### Post by strigare on 2007-10-05
> **Hans5849 said:**
> Whats the name of the previous kernel so i can load into it

2.6.22-12

---

### Post by kidalabama on 2007-10-06
when will create linux-restricted-modules-2.6.22-13-generic ?
:confused:

---

### Post by RomeReactor on 2007-10-06
Hi. We'll probably need to wait a couple of days until the package is available in the repositories. Don't upgrade yet, or if you already have, boot using the 2.6.22-12 kernel.

**EDIT**: restricted-modules-2.6.22-13 now online.

---

### Post by Grompeldepompeltje on 2007-10-06
I experienced the same problem.. solved it by first updating aptitude:
sudo aptitude update

then installing:
sudo aptitude install linux-restricted-modules-2.6.22-13-generic 

after which I could re-enable the restricted ATI driver.

---

### Post by bubill on 2007-10-06
you must use ubuntu office sources .and then sudo apt-get update source and dist-upgrade ,
i got the same problem. :)

---

