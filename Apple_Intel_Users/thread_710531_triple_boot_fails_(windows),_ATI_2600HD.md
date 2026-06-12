---
title: "triple boot fails (windows), ATI 2600HD ???"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by Hinsky on 2008-02-28
okay
i had a mac os 10.5.2 partition and a windows partition in ntfs
both worked fine until today -.-
i installed ubuntu 7.10 64bit, it's working fine excepting my graphic card 

now the first question is (i looked into several guides and some other thread but maybe i'm to stupid to install these damn drivers... i tried it "the ubuntu way" and after that my xorg.conf was completely empty. i had no backup but welll... i found xorg.conf.original-0 and xorg.conf.original-1 in /etc/X11 so i just took one of them (0)
i didn't understand the manual way...
ah  and i got an error message "not found" when i tried to configure the driver after installation.

ok  and now the important part ;)
after installing Mac OS and Windows everything worked fine as i said. ubuntu and rEFIt, too.
When i turn on my computer rEFIt launches and i can chose one of the 3 systems. mac os works fine
if i chose win xp or ubuntu i get a message from grub and can chose a linux kernel i want to boot or win xp. when i chose win xp (now i come to the point ^^) i get an error message "invalid device" or something like that.
what went wrong?

i wish to boot all 3 systems and i want to chose only one time in rEFIt which one should boot. no grub etc. after chosing win or linux.

yep... that's it  :guitar:

---

### Post by cyberdork33 on 2008-02-28
> **Hinsky said:**
> i wish to boot all 3 systems and i want to chose only one time in rEFIt which one should boot. no grub etc. after chosing win or linux.
You have to go through a bootloader for Linux. You do not want to remove the ability to change kernels, because if you have a problem, you will not be able to get into recovery mode, or change to a different kernel.

Look at the multi boot guide in my signature. It will show you how to fix the windows issue so that you boot straight from rEFIt. You can turn the timer down in grub so that it automatically boots the first kernel in less time. This is adjusted in /boot/grub/menu.lst

---

### Post by cyberdork33 on 2008-02-28
There is an option in the files called timeout. This is the number of seconds that grub will wait for input before booting the default.

---

