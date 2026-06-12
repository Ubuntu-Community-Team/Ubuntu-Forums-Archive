---
title: "Booting Problem"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2007-07-23
I accidentally formatted a linux partition when I was using windows.Now the system doesnt boot at all. I think I have done something to the boot loader.How can I fix it.

---

### Post by Mornedhel on 2007-07-23
You mean it doesn't boot into Windows either ?

If you want your Linux back, only option you have is a complete reinstall of Ubuntu (this will also reinstall GRUB so you will be able to boot back into Windows). If you only want Windows, there are some tutorials out there on how to install GRUB without going through a complete Linux installation, or how to install many other bootloaders.

---

### Post by benx009 on 2007-07-23
if you just want windows, insert your original windows disc at boot, go to the recovery console, and type **fixmbr**

---

### Post by Wim Sturkenboom on 2007-07-23
@Mornedhel: Of course it does not boot. OP has deleted some essential GRUB files (a reason why I prefer Lilo).

To get windows going again, insert the windows installation disk, go to recovery mode (or something like that) and run fixmbr (and you might have to run fixboot as well).

You can reinstall Ubuntu as well in which case it will fix the problem.

---

### Post by sailor2001 on 2007-07-23
I would suggest downloading and burning a "super grub" disk for the future

---

### Post by vivin_west on 2007-07-24
I did fixmbr in windows recovery mode. While the windows boots the Ubuntu portion doesnt boot.How do I recover that data.I have very important data in Ubuntu. I cant afford to loose my Ubuntu portion

---

### Post by Skrynesaver on 2007-07-24
If the data was on the partition you have formatted, I'm afraid it is gone.
Do you have a backup ?

---

### Post by Wim Sturkenboom on 2007-07-25
How did you setup Ubuntu? Seperate home partition? In that case it's safe to re-install Ubuntu; just make sure that during the partitioning you don't format the home partition. Or (if it was partitioned as ext2/ext3, you can use [http://www.fs-driver.org/](http://www.fs-driver.org/) from windows to recover..

And sorry to say, but if you don't have backups, your data was obviously not important for you.

---

### Post by vivin_west on 2007-07-27
I set up Ubuntu through live CD and just followed the steps. I do not know much about boot loaders. Anyway Fixmbr worked. Windows is booting fine. In the windows section there is 10 Gb partition named Unknown which I assume is a linux file system which has all my contents. I accidentally formatted a 300 Mb partition . But I am unable to install Ubuntu.While running the live CD it gives some grub related error and the systems hangs.

---

### Post by thefoolisme on 2007-07-27
What linux partition did you format?  That might help.  If it was the one you stored your data on, then you've lost it.  

If was a different partition, then someone can talk you through a reinstall without writing over the data.  however, to be on the safe side, I would make a backup of your data from Windows before attempting it.  You can get drivers for windows to read ext3 files.

---

### Post by vivin_west on 2007-07-27
I am not sure what partition I formatted as the windows disk manager names all non window files types as unknown unlike grub. But I know for sure that there were two partition.One just 300 Mb and the other 10GB. I formatted this 300Mb space. This disabled grub completely. I cant install ubuntu since grub is a default partitioner. I have even replicated the same on another laptop.The result is the same. Ubuntu wont install at all coz grub will never start.

Please try this(if you want to replicate the problem).

Install Ubuntu(select continuous free running space during install)

Boot in windows and go to the dis manager. You will find two partitions named unknown
 
One will be 300Mb, the other 10 Gb(or something larger depending on your system specs)

Format the 300 Mb partition.Windows will convert it to say NTFS. Now try booting your system. Grub will not function. Now using a windows boot CD run the command fixmbr.

Now windows will boot. But Ubuntu live CD will hang during installation.

---

### Post by envykris on 2007-07-27
i had the same problem..but you can use the Live CD or the alternate CD and choose the "rescue broken system" option...and then choose to reinstall Grub, that shd get you up and running provided you dint format the linux partition

cheers!

---

### Post by vivin_west on 2007-07-27
Can you tell me where to find this 'rescue broken system' option

---

### Post by Wim Sturkenboom on 2007-07-27
300M parition sounds like swap or /boot to me. So I guess your lucky from that perspective and your data will still be there

Do not install Ubuntu; it will probably destroy everything.
Boot from live CD
run *sudo fdisk -l* in a terminal; you will probably find some linux partitions
*mount* them (I can not say at this moment how to do it in Ubuntu)
copy files to memory stick or burn on CD
unmount

As an alternative, you can download a tool for windows from [http://www.fs-driver.org/](http://www.fs-driver.org/) that should allow you to read ext2 / ext3 partitions.



PS 1) grub is not a partitioner.
PS 2) if you already attempted to install Ubuntu and got past the partitioner, your data will more than likely  be gone

---

### Post by vivin_west on 2007-07-30
I was able to retrieve the data and run it on another system thanks,but I still cant figure out why Ubuntu is not installing on both my machines. There is nothing wrong with the Live CD as I tried both the live CDs I got through shipit. I just am not able to install... it is grub that is not working. Again a grub error is displayed during installation....

---

### Post by Wim Sturkenboom on 2007-07-31
At the end of the installation (I assume) or at the beginning ?

---

