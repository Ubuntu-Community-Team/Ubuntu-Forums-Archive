---
title: "Error Loading OS Ubuntu 7.04"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by kyrhash on 2007-06-12
Ok i got the 7.04 live CD to work (i got the /bin/sh: can't access tty; job control turned off error) but i eventually got it just by rebooting my system so i double clicked the install icon and followed the wizard.  i choose to install on an 80 GB hard drive.  I finished the wizard and rebooted the system.  The System got past the BIOS but then showed up the message "error loading operating system" and stopped altogether.  This is my first attempt at a Linux install so i may have done something completely wrong.  Also i have 2 hard drives in my computer that were completely blanked before the Linux install 1 is 250 gb and the other is an 80 gb.  I dont know what kind of connectors they have.  Any help will be greatly appreciated.

---

### Post by Inxsible on 2007-06-12
> **kyrhash said:**
> Ok i got the 7.04 live CD to work (i got the /bin/sh: can't access tty; job control turned off error) but i eventually got it just by rebooting my system so i double clicked the install icon and followed the wizard. i choose to install on an 80 GB hard drive. I finished the wizard and rebooted the system. The System got past the BIOS but then showed up the message "error loading operating system" and stopped altogether. This is my first attempt at a Linux install so i may have done something completely wrong. Also i have 2 hard drives in my computer that were completely blanked before the Linux install 1 is 250 gb and the other is an 80 gb. I dont know what kind of connectors they have. Any help will be greatly appreciated.
 
Did you have windows installed on the 80GB drive? Were you trying to set up a dual boot?
 
Can you log in via the LiveCD again and enter the following command in the terminal. Post the results here.
```
sudo fdisk -l
``` -l is lowercase L

---

### Post by kyrhash on 2007-06-12
No windows or dual boot i will be back in a sec with the command.

---

### Post by kyrhash on 2007-06-12
sudo fdisk -l yeilds this:

disk /dev/sda:  250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
units= Cylinders of 16065 * 512=822580 bytes

Device     Boot   Start    End   Blocks   ID    System

Disk /dev/sdb:  80.0 GB, 8000000000 bytes
255 heads, 63 sectors/track, 9728 cylinders
units= Cylinders of 16065 * 512=822580 bytes

Device     Boot   Start    End   Blocks              ID    System
/dev/sdb1 *       1          9540  76630018+   83    Linux
/dev/sdb2          9541   9726   1494045        5      Extended
/dev/sdb5          9541   9726    1494013       82    Linux Swap/Solaris


Sorry that took so long had to copy it by hand and transfer to this computer.

---

### Post by moebob24 on 2007-06-12
> **kyrhash said:**
> Ok i got the 7.04 live CD to work (i got the /bin/sh: can't access tty; job control turned off error) but i eventually got it just by rebooting my system so i double clicked the install icon and followed the wizard.  i choose to install on an 80 GB hard drive.  I finished the wizard and rebooted the system.  The System got past the BIOS but then showed up the message "error loading operating system" and stopped altogether.  This is my first attempt at a Linux install so i may have done something completely wrong.  Also i have 2 hard drives in my computer that were completely blanked before the Linux install 1 is 250 gb and the other is an 80 gb.  I dont know what kind of connectors they have.  Any help will be greatly appreciated.

Did you ever get this message when you tried to boot the live CD
"loading
invalid or corrupt kernal image"

I am not sure this means, it has happened 2 times now with 2 different liveCDs with iso files downloaded from 2 different places. i think since i am on a laptop there is something I am not doing right.

---

### Post by kyrhash on 2007-06-12
nope never had anything with the kernel go wrong that i saw.

---

### Post by ICUR2Ys on 2007-06-12
I am pretty new so I won't be offering technical advice.

moebob24, if you question the quality of the cd's that you downloaded, why not contact a local LUG, or loco team.  They could probably send you one that they know is good.

---

### Post by moebob24 on 2007-06-12
> **ICUR2Ys said:**
> I am pretty new so I won't be offering technical advice.

moebob24, if you question the quality of the cd's that you downloaded, why not contact a local LUG, or loco team.  They could probably send you one that they know is good.

Hmmm...i never thought of that.
Thanks

---

### Post by kyrhash on 2007-06-12
I don't mean to be rude but can we please get back on topic.

---

### Post by kyrhash on 2007-06-12
Hello World

---

### Post by kyrhash on 2007-06-13
Hello Linux World?

---

### Post by Inxsible on 2007-06-13
If you have never been able to log in to the HDD Linux, why not try and re-install it again using the LiveCD itself.
 
Check this link for help on installing
 
[Install Ubuntu]("http://ubuntuforums.org/www.psychocats.net/ubuntu/installing")

---

### Post by kyrhash on 2007-06-13
What would be the best way to format the harddrive so that i can reinstall, can that be done from the live CD?

I am going to be afk for about 2 hours.

---

### Post by kyrhash on 2007-06-13
anyone...

---

### Post by Inxsible on 2007-06-13
Yes you can use GParted on the Live CD to format your drives.
 
Its under System -- > Administration --> GParted

---

### Post by kyrhash on 2007-06-13
I figured out that if i boot the live CD then choose boot first hard disk or whatever it will come up.  Any idea why my hardware hates Ubuntu?

---

