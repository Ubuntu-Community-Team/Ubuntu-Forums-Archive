---
title: "win7 question"
date: 2011-12-03
forum: Any Other OS
---

### Post by rburkartjo on 2011-12-03
okay i got a free win7 os as a gift. thinking of installing it on its own partition. i already have ubuntu 11.10 and mint 12 installed each on its own partition. i have read that if i install win7 after i have linux installed that i can mess up grub. is that true, and i believe that i have to format the partition i want to use as fat. tks

---

### Post by Basher101 on 2011-12-03
you must create a partition at least ~ 40 GB big for windows (as it will grow a lot, lot bigger with all those updates......). you must format it NTFS. Note: windows need TWO PRIMARY partitions (one 100 MB for boot files, the rest for OS) in order to function properly. I haven't tried installing it at the **_end_** of the Hard disk, but usually it is installed at the front. Also if you have installed it, it WILL mess up your grub. Here is how you can fix that after installing:

[http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)



regards

---

### Post by roger_1960 on 2011-12-03
Yes

Installing W7 after linux will wipe out grub!  Best not to.  If you want dual boot (triple boot), backup everything, install windows then reinstall linuxes.  Or you could run windows in a virtual machine running in linux - Virtualbox or VMware...(but I've not done that - yet)

---

### Post by Basher101 on 2011-12-03
> **roger_1960 said:**
> Yes

Installing W7 after linux will wipe out grub!  Best not to.  If you want dual boot (triple boot), backup everything, install windows then reinstall linuxes.  Or you could run windows in a virtual machine running in linux - Virtualbox or VMware...(but I've not done that - yet)

consider his hardware not able to handle windows in a VM

---

### Post by rburkartjo on 2011-12-03
tks for all your help. and bash tks for the info on repairing grub after a win7 install

---

### Post by CryptAck on 2011-12-03
I've never encountered a major problem installing Windows after Linux. In the past, I've had to do this a couple times since every 6-12 months I need to re-install Windows, but not so much Linux :)

Yes, installing Windows will overwrite your GRUB settings, but you can use a LiveCD and re-install GRUB.

Windows will show your partitions in the installer as "unallocated" space, since it does not read Linux file systems. To be safe, backup before installation. The Windows Installer will format the partition in NTFS by default.

I've always had Windows be the first primary partition, so I cannot speak on the installation of Windows on a logical partition. Microsoft appears to believe that it's operating system is always primary.

---

### Post by Basher101 on 2011-12-03
> **rburkartjo said:**
> tks for all your help. and bash tks for the info on repairing grub after a win7 install

always glad i could help. Lol now imagine someone from Microsoft to help you like this without the question "Did a reboot fix it?" :D

kudos to all ubuntu users


regards

---

### Post by sadaruwan12 on 2011-12-03
Yes that will mess your grub why do you want install win 7 when you have two of the greatest distros installed on your laptop.

---

### Post by Basher101 on 2011-12-03
> **sadaruwan12 said:**
> Yes that will mess your grub why do you want install win 7 when you have two of the greatest distros installed on your laptop.

Maybe he does not have good enough OpenGL support on his hardware to run some games and still wants to run them on windows...

---

### Post by CryptAck on 2011-12-03
> **sadaruwan12 said:**
> Yes that will mess your grub why do you want install win 7 when you have two of the greatest distros installed on your laptop.

Curiosity.

---

### Post by Serpher on 2011-12-03
> **Basher101 said:**
> Note: windows need TWO PRIMARY partitions (one 100 MB for boot files, the rest for OS) in order to function properly.

This is just plain false. I don't believe you can even do that with Windows. You need 1 ~40GB NTFS partition.


> **Basher101 said:**
> I haven't tried installing it at the **_end_** of the Hard disk, but usually it is installed at the front.

This is also false. It's installed wherever you want it, and will run from anywhere. Nothing is effected by its location on the hardrive, except for extremely marginal speed increases I think. Take this from somebody who uses Windows 7 as their main OS. I just use Linux (CentOS) on servers I have.

But yeah it'll mess up GRUB, but it's as easy to fix as booting from a LiveCD and running a few commands.

---

### Post by Mark Phelps on 2011-12-03
I was going to reply, but Serpher beat me to it.

Do NOT format the new partition for Win7.  It's best to lest Win7 format it during install. And please note that Win7 won't even install in a partition formatted as FAT or FAT32.

And yes, you only need ONE NTFS partition, not two.  Win7 creates a second, boot, partition ONLY when it is installed to an empty drive -- which yours is not.

And in future, if you have additional questions about Win7 after you install it, strongly suggest you go to the right place to get answers -- sevenforums.com.

---

### Post by Basher101 on 2011-12-03
> **Serpher said:**
> This is just plain false. I don't believe you can even do that with Windows. You need 1 ~40GB NTFS partition.

windows created two partitions for me when i pointed it at ONE 30 GB NTFS partition...i think i did not explain myself accurate enough what i meant when i said it needs two partitions...

---

### Post by CryptAck on 2011-12-03
> **Mark Phelps said:**
> 
And yes, you only need ONE NTFS partition, not two.  Win7 creates a second, boot, partition ONLY when it is installed to an empty drive -- which yours is not.

I'm a bit confused by this statement. If the drive is brand new and you install Win7, it'll now create two partitions, one of which is for a boot?

---

### Post by Basher101 on 2011-12-03
> **CryptAck said:**
> I'm a bit confused by this statement. If the drive is brand new and you install Win7, it'll now create two partitions, one of which is for a boot?

the boot files will be stored on the small 100 MB partition, the rest of the OS will be stored on the bigger one. Windows creates the smaller one automatically, tho i had the experience that if you already have a smaller NTFS partition next to a larger one, it will use the smaller one as the system reserved partition.

---

### Post by pqwoerituytrueiwoq on 2011-12-03
> **Basher101 said:**
> windows created two partitions for me when i pointed it at ONE 30 GB NTFS partition...i think i did not explain myself accurate enough what i meant when i said it needs two partitions...
if you already have 3 primary partitions (not counting one for windows) windows will not make that

i have managed to install windows 7 64bit on to 10gb but dont expect it to be worth using it has virtually no space for the pageing file much less updates/software that is actually useful

---

### Post by Basher101 on 2011-12-03
> **pqwoerituytrueiwoq said:**
> if you already have 3 primary partitions (not counting one for windows) windows will not make that

i have managed to install windows 7 64bit on to 10gb but dont expect it to be worth using it has virtually no space for the pageing file much less updates/software that is actually useful

Thats why i used vLite (which is actually designed for Vista) to scram off all the bloatware i do not need like the server stuff or other languages. How high are the chances i will ever need Chinese?

After the "cleaning" of bloatware on the install disc, i got to 7 GB after a fresh install. It is more than 50% smaller than an original fresh install

---

### Post by Serpher on 2011-12-03
> **Basher101 said:**
> windows created two partitions for me when i pointed it at ONE 30 GB NTFS partition...i think i did not explain myself accurate enough what i meant when i said it needs two partitions...

Never happens to me. Upon doing some research it would appear that it is a boot partition. I wonder if it uses a faster version of NTFS without journaling or something.

---

### Post by CryptAck on 2011-12-03
> **Basher101 said:**
> the boot files will be stored on the small 100 MB partition, the rest of the OS will be stored on the bigger one. Windows creates the smaller one automatically, tho i had the experience that if you already have a smaller NTFS partition next to a larger one, it will use the smaller one as the system reserved partition.

Sorry, I should have clarified. 

I'm not confused by **what** it does, I'm confused on **when** it does it.

I have Windows 7 and I haven't received a boot partition on re-install. I'm wondering if it's an option to setup, or it doesn't do it simply because I have other partitions setup.

---

### Post by Basher101 on 2011-12-03
> **CryptAck said:**
> Sorry, I should have clarified. 

I'm not confused by **what** it does, I'm confused on **when** it does it.

I have Windows 7 and I haven't received a boot partition on re-install. I'm wondering if it's an option to setup, or it doesn't do it simply because I have other partitions setup.

Well on the "when" - it creates it, or reuses an already existing one during installation (i don't delete the 100 MB partitions upon a Windows 7 reinstall). Check your partition table, i am sure you have a small partition for the boot files somewhere...would be interesting to see if that is not the case..

---

### Post by Serpher on 2011-12-03
[[IMG]http://img696.imageshack.us/img696/7810/80529830.png[/IMG]](http://imageshack.us/photo/my-images/696/80529830.png/)

The 300MB partition is my boot for Fedora.

---

### Post by Basher101 on 2011-12-03
> **Serpher said:**
> [[IMG]http://img696.imageshack.us/img696/7810/80529830.png[/IMG]](http://imageshack.us/photo/my-images/696/80529830.png/)

The 300MB partition is my boot for Fedora.

interesting....usually windows sets up a small 100 MB partition before itself. Maybe this is not the case on pre-installed windows?

---

### Post by Serpher on 2011-12-03
> **Basher101 said:**
> interesting....usually windows sets up a small 100 MB partition before itself. Maybe this is not the case on pre-installed windows?

This wasn't pre-installed at all. I've honestly never ran into that 100MB partition xD. I'm using Ultimate edition, might be something Home Basic does or something like that.

---

### Post by Basher101 on 2011-12-03
> **Serpher said:**
> This wasn't pre-installed at all. I've honestly never ran into that 100MB partition xD. I'm using Ultimate edition, might be something Home Basic does or something like that.

true. true.

---

### Post by rburkartjo on 2011-12-03
okay going to try the win7 install. this old boy is no fool though. i copied my home to a separate partition and used remastersys to burn a copy of my linux os first(just in case). let ya'll know how it goes

---

### Post by Basher101 on 2011-12-03
you will need this to restore grub after the install [http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)

---

### Post by CryptAck on 2011-12-03
> **Serpher said:**
> This wasn't pre-installed at all. I've honestly never ran into that 100MB partition xD. I'm using Ultimate edition, might be something Home Basic does or something like that.

Same for me on Home Premium; never had a boot partition for Windows.

---

### Post by Basher101 on 2011-12-03
> **CryptAck said:**
> Same for me on Home Premium; never had a boot partition for Windows.

well i dunno how it is in general, but up until now i have never been able to install Windows 7 on any of my machines without the 100 MB partition...but oh well, as long as it works :3

Kudos to all

---

### Post by CharlesA on 2011-12-03
If the partition is already created, the installer won't create the boot partition.

---

### Post by Basher101 on 2011-12-03
> **CharlesA said:**
> If the partition is already created, the installer won't create the boot partition.

I can not agree with this. On reinstalls i delete the old windows volumes from the Windows installer CD when booted from it and it does indeed create the boot partition. When i create the new Volume it gives me a notification that it creates a system reserved Partition. I would like to upload a screen from virtualbox, but i cannot reboot to ubuntu right now..

---

### Post by Dr. C on 2011-12-03
> **Basher101 said:**
> interesting....usually windows sets up a small 100 MB partition before itself. Maybe this is not the case on pre-installed windows?

It depends on the type of Windows 7 installation media used. When I used the OEM media from HP to install Windows 7 Professional in a VM it did create the 100MB partition.

---

### Post by Basher101 on 2011-12-03
> **Dr. C said:**
> It depends on the type of Windows 7 installation media used. When I used the OEM media from HP to install Windows 7 Professional in a VM it did create the 100MB partition.

Oooooooh i see now. So up until now i have always used OEM installation...

mystery solved :popcorn:

---

### Post by CharlesA on 2011-12-03
> **Basher101 said:**
> I can not agree with this. On reinstalls i delete the old windows volumes from the Windows installer CD when booted from it and it does indeed create the boot partition. When i create the new Volume it gives me a notification that it creates a system reserved Partition. I would like to upload a screen from virtualbox, but i cannot reboot to ubuntu right now..

That's cuz you deleted the previous partition and recreated it.

If you create a partition in gparted, you should be able to just let Windows install on one partition.

---

### Post by CryptAck on 2011-12-03
> **Dr. C said:**
> It depends on the type of Windows 7 installation media used. When I used the OEM media from HP to install Windows 7 Professional in a VM it did create the 100MB partition.

That would explain the mystery, but I wonder why one would install differently than another..strange still.

---

### Post by rburkartjo on 2011-12-04
well i gave up for awhile until after i move. could not get it to install no matter what i did. though i learned how to use remastersys and make a live cd of my system. think i am going to get an external hard drive and install on that. will mess with it at a later date. seems to be a safer way.
tks ya'll

---

