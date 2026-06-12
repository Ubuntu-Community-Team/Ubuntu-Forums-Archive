---
title: "Riptide/conexant modem help"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by whythehellcantilogon on 2005-09-02
Hi, I recenty installed ubuntu on my computer and I am having many problems installing my modem. 

I ran scanModem and the line identifying my modem read

Class 0780: 127a:4321 Communication controller: Rockwell Interational Riptide      HCF 56k PCI Modem
Sub System 1235:4321 Risq Modular Systems, Inc. Hewlett Packard DF
0000:00:0b.1 0780: 127a:4321

I don't currently have any way to get the entire log posted, but if you need it I will type it out...

I found drivers at linuxant.com/drivers

It says that I need to install both the riptide and the HCF drivers.

Under the riptide download page ([http://www.linuxant.com/drivers/riptide/downloads.php](http://www.linuxant.com/drivers/riptide/downloads.php))

it says to use it I have to kernel-source and gcc C compiler must be installed. This is my first problem. I dont understand where to get these or what to do with them. any help would be greatly appreciated.

Erik

---

### Post by thoerner on 2006-02-07
open a terminal and type:

sudo apt-get install kernel-source
sudo apt-get install gcc
sudo apt-get install gcc-3.4

this will install the packages required

---

### Post by az on 2006-02-07
You would need to install the linux-headers package, since you do not need to recompile the whole kernel, but just compile a module for the one you are running.  Use the linux-headers package for that.

However, the riptide driver does not work for the 2.6 kernel AFAIK.  Conexant don't care about linux users so they have not released their driver as open source, nor worked on it since 2001.

They screwed you.

---

### Post by darthchaosofrspw on 2006-06-04
[QUOTE=azz]You would need to install the linux-headers package, since you do not need to recompile the whole kernel, but just compile a module for the one you are running.  Use the linux-headers package for that.

However, the riptide driver does not work for the 2.6 kernel AFAIK.  Conexant don't care about linux users so they have not released their driver as open source, nor worked on it since 2001.

They screwed you.[/QUOTE]

I think somebody needs to reverse-engineer the Riptide driver source code and make a new Riptide driver compatible with 2.6+ Linux kernels...maybe even make a .deb Debian package of it. I installed Breezy Badger on my desktop yesterday...I'm downloading Dapper Drake right now.

---

### Post by Matchless on 2006-06-06
[QUOTE=whythehellcantilogon]Hi, I recenty installed ubuntu on my computer and I am having many problems installing my modem. 

I ran scanModem and the line identifying my modem read

Class 0780: 127a:4321 Communication controller: Rockwell Interational Riptide      HCF 56k PCI Modem
Sub System 1235:4321 Risq Modular Systems, Inc. Hewlett Packard DF
0000:00:0b.1 0780: 127a:4321

I don't currently have any way to get the entire log posted, but if you need it I will type it out...

I found drivers at linuxant.com/drivers

It says that I need to install both the riptide and the HCF drivers.

Under the riptide download page ([http://www.linuxant.com/drivers/riptide/downloads.php](http://www.linuxant.com/drivers/riptide/downloads.php))

it says to use it I have to kernel-source and gcc C compiler must be installed. This is my first problem. I dont understand where to get these or what to do with them. any help would be greatly appreciated.

Erik[/QUOTE]
 It seems as if 127a:4321 could be your device id. If you go to my post at [http://www.ubuntuforums.org/showthread.php?t=189009&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=189009&highlight=conexant) you will find a howto that may help you, but is for HSF. The problem is that I have only tested an HSF modem and not the HCF ones. If you get it to work with [http://www.linuxant.com/drivers/riptide/archive/riptide-0.6lnxtbeta03122800/riptide-0.6lnxtbeta03122800.tar.gz?PHPSESSID=c6e458d24d412f7a53caca371c0f6f4b](http://www.linuxant.com/drivers/riptide/archive/riptide-0.6lnxtbeta03122800/riptide-0.6lnxtbeta03122800.tar.gz?PHPSESSID=c6e458d24d412f7a53caca371c0f6f4b) then I would be glad if you could let me have the process to add to the howto., but as Azz says it does not work on kernel 2.6, so it may be as he says!

---

### Post by darthchaosofrspw on 2006-10-10
> **Matchless said:**
> It seems as if 127a:4321 could be your device id. If you go to my post at [http://www.ubuntuforums.org/showthread.php?t=189009&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=189009&highlight=conexant) you will find a howto that may help you, but is for HSF. The problem is that I have only tested an HSF modem and not the HCF ones. If you get it to work with [http://www.linuxant.com/drivers/riptide/archive/riptide-0.6lnxtbeta03122800/riptide-0.6lnxtbeta03122800.tar.gz?PHPSESSID=c6e458d24d412f7a53caca371c0f6f4b](http://www.linuxant.com/drivers/riptide/archive/riptide-0.6lnxtbeta03122800/riptide-0.6lnxtbeta03122800.tar.gz?PHPSESSID=c6e458d24d412f7a53caca371c0f6f4b) then I would be glad if you could let me have the process to add to the howto., but as Azz says it does not work on kernel 2.6, so it may be as he says!

With Riptide HSF modems, you can use the modem without installing the Riptide drivers, but for Riptide HCF modems, the modem will not work until you install the Riptide drivers. I learned that from personal experience when I had Xandros 2.01 OCE and Linspire 4.5.603 installed on my old desktop that had a Riptide HCF modem.

---

