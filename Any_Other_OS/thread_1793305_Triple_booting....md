---
title: "Triple booting..."
date: 2011-06-29
forum: Any Other OS
---

### Post by Krauser Joestar on 2011-06-29
Hello again Ubuntu community


I have 2 OS on my computer, ubuntu and windows, and i wanted to load another one (arch)


Since my dual boot always start on ubuntu (have to arrow it down to windows) i would like to maintain that status.

I'll use the remaining space of the windows partition and use some for arch linux (should i use logical or primary partitions btw?)

My question is, if i want the boot config to remain the same, which i mean starting with ubuntu, do i just need to install arch normally like i did to ubuntu? Or do i have to specify something on the grub config files?


Thanks in advance

---

### Post by FormatSeize on 2011-06-29
> **Krauser Joestar said:**
> Since my dual boot always start on ubuntu (have to arrow it down to windows) i would like to maintain that status.
By default, the way Grub orders your partitions is in the order that they are installed. So your Linux partition is first on the list because it was the one that you most recently installed. 
 
> **Krauser Joestar said:**
> I'll use the remaining space of the windows partition and use some for arch linux (should i use logical or primary partitions btw?)
You will want to use a primary partition. 
 
> **Krauser Joestar said:**
> My question is, if i want the boot config to remain the same, which i mean starting with ubuntu, do i just need to install arch normally like i did to ubuntu? Or do i have to specify something on the grub config files?

Once you install Arch, it will be the first on the bootloader list. If you want to change that, you will have to follow the instructions [here](http://www.linuxquestions.org/questions/ubuntu-63/how-to-change-grub-boot-order-456724/).

---

### Post by Elfy on 2011-06-29
Not installed Arch - it is possible that you can install it's bootloader to whatever partition you install it to.

Then boot ubuntu and either update it's grub or add arch as a custom entry.

Thread moved to Other OS/Distro Talk.

---

### Post by handy on 2011-06-29
**@Krauser Joestar:** Follow the Beginners' Guide & check the Official Install Guide if required. The Arch documentation rarely misses anything, it certainly won't miss having a guide for how to get through this:

[https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Install_Bootloader](https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Install_Bootloader)

---

### Post by Elfy on 2011-06-29
> **handy said:**
> [https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Install_Bootloader](https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Install_Bootloader)

Before I posted I looked at the Arch Beginners Guide, this was what made me think twice 

> Warning: Make sure to install GRUB on /dev/sdX and not /dev/sdX#! This is a common mistake.

I've not installed arch so don't know if this is just because they assume that arch would be the only or main install or some other reason - hence moving it here and changing the tag to ARCH ;)

Of course if you can install to sdx# without issue then that would be the best thing for the OP I'd imagine.

---

### Post by oldfred on 2011-06-29
It looks like Arch is better than Ubuntu in that it gives a choice of none. But I would still install to the partition /dev/sda# where # is the number of the partition installed into.

> **Install Bootloader**

 Install Bootloader will install a bootloader on your hard drive, either GRUB or [COLOR=Red]NONE in case you have a bootloader already installed[/COLOR] and want to use that one instead. If you choose to install GRUB, the setup script will want you to examine the appropriate configuration file to confirm the proper settings.
 ****

---

### Post by handy on 2011-06-29
**@Krauser Joestar:** [**_The Beginners' Guide_**]("https://wiki.archlinux.org/index.php/Beginners_Guide") is renowned for giving highly effective instructions on how to handle the installation of Arch, it is one of the essential components at least for a first time installation, as Arch IS very different from other distros. 

The Beginners' Guide, includes everything that you need to know for an Arch installation. Including, the very common situation where there are more than one OS being used on the same computer. 

Installing the bootloader is the last thing you do before you reboot & boot into your Arch install for the first time, after which you continue the installation & configuration.

You really should read [**_The Beginners' Guide_**]("https://wiki.archlinux.org/index.php/Beginners_Guide") & familiarise yourself with the process. After which you will be far better informed about what you are getting into & so then be more able to realistically evaluation whether you do actually want to go to the trouble of installing Arch. 

Arch is not for everyone, it is the opposite of Ubuntu, as you will find out if you go ahead & install it.

The installation is actually imho the hardest thing about using Arch. I quite enjoyed it, but I'm like that. :)

---

### Post by Krauser Joestar on 2011-06-29
thanks for all the feedback guys, i'll try it out tomorrow.

---

### Post by Krauser Joestar on 2011-06-30
Well first of all i installed successfully arch on the virtual machine (although gnome 3 isn't working but i suspect it has something to do with the guest additions or maybe the download was corrupt)just to feel the OS.

I have a question though, would be possible to boot it from a different hard drive? Like, booting win7 and ubuntu from a primary partition of the C: drive while i can boot arch from the D: drive, since i have a lot more space there?


Thanks in advance.

---

### Post by oldfred on 2011-06-30
Do you have two drives or two partitions. Windows does not tell you if d: is just sda2 (second partition) or sdb1 (partition on second drive)?

Post this from any Linux or liveCD:
```

sudo fdisk -lu
```

---

### Post by Krauser Joestar on 2011-07-01
> **oldfred said:**
> Do you have two drives or two partitions. Windows does not tell you if d: is just sda2 (second partition) or sdb1 (partition on second drive)?

Post this from any Linux or liveCD:
```

sudo fdisk -lu
```

Eh i went wrong on that. the D: is really just sda2, the second parition but i have an enternal hard disk(sdb).

---

### Post by Krauser Joestar on 2011-07-01
bump and sorry to bother you guys.

---

### Post by handy on 2011-07-01
> **Krauser Joestar said:**
> 
...

I have a question though, would be possible to boot it from a different hard drive? Like, booting win7 and ubuntu from a primary partition of the C: drive while i can boot arch from the D: drive, since i have a lot more space there?


Thanks in advance.

Yes.

---

### Post by Krauser Joestar on 2011-07-01
kk thank you guys.

---

