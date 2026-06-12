---
title: "Help Uninstalling Ubuntu"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by FileMaster on 2005-10-10
Hi, I've tried Ubuntu for a while and would like to remove it. What is the correct way to uninstall it from:

1. A PC with Windows XP on it (dual boot)

2. A PC with just Ubuntu on it

Thanks,
FileMaster

---

### Post by erikpiper on 2005-10-10
Are you sure? I think it is the best OS ever- but I am a member here :) Mind if I ask why?

For the PC with only ubuntu- just install whatever over it. Repartitioning will wipe it out. (Just install as if the PC was empty)

For the pc with windows: I don't know how to clear the MBR, but a fresh install of windows would work- If you want the headaches. :p I am looking for the answer now.

---

### Post by erikpiper on 2005-10-10
Ok got this- [http://info.ccone.at/INFO/mandrake/9.0/en/ch01s26.html](http://info.ccone.at/INFO/mandrake/9.0/en/ch01s26.html) 
from google.

Boot into linux using the live cd- and boot with the -noswap option so you can remove the swap partition.

Using gparted, remove all linux partitions. If there is no gparted, install it using synaptic. (Yes it will work with the live cd)

Then, boot into DOS (Floppy? I cant help you there) and run fdisk /mbr

---

### Post by FileMaster on 2005-10-10
Hi erikpiper,

Thanks for the advise.

The reason is that I would like to try a different distro that may be more suitable for me. Probably something with hwsetup, KDE, JRE pre-installed, and a few other different applications and approaches. It's nothing against Ubuntu, just looking at other options while I'm still in experimenting mode with Linux.

I'm interested in keeping the existing Windows installation and parition so not looking to re-install Windows. Just to remove Linux and possibly claim back the space.

FileMaster


[QUOTE=erikpiper]Are you sure? I think it is the best OS ever- but I am a member here :) Mind if I ask why?

For the PC with only ubuntu- just install whatever over it. Repartitioning will wipe it out. (Just install as if the PC was empty)

For the pc with windows: I don't know how to clear the MBR, but a fresh install of windows would work- If you want the headaches. :p I am looking for the answer now.[/QUOTE]

---

### Post by Perfect Storm on 2005-10-10
you could try Kubuntu (kde version of ubuntu), to install JRE it's quite simple: [http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

---

### Post by Krissy on 2005-10-10
Hello, a newbie here. I've got same problem......

[QUOTE=erikpiper]For the PC with only ubuntu- just install whatever over it. Repartitioning will wipe it out. (Just install as if the PC was empty).[/QUOTE]

And if this is not workin? It gives me: "Setup cannot install win98...a disk error was detected while writing a new boot record to  your first hard disk."

---

### Post by Efwis on 2005-10-10
[QUOTE=Krissy]
And if this is not workin? It gives me: "Setup cannot install win98...a disk error was detected while writing a new boot record to  your first hard disk."[/QUOTE]


since you want to install Windows9x/ME, you will need to use fdisk and repartition the harddrive.

put in a boot disk, not the Windows 98 disk, if you dont'  have one you can get one to put on floppy from [http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm"), make sure you get the correct boot disk if you need it (i.e. windows98 OEM, Windows 98 custom, Windows 98 SE etc..).

put the disk in and boot your machine, when the C: prompt comes up type in Fdisk then repartion and reformat the hdd. I'm not sure if Gparted will do the same thing or not especially since Windows 9x/ME needs the Dos partition.

---

### Post by erikpiper on 2005-10-10
Oh...  W98- That is different :)

Advice with other linuxes- stay far far away from RPM. Dependencies are horrible. Use debian based distros, or gentoo, but stay away from rpm :p  

Also, Mepis is the buggiest and worst linux I have ever used 

Ubuntu is the all around best in my opinion, so dont forget about it :)

---

### Post by FileMaster on 2005-10-10
Yes I agree Debian is a better choice, especially for newbies.

AI - I tried Kubuntu, other than the KDE it still has the other issues. I tried other live CD's these couple of days and had better luck with them. Probably due to the hwsetup from Knoppix and better choices (for me) with other applications. I know most of these things can be installed onto Ubuntu (or any distro) it's just that I would rather start with them built instead of replace things one by one. In no means trying to belittle the good efforts of Ubuntu, just that no one distro fits all.

Btw, Partition Magic doesn't run anymore (at all) giving errors since the installation of Kubuntu. I wanted to remove the linux parition from within WinXP with PM as a safer option but it looks like that's not possible. I used fdisk /mbr in the past and these things are as reliable as a French car.

Any other suggestions for clearing up a Ubuntu (or any other linux distro) from a dual boot system WITHOUT harming the WinXP one? What would happen if I tried installing another linux on top of the Ubuntu?

Appreciate your advice.
FileMaster
 

[QUOTE=erikpiper]Oh...  W98- That is different :)

Advice with other linuxes- stay far far away from RPM. Dependencies are horrible. Use debian based distros, or gentoo, but stay away from rpm :p  

Also, Mepis is the buggiest and worst linux I have ever used 

Ubuntu is the all around best in my opinion, so dont forget about it :)[/QUOTE]

---

### Post by Wolki on 2005-10-10
[QUOTE=FileMaster]Any other suggestions for clearing up a Ubuntu (or any other linux distro) from a dual boot system WITHOUT harming the WinXP one? What would happen if I tried installing another linux on top of the Ubuntu?[/QUOTE]

To remove ubuntu, just restore the original windows boot loader, then delete the linux and swap partition. To restore the boot loader, boot from the windows cd, there should be an option under recovery things (at least it was on my parents' win2k box).

[edit] look here for detailed WinXP instructions: [http://ubuntuforums.org/showpost.php?p=399221&postcount=3](http://ubuntuforums.org/showpost.php?p=399221&postcount=3)

If you want  to install another linux, just install that one over ubuntu. make sure you use the same partitions, then everything should work without data loss.

---

