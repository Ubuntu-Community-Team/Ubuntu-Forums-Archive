---
title: "N56VZ Wubi problem"
date: 2012-08-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Sateg on 2012-08-12
Hello,

I've recently bought an Asus N56VZ laptop and I want to install Ubuntu on it, however I want Windows to be the main OS on this device(I need software like Eagle, AutoCAD or SolidWorks). Because I don't want to mess with the Windows MBR and boot sequence(I want the laptop to boot fast, from my experience switching the default "Asus boot" to grub makes it longer, at least it worked like that on my EEE 1005HA) , I've tried to install Ubuntu 12.04 through Wubi with no success. The problem is in the Windows Boot menu: when I choose Ubuntu, I get this error:

File: \ubuntu\winboot\wubildr.mbr
 Status: 0xc0000098
 Info: The selected entry could not be loaded because the application is missing or corrupt.


The file is there so I am kinda stuck with it.

According to what I've already found out, this laptop uses UEFI to boot and this might mess up wubi setup, but I'm not really good at that kind of stuff ;)

Any help would be highly appreciated

---

### Post by Linuus on 2012-09-07
> **Sateg said:**
> Hello,

I've recently bought an Asus N56VZ laptop and I want to install Ubuntu on it, however I want Windows to be the main OS on this device(I need software like Eagle, AutoCAD or SolidWorks). Because I don't want to mess with the Windows MBR and boot sequence(I want the laptop to boot fast, from my experience switching the default "Asus boot" to grub makes it longer, at least it worked like that on my EEE 1005HA) , I've tried to install Ubuntu 12.04 through Wubi with no success. The problem is in the Windows Boot menu: when I choose Ubuntu, I get this error:

File: \ubuntu\winboot\wubildr.mbr
 Status: 0xc0000098
 Info: The selected entry could not be loaded because the application is missing or corrupt.


The file is there so I am kinda stuck with it.

According to what I've already found out, this laptop uses UEFI to boot and this might mess up wubi setup, but I'm not really good at that kind of stuff ;)

Any help would be highly appreciated

I have the exact same issue with the Asus N56VZ. Did you find any solution?

---

### Post by Sateg on 2012-09-08
> **Linuus said:**
> I have the exact same issue with the Asus N56VZ. Did you find any solution?

Unfortunately not, I'm still waiting for someone with greater knowledge to help me. I had an idea to try and put the wubildr.mbr file on the Windows Boot Partition(it's a hidden system partition), but I haven't had time to try it out(besides I'm not sure how I should access this partition).

---

### Post by sammyboy405 on 2012-09-17
I Have a Similar ASUS Laptop Running UEFI And For the Life of me cant get Wubi to work.

Hopefully someone finds a solution..  I love the ease of Wubi for removal/uninstall.

---

