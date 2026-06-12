---
title: "Fedora 15, Ubuntu 11.04 and GRUB"
date: 2011-05-03
forum: Any Other OS
---

### Post by natibo on 2011-05-03
I have been using linux for a few years and have tried many distros, but am not a computer programmer. For the first time I would like to dual boot Ubuntu 11.04 with Fedora 15. 

First I tried installing Ubuntu 11.04 and then Fedora 15 (Beta) telling the installer to re-size the Ubuntu partition. When Fedora 15 was installed and I restarted I got no option to boot into Ubuntu. Same when i installed Fedora first and then Ubuntu, it booted right into Ubuntu. On both occasions, the software managers said i had grub installed.

I VERY new at this. How do I get my computer to boot into grub so I can have the option of booting into one or more OS's? I searched for a primer on the internet but am still at a loss.

---

### Post by Rifester on 2011-05-03
At the very end of the Fedora installation there is a check list right before you start the install.   One option is something like:  Boot Manager.   The easiest way is to select this then choose DO NOT INSTALL BOOT MANAGER (it will give you a warning-just ignore it and proceed).   The you will GRUB from Ubuntu and will boot into Ubuntu's Plymouth screen.   Once you are back in Ubuntu open a terminal an type:  sudo update-grub.   When you reboot you will be given the option of booting into Fedora or Ubuntu.

---

### Post by natibo on 2011-05-03
Thanks very much

---

### Post by wilee-nilee on 2011-05-03
If your next install doesn't work you can use this tool for yourself or post it and we can get you fixed up.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

I have seen advice to install the bootloader to the OS and not, I just let it go the the mbr and reload grub, I suspect there is more going on with your setup that a simple don't install grub will fix, fedora is grub-legacy. You would have had to add stanzas to the menu.list=grublegacy, if you wanted that to be the bootloader, grub2=Natty has the os-prober which automatically finds the other OS.

If your using two HD's when you install Ubuntu make sure to use the custom install and at the partition change screen is a dropdown or up for where grub goes it should be the HD where Ubuntu is=sda, sdb...etc, no numbers=no partitions.

---

### Post by k357k9 on 2011-05-05
This has always worked for me -- install the distro with grub(1) first and then let the one with grub2 work its magic.

---

### Post by natibo on 2011-05-05
When I installed Fedora 15 first, and then Ubuntu 11.04, Ubuntu did not even recognize that there was another linux distro on my HD.

---

### Post by k357k9 on 2011-05-05
> Ubuntu did not even recognize that there was another linux distro on my HD
Wow!  I have not tried doing this with any *buntu 11.04 yet.  I wonder if they changed something?

---

### Post by wojox on 2011-05-05
> **natibo said:**
> When I installed Fedora 15 first, and then Ubuntu 11.04, Ubuntu did not even recognize that there was another linux distro on my HD.

So you got it all worked out now?

---

### Post by natibo on 2011-05-06
Just installed OpenSuse 11.4 with Gnome 3 until Fedora 15 is launched.

---

### Post by satanselbow on 2011-05-06
The trick is to get Ubuntu on 1st and install grub to the MBR - typically /sda <---- no postfix number just /sda

and then install the the bootloader of the 2nd (and any subsequent) distros into their respective partitions.

ie if Fedora is going in /sda10 install the bootloader to /sda10
    if OpenSuse is going in /sda11 install the bootloader to /sda11

You can then boot back into your "master" Ubuntu install and run:

```
sudo update-grub
```

and all you other distros will be picked up :popcorn:

---

### Post by wolfen69 on 2011-05-07
> **k357k9 said:**
> This has always worked for me -- install the distro with grub(1) first and then let the one with grub2 work its magic.

Exactly. But hopefully all distros will soon use grub2. I havn't had 1 problem with it.

---

### Post by richard.e.morton on 2011-05-14
ok, so I am in a similar position, however before finding this thread I have already done the deed... I had ubuntu 1104 installed and installed fedora15, resizing the ubuntu partition by 9gb to make space for it.

Now I cant get into Ubuntu, how can I recover this?

thanks
R

---

### Post by ManualSparrow on 2011-05-15
So you can boot Fedora, and Fedora is using GRUB Legacy? 

[http://ubuntuforums.org/showthread.php?t=1736692](http://ubuntuforums.org/showthread.php?t=1736692) Posts 5-7 will most likely do the trick, since I did the exact same thing a few weeks ago. Caveat - did you install the Fedora GRUB on the MBR, or on its partition? (If the GRUB menu is present at boot you probably put it on the MBR, which is where you want it).

---

