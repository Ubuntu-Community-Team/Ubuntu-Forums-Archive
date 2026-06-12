---
title: "Deleted Device Driver Partitions, Can my Mac be saved?"
date: 2007-01-07
forum: Apple PPC Users
---

### Post by plays_with_fire on 2007-01-07
I recently acquired a PowerBook G3 Pismo. Not being a Mac Person I decided the first order of business was to get a proper operating system running on it. So I've got Ubuntu Dapper Drake running just fine, and I left space on my hard drive to re-install OS X under a dual boot system. 

Problem is, when I formatted the hard drive I got rid of the Device Driver Partitions. I didn't know what they were and my PC instincts told me the best way to get an old computer running well with a fresh operating system is to kill all the partitions on a drive, reformat, repartition, etc. 

Now my OS X Install DVD doesn't boot properly. Does anyone know a way to restore the Device Driver Partitions or should I give up hope of running OS X on this hard drive?

---

### Post by janiocarvajal on 2007-03-21
i am equal... to you...


i have installed ubuntu... and... 


i need install mac os 10.4 and the DVD run but "disk utility" say "gathering disk information" and nothing more...

:_(

i have a PowerBook G4 - 1Gz - 512 RAM - 60 GB

ubuntu run lower that mac os in my PowerBook G4...

I need Install MacOS ... buaaaaaahhhh  :_(

if you can send information to: [email]janiocarvajal@gmail.com[/email]

gmail is great ... no fear to spam!

sorry, poor english!

---

### Post by grazie on 2007-03-21
I've never run OS9 (for any length of time) so I'm no authority on this, but the hard disk driver partitions referred to are only required for OS9. Removing them will not affect the machines abillity to boot any install cd. If OS9 needs to be installed on the hard drive without any OS9 driver partitions, you do have a problem. I believe the OS9 install cd does not have the ability to recreate these partitions. However, the OS X install does have this ability. Unfortunately, I believe the only way to to recreate the OS9 driver partitions is by wiping the whole disk.

---

### Post by seatea on 2007-03-21
I don't have a solution, but I don't think that the absence of the devise drivers should have any effect on your  ability to boot the Mac OS X installation CD. You might be able to use the Ubuntu installer to create a HFS partition in the free space, as Ubuntu doesn't do HFS+; erase the HFS partition with Disk utility and format as HFS+; then install Mac OS X on that partition. Sometimes a peripheral will interfere with CD booting.

---

### Post by plays_with_fire on 2007-03-22
At this point I suspect my Mac OSX dvd, it's a burned copy, worked once for a re-install of Mac OSX when Mac OSX was installed already, but after formatting the hard drive it hasn't worked. One of these days I'll remind my buddy that sold me the machine to burn me a new copy, or just get impatient and go buy one.

---

### Post by woopie49 on 2007-03-22
janiocarvajal

Unfortunately I think you will have to do a re-install

Boot from the OSX CD/DVD

When loaded, under Edit (I think) select Disk Utility, select your HD icon that will be shown in the left hand side of the window (not the partitions)  and erase it.

Partition your HD into 2x 30gig partitions (or whatever size you like) then proceed to install OSX, reboot and update sys software.

Then install Ubuntu - when Ubuntu comes to partitioning during installation, select "largest free space" (which should auto select the other partition) or select the other partion manually.

After installation, reboot, holding down the "option" key to get the "old age Mac" splash screen to appear, select what you want to boot from or just reboot straight into OSX

It may be of interest to any who wish to use OS9 as well - OS9 must be installed within the first 8gig of the HD or the first partition

Ron

---

### Post by woopie49 on 2007-03-22
addendum....

I should clarify my last paragraph, the OS9 driver can be installed with earlier versions of Disk Utility that came with (up to) 10.3.8 (I think) and is loaded during formatting. This is true for any Mac that supports booting OS9 natively up to Mac G4 dual 1.25 FW800.

The "option" slash screen only works with G4s and up as far as I am aware

Ron

---

### Post by janiocarvajal on 2007-03-27
i had resolved the mac inconvenient...


a friend, change the logical board to the hard disk and this unblock for install...


the problem is mac... is very closed operating system...

I recommend that they do not only install "ubuntu" in "powerpc" but that they make a partition and they have operating systems both. For some reason mac "powerpc" is blocked at disc level not to allow the installation of strange operating systems. If I am mistaken corrijanme please, but to me it happened to me. atte,

---

### Post by ZoiaGuyver on 2007-03-28
All the Mac's running OF have the ability to write protect the HD against major changes to the HD's mbr, it also has a second protection of encrypting the drive. This being closed source Apple design isnt able to be overwritten by anything other than Mac OS as far as i know. 

Ive tried and failed on many Mac's to install linux only to come up against this and normally it means one of two things, either get a new HD or find out what the pass was.

On all the macs ive done its been the first option (luckily none have used the OF protection where you cant assign changes to OF).

If you have any of Mac OS X disks upto Tiger i think it was they all should be able to handle most things the dual boot for OS9 option is for "Classic" mode only. This is normally used for applications not designed or able to run on OS X (tbh i havnt found many that havnt been updated too).

Other option is just use Ubuntu (or Varients) i run 4 Mac's at the mo ranging from G3's to G4's of all different types and not one has Mac OS X on it (thats sat in the cupboard collecting dust :P).

Any linux has its downsides but Ubuntu on PPC has a lot less than most.

---

