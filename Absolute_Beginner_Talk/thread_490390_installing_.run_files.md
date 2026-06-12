---
title: "installing .run files"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ksn linux on 2007-07-02
I know that the forum is flooded with questions about how to install software, however it was hard to find a guide that isn't dependent on using add/remove or synaptic package manager.  I have recently downloaded the latest ati drivers for my radeon x800 (file name below)

ati-driver-installer-8.38.6-x86.x86_64.run

and i am sure that drivers are not in the add/remove or the synaptic package manager so it seems I need to use the terminal.  If somebody could post a guide on how to install this file, or any .run file for that matter it would be most appreciated.

As long as I am asking how to install software i might as well add I have gotten Google Earth, which is a .bin file.  If the installation is any different for .bin files could you post a guide on that as well.

---

### Post by eternalsword on 2007-07-02
you probably don't want to do it that way.  that will compile the driver, and you would need to redo it every time you install a newer kernel version.  you should be able to install the xorg-driver-fglrx package from synaptic or via terminal ```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by reset3x on 2007-07-02
I suggest that you go here and download Envy... It will save you some headaches.. 

[http://albertomilone.com/](http://albertomilone.com/)

---

### Post by nphx on 2007-07-02
If you would like to install from the ATI.com here is the link. In the tutorial scroll down to the section where it says "Install from ati.com (latest version of drivers)."

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by dreadlord_chris on 2007-07-02
> **ksn linux said:**
> I know that the forum is flooded with questions about how to install software, however it was hard to find a guide that isn't dependent on using add/remove or synaptic package manager.  I have recently downloaded the latest ati drivers for my radeon x800 (file name below)

ati-driver-installer-8.38.6-x86.x86_64.run

and i am sure that drivers are not in the add/remove or the synaptic package manager so it seems I need to use the terminal.  If somebody could post a guide on how to install this file, or any .run file for that matter it would be most appreciated.

I'd be willing to bet that right next to the download link for those drivers there was a link to how to install them....
well, here ya go:
```

cd /to/folder/where/run/file/is
sudo sh ati-driver-installer-8.38.6-x86.x86_64.run

```

as for a general instalation guide?
you mean like this one - [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/) ?

---

### Post by ksn linux on 2007-07-02
I entered the command that eternalsword gave me into the terminal and it installed xorg-driver-fglrx, but I am not sure where it installed to and what xorg does, could somebody explain.

---

### Post by ksn linux on 2007-07-02
thanks for all the help

---

