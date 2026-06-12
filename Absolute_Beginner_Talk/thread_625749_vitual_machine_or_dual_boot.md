---
title: "vitual machine or dual boot?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-11-28
i  need to use two map programs(micro$haft specific) for work maybe 10gb. what is my best option of the above as i had no success with wine & this laptop is Ubuntu only.
if i was to install XP , do i use something like gpart first?

---

### Post by SoggyCornflake on 2007-11-28
> **jon zendatta said:**
> i  need to use two map programs(micro$haft specific) for work maybe 10gb. what is my best option of the above as i had no success with wine & this laptop is Ubuntu only.
if i was to install XP , do i use something like gpart first?

If you install Windows XP, it will probably wipe out your Ubuntu install - (Microsoft doesn't normally play nice with other Operating Systems).

Laptops historically have more customized hardware than their desktop counter parts, so a VM running a generic Windows XP installation may have trouble using some peripherals unless VMWare ( or whatever VM program you use) can handle the differences.  VMWare is pretty good I think, so you might be OK going that route

I would try the VM first.  If that doesn't work, then I'd make a backup of your Ubuntu installation and then install Windows XP in a partition and then reinstall your Ubuntu in another partition.

Hope that helps

---

### Post by ewr2san on 2007-11-28
It's also possible to do a bit of both.
[http://www.vmware.com/support/ws5/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws5/doc/ws_disk_dualboot.html)

You setup a dual boot system.  Then from inside Linux your VM boots windows from the raw partition (the dual boot one).  That way you get the best of both.  Wanna run a single windows app inside Linux, no problem.  Want to reboot and run windows.  Ok go for it.  Theroretically youi could set it up both ways and also boot the Linux partition as a VM under windows as well.

I used to have this running on my laptop with vmware, but gave it up in favor of 100%  kubuntu.

---

### Post by jon zendatta on 2007-11-28
cool thanks sounds like i have 3 options: i try vm tonight thanks

---

### Post by bodhi.zazen on 2007-11-28
> **SoggyCornflake said:**
> If you install Windows XP, it will probably wipe out your Ubuntu install - (Microsoft doesn't normally play nice with other Operating Systems).

Laptops historically have more customized hardware than their desktop counter parts, so a VM running a generic Windows XP installation may have trouble using some peripherals unless VMWare ( or whatever VM program you use) can handle the differences.  VMWare is pretty good I think, so you might be OK going that route

I would try the VM first.  If that doesn't work, then I'd make a backup of your Ubuntu installation and then install Windows XP in a partition and then reinstall your Ubuntu in another partition.

Hope that helps

LOL

ANY OS will do this if you are not careful (they all have to option to "use entire disk").

If you are wanting to install another OS, windows or otherwise, there are a few things you should understand.

1. How does partitioning work ? Window uses C:\ E:\ 
Linux uses /dev/hdxy or /dev/sdxy

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

2. You will need to make space for your new OS. What you need to know is that Windows (and a few other OS) need a PRIMARY PARTITION to install into.

You should probably manage your partitions from a live CD, you can use the Ubuntu CD or the gparted live CD.

Resize your ubuntu root partition and make a new FAT primary partition (for windows).

gparted Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

3. Install windows into the FAT partition. It is OK to reformat the space to NTFS (I would advise this).

4. Restore grub : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

=======================

Also, be advised I consider booting a physical partition with VMWare/Vbox to be Beta, it may or may not go well for you to do so.

=======================

My advice is to install Windows into qemu/VMWaer (server)/Virtual Box on Ubuntu.

qemu : [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

VMWare Server : [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

VirtualBox : [http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

The advantage is that you will not need to dual boot, ie you can access both OS at the same time.

The disadvantage is that qemu/VMWaer (server)/Virtual Box do  not directly use your hardware ie they emulate a videocard so you may or may not have problems with your application.

---

### Post by Depressed Man on 2007-11-28
I'd say it depends on the software. If your just keeping it to run something like Microsoft Word then just use Wine or a virtual machine. 

But if it's a game that relies on directX or any program that's 3D in DirectX you pretty much have to dual boot unless there is Wine support for it.

---

