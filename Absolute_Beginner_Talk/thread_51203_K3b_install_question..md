---
title: "K3b install question."
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by aum11 on 2005-07-22
Have just installed k3b in order to backup to dvdrw.

My newby problem is that K3b hasn't shown up anywhere in the menu.  

Where would it be, and how to get it into the menu?

I already have installed smeg.

Thanks,

---

### Post by jasmuz on 2005-07-22
alt+f2 : type k3b and click run.

Adding to the menu, well that is a whole other issue.

---

### Post by Nequeo on 2005-07-22
[QUOTE=aum11]Have just installed k3b in order to backup to dvdrw.

My newby problem is that K3b hasn't shown up anywhere in the menu.  

Where would it be, and how to get it into the menu?

I already have installed smeg.

Thanks,[/QUOTE]
 In the case of K3B try typing this on the command line:

```

sudo mv /usr/share/applnk/Multimedia/k3b.desktop /usr/share/applications/

```

K3B comes with a menu shortcut, but being a KDE app it puts the file in the wrong place. For other applications, the way I do it is by typing
```

 'dpkg -L packagename | grep desktop' 

```
That will find any existing menu items in the package. For Ubuntu, those files need to be put in /usr/share/applications. If they're in the correct format, they'll just show up. If they're not, you may need to edit the category, or similar.

For applications that don't have pre-existing menu items, try just typing the program name on the command line. If the program runs, then you don't need to worry about where it is, the same trick will work for the menu shortcut. (Though it's probably in /usr/bin). 

If you still need to know where a package has put it's files, just type ```

dpkg -L packagename
``` on the command line, or search up the package in Synaptic and look under Properties --> Installed Files.

Cheers!

---

### Post by poofyhairguy on 2005-07-22
This is what I once wrote on the topic:

[https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29](https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29)

---

### Post by aum11 on 2005-07-22
Thanks Jasmuz.
that worked fine.

Where is  the K3b application held so that I can browse to it and incorporate it into smeg?  And what extension is it?
Thanks. :)

---

### Post by aum11 on 2005-07-22
Thanks for your inputs.

Poofyhairguy,
thanks for the wiki.

A question for You.  The following is the chipset:

IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)

What do I enter for the module via82cxxx ?
is it via82c801?

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=aum11]Thanks for your inputs.

Poofyhairguy,
thanks for the wiki.

A question for You.  The following is the chipset:

IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)

What do I enter for the module via82cxxx ?
is it via82c801?[/QUOTE]


try it:

> sudo modprobe via82c801

---

### Post by aum11 on 2005-07-23
I tried it and got:

$  sudo modprobe via82c801
Password:
FATAL: Module via82c801 not found.

Excuse my ignorance but what does this mean?

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=aum11]I tried it and got:

$  sudo modprobe via82c801
Password:
FATAL: Module via82c801 not found.

Excuse my ignorance but what does this mean?[/QUOTE]

That you don't have tha sort of motherboard. I have trouble getting dma to work on my Viao...so don't take it personally.

---

