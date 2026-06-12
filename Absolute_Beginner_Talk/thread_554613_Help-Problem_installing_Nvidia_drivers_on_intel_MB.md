---
title: "Help-Problem installing Nvidia drivers on intel MBP"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by N3r0H on 2007-09-19
NVIDIA GeForce 8600M GT

I'm trying to install NVidia drivers for my MBP. I'm running Ubuntu Ultimate inside VMware Fusion. I downloaded 100.14.19 but get error that I can't open it. I'm using the command
   sh NVIDIA-Linux-x86-100.14.19-pkg1.run  to install it. But I really have no idea what to do as this is my first day on linux.

---

### Post by w4ett on 2007-09-20
I recommend the use of  an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type: 


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by ayenack on 2007-09-20
He's using a VM can he install and load graphic drivers in that? Don't think he can the VM will use it's own generic driver I think for all video cards.

---

### Post by skyjacker on 2007-09-20
> **w4ett said:**
> I recommend the use of  an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type: 


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck
Just installed Envy Tuesday.  I also have Nvidia and now everything is ok again:). works great

---

