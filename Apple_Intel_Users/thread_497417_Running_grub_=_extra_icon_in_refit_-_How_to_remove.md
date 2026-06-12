---
title: "Running grub = extra icon in refit - How to remove?"
date: 2007-07-10
forum: Apple Intel Users
---

### Post by grim1234 on 2007-07-10
After building a kernel and running these commands :

Grub, 

root (hd0,3)

setup (hd0,3)


I now have an extra linux icon in refit. Does anyone know how I can remove this?

---

### Post by cyberdork33 on 2007-07-10
Most likely, you have grub installed in the MBR and in the Ubuntu partition now. You will need to "uninstall" grub from the MBR.

[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12)

If you are triple booting, then using the fixmbr method from the WinXP cd should be good as that will allow you to boot windows directly from refit without grub getting involved.
[http://ubuntuforums.org/showthread.php?t=398869](http://ubuntuforums.org/showthread.php?t=398869)

---

### Post by ronocdh on 2007-07-10
> **cyberdork33 said:**
> If you are triple booting, then using the fixmbr method from the WinXP cd should be good as that will allow you to boot windows directly from refit without grub getting involved.
[http://ubuntuforums.org/showthread.php?t=398869](http://ubuntuforums.org/showthread.php?t=398869)
It was my understanding that this process would overwrite the GRUB information on the MBR and thus make Ubuntu impossible to boot. Are you saying that one could do **fixmbr** and then basically have the same functionality with GRUB as one would with ELILO, i.e. choosing an icon on the rEFIt screen takes the user directly to that operating system?

I am currently triple booting, and both WinXP and Ubuntu icons take me to the GRUB screen, where I must select again. Given the firmware issue where the keyboard often doesn't respond, this is quite a problem on the rare occasion I need to get into Windows.

---

### Post by cyberdork33 on 2007-07-10
no, I am saying that grub was installed to the partition this time (which is the change I is wanted) instead of the MBR. This is actually fine. but now grub is installed in the MBR and the root partition. rEFIt sees this and has an option for both. Linux has to have a bootloader (grub or lilo) to load the kernel, so no you have to use one (somewhere), but you don't have to use grub for Windows, refit should be able to boot it like bootcamp does. It won't hurt to try, if it causes you to be unable to boot Ubuntu, then you just have to use the live cd to reinstall it to the MBR again (as the default installer does).

This may all be for naught though since apparently grim installed to the wrong partition anyway.

See the Grub Documentation for more details on installing to different partitions.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

Specifically:
> 
Once you've set the root device correctly, run the command setup (see [setup]("http://www.gnu.org/software/grub/manual/html_node/setup.html#setup")):  
     ```
grub> setup (hd0)
```     This command will install the GRUB boot loader on the Master Boot Record (MBR) of the first drive. If you want to put GRUB into the boot sector of a partition instead of putting it in the MBR, specify the partition into which you want to install GRUB:  
     ```
grub> setup (hd0,0)
```

---

