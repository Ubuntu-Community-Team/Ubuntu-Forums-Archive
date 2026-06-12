---
title: "First Time - Need Help"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by RageRhinos on 2007-05-08
Im in the process of downloading the .iso

please let me know, if i am going about this in the right way.

after it downloads i need to burn it to a CD?

then i put it in the cd drive and reboot, i will then be able to install? or do i need to set something so it tries to boot from the CD drive? if so how do i do this?

then i just install as normal, and will have ubuntu running?

this wont delete windows right? and when i turn my computer on i will have the option to boot using either windows or ubuntu? can someone confirm this?

all help is appreciated!

---

### Post by bollix47 on 2007-05-08
Most of your questions should be covered [here]("http://www.psychocats.net/ubuntu/index").

---

### Post by epb on 2007-05-08
Yes you're going the right way! :) After you've downloaded the iso, you need to burn it to a cd, and then you've got a Live cd. [Look here]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29"), on how to burn the iso to a cd.

Afterwards, you should tap in the CD and reboot from this.. then you can try out Ubuntu without having to install it (so yes, this won't delete Windows!).

---

### Post by LaRoza on 2007-05-08
> 
please let me know, if i am going about this in the right way.

after it downloads i need to burn it to a CD?


You need to burn it as an image, not a data file.

> 
then i put it in the cd drive and reboot, i will then be able to install? or do i need to set something so it tries to boot from the CD drive? if so how do i do this?


You can use the Live CD to run Ubuntu live. You should be able to boot from a disk without trouble unless you set your BIOS not to.

> 
then i just install as normal, and will have ubuntu running?


During the install process, you are given options, but before installing, you should try the live cd. If you do install, Ubuntu can alter the partitions to make room for Ubuntu without erasing anything, but you should backup essential data anyway. You can manually repartition, resize the partition or overwrite the drive.

If you want to dual boot with Windows, defrag windows first.
 
> 
this wont delete windows right? and when i turn my computer on i will have the option to boot using either windows or ubuntu? can someone confirm this?

Yes, Ubuntu locates Windows and adds it to Grub.

---

### Post by Cypher on 2007-05-08
Yes..you download the ISO and burn it, it will make a bootable CD.

You should check your BIOS and make sure that the CD is set to boot before the HD. Then insert the CD and the LiveCD will boot into a full GUI desktop.

From here, you can play around with Linux and if you want to install it click on the Install icon on the desktop.

If you have free space available on your HD right now, Ubuntu can be installed to that, if not you will need create new space you should use a partition resizer tool either in windows or Linux to make some space.

When you install GRUB onto the HD, it will automatically setup the dual-boot with Linux and Windows..

---

### Post by kebes on 2007-05-08
You may find a guide such as this one:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

To be helpful. It has detailed instructions (with screenshots) showing how to burn the disk image, boot, etc.


But to give you brief answers to your questions:

1. After downloading the .iso, you just burn it to disk. A common mistake is to burn the files to a CD, but in fact you have to select the "burn disk image" option, and then select the ISO file. This makes a bootable disk.

2. Then you put the disk in the drive and reboot. Normally you will boot directly into the Ubuntu Installer. However, on some computers you need to enter BIOS and turn on the "boot from CD" option.

3. Once the disk loads, you will have a full (though slow) Ubuntu session. You can try it out and see if you like it. If you want to install, click the "Install" icon on the desktop.

4. During the installation process, there is a "partitioning phase" where it asks you how you want to partition. At this stage, you can decide if you want to erase Windows, or resize partitions and install in the free space. This is the step where you must be very careful, so that you don't accidentally erase Windows. (As always, it's a good idea to backup important data before doing something like this.)

5. Once the install completes, you just reboot. If you didn't erase Windows, then you will have a screen during bootup where you select Windows or Ubuntu.



If you need any additional information, please feel free to ask more questions.

---

### Post by thefoolisme on 2007-05-08
And please make sure you back up all of your important files before attempting this!!  

Read up and become familiar with the process.  Use the links everyone has provided for you above.  Most of the information you need will be in them. If you need any clarification, feel free to ask.

---

