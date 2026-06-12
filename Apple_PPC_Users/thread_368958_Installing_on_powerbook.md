---
title: "Installing on powerbook"
date: 2007-02-23
forum: Apple PPC Users
---

### Post by jaimesharp on 2007-02-23
I would like to know what is the best method for a dual boot with tiger and ubuntu 6.06 also whenever i try and install on a blank drive it gives cannot create filesystem errors what is causing this

---

### Post by beanworks on 2007-02-26
[INDENT]what is the best method for a dual boot with tiger and ubuntu 6.06[/INDENT]

Hopefully you have the tiger disc.  :)   The best way is to back up all your stuff, or even better, create a bootable disk image on a different drive (such as a firewire drive), then use the disk utility on the tiger install disk to create two partitions.  This is going to wipe out what you have on the drive (which is why creating the disk image is important - check to make sure the disk image will boot before you proceed).  

Go back into the disk utility on the OSX disk, in the left pane select the disk you want to install Ubuntu on, and click the partition tab.  Use the drop down menu to select two partitions.  In the first partition, select the recommended Mac filesystem type.  For the other partition (give Ubuntu at least 5 GB) select "free space" then click on the button to start the partitioning process.

When the partitioning is finished, use the Tiger disk utility again to restore the disk image on the firewire drive to the new partition you created.  When that is up and running, put in the Ubuntu disk, and hold down the "C" key on reboot.  When you install, you will come to the partitioning tool.  Either select the option that says "Use largest continuous free space" or "Manually Partition."  You should probably use the manual partition option if you have a lot of space on each partition, just to make sure that Ubuntu selects the correct partition.  Use the recommended configuration as long as it uses the correct partition.  You will have a chance to check the configuration before you commit to the changes. (and don't get rid of that disk image, just in case!)

After Ubuntu installs, you will have the option, on boot, of selecting either Linux or OSX.

[INDENT]whenever i try and install on a blank drive it gives cannot create filesystem errors what is causing this[/INDENT]

Is it a firewire drive?  Macs will only boot from external drives if they are firewire. Also, before you install on a new drive, you will have to format it and create at least one partition, but you can do that during the install process.

---

### Post by jaimesharp on 2007-02-27
thanks for answers i had thought of that buy now yaboot fails either way at 98% complete

---

### Post by grazie on 2007-02-27
Hi jaimesharp,

In order for someone to help you'll need to provide a lot more details. Do you mean the installation is failing at 98%, installing yaboot? If you've got a powerpook, you intend to dual boot and you've installed to a blank disk, then this must be an external drive? Correct? If so, you've come to a known bug that's recently been discussed [here]("http://www.ubuntuforums.org/showthread.php?t=364587"). The problem can be overcome, but setting up booting from an external drive can be awkward.

---

### Post by jaimesharp on 2007-03-12
The installation fails at 98% when it hits yaboot the drive is not firewire and i knew macs could not boot usb but i wanted to install linux as a portable drive so i could use it in multiple machines as it is an ide hard drive which was an internal but i sold the machine from which it came out of. this test was also conducted on the internal drive as well creating the unknown file system error.

---

