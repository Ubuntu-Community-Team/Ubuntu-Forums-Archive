---
title: "Distro that doesn't force GRUB install?"
date: 2011-08-15
forum: Any Other OS
---

### Post by 8_Bit on 2011-08-15
I'm trying to install a new distro on a new box. It already has Lubuntu and Win 7, with GRUB properly setup.

[SIZE=4]**Are there any distros that do NOT force you to install a boot loader during installation of the OS?**[/SIZE]

Ubuntu and all of its derivatives all force you to.

If I'm remembering correctly, Fedora doesn't. What others are there?

I don't want to replace the GRUB already on the drive!

---

### Post by aeronutt on 2011-08-15
Yea, I hate that too. Ubuntu used to have an 'advanced' option to allow you not to load grub. I'm pretty sure the gnatty build allows you to not load grub.

[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

I've started using a boot-repair program to reconfigure grub the way I want it after it gets loaded by a new .iso load.

---

### Post by 23dornot23d on 2011-08-15
Slackware 13.37 .... although it comes up with the choice to add LILO ... it also says not to
add any boot info at all .... 

It also gives you another option this is very good in my mind -  to just write the boot loader to a flash drive ...... 
but if you have a system that already set up grub .... 
Then next time you do update grub in that installation it should pick slackware up too .....
Slackware is a little harder to first set up though than Ubuntu or Fedora ...... and from my little play with it .......
 its a learning Distro ..... 

I am learning all the time - now I have it installed ..... simple things seem a lot more complicated now ...... ;)

---

### Post by beew on 2011-08-15
> **8_Bit said:**
> I'm trying to install a new distro on a new box. It already has Lubuntu and Win 7, with GRUB properly setup.

[SIZE=4]**Are there any distros that do NOT force you to install a boot loader during installation of the OS?**[/SIZE]

Ubuntu and all of its derivatives all force you to.

If I'm remembering correctly, Fedora doesn't. What others are there?

I don't want to replace the GRUB already on the drive!

Yes, Fedora doesn't. 

But it is not a problem though, I have a system with several flavours of Ubuntu and other Linuxes, all you need to do is to install the bootloader in the partition instead of the drive. Foe example, you have ubuntu11.04 already installed  (in say sda1)and it controls grub, now you want to install Kubuntu in sda5 and you don't want it to mess up grub already installed, all you need to do is to install its bootloader in sda5 instead of sda.

P.S. I don't know about Slackware but for Ubuntu installing the bootloader back into the live usb as suggested by 23dornot23d  doesn't work.

---

### Post by el_koraco on 2011-08-16
Systems with the Anaconda installer don't force the installation of GRUB. The thing is, GRUB, the troublesome bootloader that it is, is useful for passing boot time parameters to the kernel. So all you need to do is install it into the root partition of the new distro. If you have GRUB2 handling the boot (like in Lubuntu's case, you have to run update-grub and it will autodetect the other system, and chainload into the second GRUB on the root partition.

---

### Post by mips on 2011-08-16
> **8_Bit said:**
> 
Ubuntu and all of its derivatives all force you to.


I'm pretty sure the alternate install cd does not force you to install grub but I could be wrong.

---

### Post by Dlambert on 2011-08-17
Linux Mint Debian

---

### Post by drs305 on 2011-08-17
As a workaround in Ubuntu you can also just plug in a USB thumb drive or point the Grub installation to another non-booting drive. Grub will be installed but as long as your BIOS doesn't point to that drive it won't be used. You can then lock/pin grub-common and grub-pc so they won't update and you can forget it exists.

---

### Post by NightwishFan on 2011-08-17
I think there used to be an 'advanced' option even on the Ubuntu live cd that lets you uncheck installing grub. Or am I wrong/was it changed? Also Debian you can deny installing it or even install lilo from the installer and probably even the live cd.

---

### Post by drs305 on 2011-08-17
> **NightwishFan said:**
> I think there used to be an 'advanced' option even on the Ubuntu live cd that lets you uncheck installing grub. Or am I wrong/was it changed? Also Debian you can deny installing it or even install lilo from the installer and probably even the live cd.

The option *did* exist, but in the most recent Desktop release (Natty) the option to omit Grub 2 was removed from the Desktop CD. You have to select a place to install it. 

That is one of the reasons I mentioned the workaround of installing it to the MBR of a removable drive that won't be looked at by BIOS. Some users were not happy that the option to omit G2 was removed, but it was adopted and is the same in *oneric ocelot*, at least for now.

---

### Post by NightwishFan on 2011-08-17
Thanks for the info. Perhaps I should install the latest Ubuntu dev release in virtualbox to test it from time to time.

---

### Post by 8_Bit on 2011-08-21
I'd just like to confirm what beew said. I have now installed several distros, including Ubuntu and Kubuntu, several times successfuly without overwriting GRUB. I just have to make sure I install bootloader on the same partition as the OS itself.

So if I install a new distro on /dev/sda8, I tell the installer to place the bootloader on /dev/sda8 as well. Works great!

You do have to boot into the first original GRUB distro you installed, and run the following command though.
"sudo update-grub"

This will update the grub listings to reflect any new distros you have installed.

---

### Post by hhh on 2011-08-21
What's wrong with just letting Grub get installed, then boot into the OS you want to control Grub and running (replace sda if appropriate)...```
sudo grub-setup /dev/sda
```
... then running sudo grub-update?

---

### Post by grubu on 2011-08-23
> **drs305 said:**
> As a workaround in Ubuntu you can also just plug in a USB thumb drive or point the Grub installation to another non-booting drive. Grub will be installed but as long as your BIOS doesn't point to that drive it won't be used. You can then lock/pin grub-common and grub-pc so they won't update and you can forget it exists.

The USB plug-idea is a very good solution, what would happen if grub2 is already installed on sda and during a new installation maybe grub is installed onto an empty sda8 partition?

---

### Post by IWantFroyo on 2011-08-23
Arch used to be like that. After the update, you have to select something, though.

---

### Post by oldfred on 2011-08-23
You have to be careful to not let grub updates reinstall to the wrong place also.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can install grub2's boot loader anywhere, but not to a windows NTFS partition which has to have a NTFS signature or boot code. Linux partitions are generally empty or may have left over data if partition was moved for any reason.

---

### Post by doorknob60 on 2011-08-24
> **IWantFroyo said:**
> Arch used to be like that. After the update, you have to select something, though.
Really? I'm 99% sure you don't have to install GRUB, I just recently installed it. If you don't want to install it, on the main menu thing where it shows like the 7 steps or whatever, just skip over the step of install bootloader and just go to finish, nobody said you have to use all the steps listed :)

Unless you're talking about the 2011.08.19 ISO, in which case I haven't used that one yet, but I'd assume it works the same way.

---

### Post by mips on 2011-08-24
> **doorknob60 said:**
> Really? I'm 99% sure you don't have to install GRUB, I just recently installed it. If you don't want to install it, on the main menu thing where it shows like the 7 steps or whatever, just skip over the step of install bootloader and just go to finish, nobody said you have to use all the steps listed :)

Unless you're talking about the 2011.08.19 ISO, in which case I haven't used that one yet, but I'd assume it works the same way.

I recently used the 2011.06.10 releng ISO and that definitely did not force you to install grub, it was a optional step you could leave out.

I simply can't see the arch devs forcing you to install grub, it would go against everything they stand for & cause a fair amount of outrage.

---

### Post by aeronutt on 2011-08-24
> **mips said:**
> I'm pretty sure the alternate install cd does not force you to install grub but I could be wrong.

This would be good, can anyone confirm?

---

