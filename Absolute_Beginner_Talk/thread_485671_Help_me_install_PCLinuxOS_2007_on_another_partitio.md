---
title: "Help me install PCLinuxOS 2007 on another partition"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-06-27
I have some free hard drive space to which I want to install PCLinuxOS 2007 on and I want to make sure that the install will be very clean and won't cause any problem and that I can easily remove the PCLinuxOS partition without problems.

When I have installed PCLinuxOS before and decided to uninstall it, I experienced partition or file system problems and I guess it is because PCLinuxOS uses LILO instead of GRUB.

I have an Ubuntu Partition, a Home Partition, a swap partition, and some free space. I intend to create a partition on that free space and install PCLinuxOS on it.

What should I do with the install if I am planning to uninstall PCLinuxOS eventually?

Should I use the same home partition that my Ubuntu install uses?

Can I just use the GRUB boot loader that I am already using with my Ubuntu install?

Will there be problems if I format my Ubuntu's swap partition when I am installing PCLinuxOS 2007?

---

### Post by benson444 on 2007-06-27
I think the best way to multi-boot various Linux distros is chainloading. When you come to install the boot-loader, leave the one Ubuntu installed on the MBR and install the new distro's loader to the partition you are installing that distro to.

So install PCLinuxOS to, say, hda4 and install PCLinuxOS's boot-loader to hda4. Then reboot into Ubuntu (you'll have no option to boot PCLinuxOS from the MBR as you haven't changed it yet) and edit /boot/grub/menu.lst adding these lines:

title PCLinuxOS
rootnoverify (hd0,3)  # assuming hda4
chainloader +1

Then, if you want to remove PCLinuxOS, you can just delete its partition, boot into Ubuntu and remove those lines from menu.lst to get back to where you started.

Can't help with the /home partition thing as I've never had one on a different partition.

---

### Post by louieb on 2007-06-27
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") contains information on chain loading and lots of other dual boot information. I echo benson444 that chain loading or a config file entry is the way to go when dual booting multiple Linux Distributions.   

Just formating your swap partition with PCLinuxOS should not cause any problems. 

You can use the same /home partition for both. But be aware that you could get some strange behavior from some of your programs. Probably best to keep  different /home folders for each distribution.

---

### Post by encho on 2007-06-27
PCLOS used lilo some time ago, but latest one is with grub. So all the above is correct and useful. I would recommend using different home as well (or diff username), as it might behave differently in some occasions. And uninstalling would be less painful (that's if you ever want it to ;))

---

### Post by timcredible on 2007-06-27
since ubuntu is gnome and pclos is kde, you won't have desktop problems booting between the two (i did this with ubuntu 6.06 and pclos 0.93a for quite a while).

however, on the booting, i disagree with the other posts.  i believe that pclos changed to grub with the 2007 iteration, so you can use the 'CONFIGFILE' option in grub.  basically, it says 'go to this other menu.lst file and do what it says'.  the reason i think this is better is because it lets the entire menu.lst file be run in case there's something in it that the pclos needs.  be aware that if pclos2007 is still lilo, CONFIGFILE isn't an option.

i'm not on the machine where i've got this or i'd post the details on the configfile option

---

### Post by wersdaluv on 2007-06-27
I have installed PCLOS succesfully. All I had to do was not to install GRUB on the MBR and to create a different user name on the home partition so that my configuration files between the two distros wont create conflicts.

---

