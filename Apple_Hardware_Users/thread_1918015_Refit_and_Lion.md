---
title: "Refit and Lion"
date: 2012-01-31
forum: Apple Hardware Users
---

### Post by LinuxBill on 2012-01-31
With the lion release it allows you to be able to hold alt at boot and search for bootable media. Does this render refit useless for users that unfortunately are now using lion. I replaced my macbook and now have an 2011 gen Macbook which came with Lion *Sigh* .Just wondered if refit will even be needed on Lion? Anyone know if they are planning to release a Lion version of Refit?

Thanks
William

---

### Post by cyberdork33 on 2012-01-31
> **LinuxBill said:**
> With the lion release it allows you to be able to hold alt at boot and search for bootable media. Does this render refit useless for users that unfortunately are now using lion. I replaced my macbook and now have an 2011 gen Macbook which came with Lion *Sigh* .Just wondered if refit will even be needed on Lion? Anyone know if they are planning to release a Lion version of Refit?

Thanks
William

OS X has done that for a very long time, it is not a new feature of Lion.

---

### Post by Lars Noodén on 2012-01-31
I've been using rEFIt with Lion and haven't noticed any change in that regard.

---

### Post by LinuxBill on 2012-01-31
Ah right never knew this..but then why use refit if you can already boot into whatever you need? 

Thanks
William

---

### Post by kwolf22 on 2012-05-26
You don't need rEFIt.  From the rEFIt websites's [Myths & Facts About Intel Macs:]("http://refit.sourceforge.net/myths/")

> **Myth: You need rEFIt to install/boot Linux**

You don’t. The firmware’s built-in boot volume chooser (hold Option to activate it) will recognize Linux boot CDs as well as bootable hard disks and let you boot them. (They may be labeled “Windows”, though.) For triple-booting you’ll get only one item in the built-in chooser, but you can use GRUB, LILO, or NTLDR to act as a second-level menu to choose between Windows and Linux. The gptsync tool can be compiled to run on Linux.

Of course rEFIt makes it easier. For example, it will give you a single menu even for triple-boot setups. 

---

