---
title: "Help needed"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by c.vikramnarayan on 2008-03-28
Hi...
          I just downloaded ubuntu live cd.... i want to install it in my computer....

My configuration is AMD Athlon 32 bit processor...
                               256 mb internal NVIDIA graphics card....
                               768 mb RAM....

I have a problom loading ubuntu.... Every thing gets loaded but when it starts loading the desktop my monitor just blinks.... :confused: Is there any problem with the drivers .... Is it not compatable with my configuration? I have also tried other flavors of linux but in vein, having the simillar problem...Can anyone tell me what i can do to avoid this problem... I am very interested in installing linux... Also i couldn't install any linux flavors in any of 32 bit AMD athlon processor... 

Thanks in advance....
Regards  :)
Vikki

---

### Post by Jimmy Johnson on 2008-03-28
It may help to add vga=normal to the cds boot syntax. Use "F Keys" for help.

---

### Post by bumanie on 2008-03-28
You could try the alternate cd. It often installs when the live cd won't.
You may find the alternate cd installs better. Go here to find the alternate cd download
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by jan quark on 2008-03-28
and check out hermans site for a guide to the alternate installation
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by sailor2001 on 2008-03-28
> **c.vikramnarayan said:**
> Hi...
          I just downloaded ubuntu live cd.... i want to install it in my computer....

My configuration is AMD Athlon 32 bit processor...
                               256 mb internal NVIDIA graphics card....
                               768 mb RAM....

I have a problom loading ubuntu.... Every thing gets loaded but when it starts loading the desktop my monitor just blinks.... :confused: Is there any problem with the drivers .... Is it not compatable with my configuration? I have also tried other flavors of linux but in vein, having the simillar problem...Can anyone tell me what i can do to avoid this problem... I am very interested in installing linux... Also i couldn't install any linux flavors in any of 32 bit AMD athlon processor... 

Thanks in advance....
Regards  :)
Vikki

sounds like you didn't burn an iso disk (image)...you have to boot into ISO disk, not the files that are on the disk.

---

### Post by c.vikramnarayan on 2008-03-28
> **sailor2001 said:**
> sounds like you didn't burn an iso disk (image)...you have to boot into ISO disk, not the files that are on the disk.
actuall i have buned the iso file... i installed ubuntu using the same cd in another system but only in amd athlon 32 bit i get a problem like this...
:-(

---

### Post by Duck2006 on 2008-03-28
Have you tried safe graphics mode?
If it don't work for you then use jan quark way to install ubuntu.

---

### Post by LowSky on 2008-03-28
otherwise try booting into safemode at startup and try to reconfigure your set up

logon then type ```
 sudodpkg-reconfigure xserver-xorg
```


or, like others have said try the alternative install cd

---

### Post by c.vikramnarayan on 2008-03-30
> **LowSky said:**
> otherwise try booting into safemode at startup and try to reconfigure your set up

logon then type ```
 sudodpkg-reconfigure xserver-xorg
```


or, like others have said try the alternative install cd
I just managed to install Hardy version 8.04 using the alternate cd.... But now whenever i enable my nvidia - glx driver and restart it does not work....So i can´t enable any desktop effects... any other alternate for nvidia....?

---

