---
title: "[SOLVED] Fixing Grub......."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-25
I installed Ubuntu 7.10 on my 40gig ext hdd. worked great and booted up just fine. Only problem is now when i unplug the usb drive from my computer, the grub wont load. I  HAVE to have the usb drive in to even turn on my laptop. How can i fix the grub in my laptop so it will load up again on its own?????

---

### Post by dcstar on 2008-03-25
> **N1N31NCHN41L5 said:**
> I installed Ubuntu 7.10 on my 40gig ext hdd. worked great and booted up just fine. Only problem is now when i unplug the usb drive from my computer, the grub wont load. I  HAVE to have the usb drive in to even turn on my laptop. How can i fix the grub in my laptop so it will load up again on its own?????

The grub files are on the external HDD, if you want to use the machine without it then you have to install Ubuntu on the internal HDD.

---

### Post by N1N31NCHN41L5 on 2008-03-25
> **dcstar said:**
> The grub files are on the external HDD, if you want to use the machine without it then you have to install Ubuntu on the internal HDD.

I'm sorry i forgot to mention that I am on a Acer Aspire 5100 that is dual loaded with Windows XP Media Center edition and Ubuntu 7.10 gutsy Gibbon. I loaded ubuntu on the ext hdd using this laptop. I can load any of the thre os's but the ext hdd MUST be plugged in. I just want to be able to load into Ubuntu or Windows agin WITHOUT having to have the ext hdd plugged in???:confused::guitar::confused:

---

### Post by bumanie on 2008-03-25
You will have to reinstall grub to your 7.10 installation that is on your internal drive. You will need to supply your setup for anyone to help. Post the output of > sudo fdisk -lu Grub has written itself to your external drive, that's why nothing will boot when the external drive is unplugged. Read this for heaps of info. on grub [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by N1N31NCHN41L5 on 2008-03-25
> **bumanie said:**
> You will have to reinstall grub to your 7.10 installation that is on your internal drive. You will need to supply your setup for anyone to help. Post the output of  Grub has written itself to your external drive, that's why nothing will boot when the external drive is unplugged. Read this for heaps of info. on grub [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

josh@josh-laptop:~$ sudo fdisk -lu
[sudo] password for josh:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    83072114    41536026    c  W95 FAT32 (LBA)
/dev/hda2       223849710   234436544     5293417+   5  Extended
/dev/hda3        83072115   223849709    70388797+  83  Linux
/dev/hda5       229151223   234436544     2642661   82  Linux swap / Solaris
/dev/hda6       223849836   229151159     2650662   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d02a533

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74943224    37471581   83  Linux
/dev/sda2        74943225    78236549     1646662+   5  Extended
/dev/sda5        74943288    78236549     1646631   82  Linux swap / Solaris




there yuo are, hope this helps

---

### Post by louieb on 2008-03-25
You Have Ubuntu installed on the internal drive too. Is that right?
I would have give the same link as bumanie.    But short of it is you you need to change GRUBS  IPL code in the internal hard drives MBR to boot  GRUB on the internal drive.

Boot up Ubuntu doesn't matter which one. 
Open a terminal window.
```
 sudo grub
``````
find /boot/grub/stage1
```Returns where it found the file. in the form of (hd#,#)  Should find it twice one for internal and external. Wild guess but (hd0,#) is probally the internal. 
Use what it returned to put GRUB IPL code back in the MBR of the internal drive.
Use the numbers from your internal drive (#)
```
 root (hd#,#)
``````
setup (hd#)
``````
quit
```Should be able to reboot now without the external plugged in.

To get Ubuntu on the external drive to boot you will have add an entry for it in the internal /boot/grub menu.lst Look at the page bumanie gave you and look for the **configfile **option.
Good luck.

---

### Post by bumanie on 2008-03-25
According to your fdsik -lu, your 7.10 install is dual booted with windows and your / is at hda3. To reinstall grub to your internal drive you will need to go to terminal and type
> sudo grub
> find /boot/grub stage
this should give the output of (hd0,2)
> root (hd0,2)
> setup (hd0)
[If the output is different, substitute the numbers and letters accordingly]
quit and reboot and see if it works. 
I suspect making this change will upset your external hard drive. I'm not sure of what your aim of having an external hard drive is, but you may need to use a utility that boots the drive from an .iso as this (from my experience) won't interfere with grub. I am happy for someone to correct me if I am wrong.

---

### Post by N1N31NCHN41L5 on 2008-03-25
> **bumanie said:**
> According to your fdsik -lu, your 7.10 install is dual booted with windows and your / is at hda3. To reinstall grub to your internal drive you will need to go to terminal and type


this should give the output of (hd0,2)


[If the output is different, substitute the numbers and letters accordingly]
quit and reboot and see if it works. 
I suspect making this change will upset your external hard drive. I'm not sure of what your aim of having an external hard drive is, but you may need to use a utility that boots the drive from an .iso as this (from my experience) won't interfere with grub. I am happy for someone to correct me if I am wrong.


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,2)
 (hd1,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub>   


NOW I"M LOSTTTTTT

---

### Post by louieb on 2008-03-25
You should have used **root (hd0,2)** not hd0,0)

other than that what you did will work. Just try it again.

---

### Post by N1N31NCHN41L5 on 2008-03-25
> **bumanie said:**
> According to your fdsik -lu, your 7.10 install is dual booted with windows and your / is at hda3. To reinstall grub to your internal drive you will need to go to terminal and type


this should give the output of (hd0,2)


[If the output is different, substitute the numbers and letters accordingly]
quit and reboot and see if it works. 
I suspect making this change will upset your external hard drive. I'm not sure of what your aim of having an external hard drive is, but you may need to use a utility that boots the drive from an .iso as this (from my experience) won't interfere with grub. I am happy for someone to correct me if I am wrong.

grub> find/boot/grub stage

Error 27: Unrecognized command

grub> find /boot/grub/stage1



sorry last post was results from louieb

and ext hdd IS plugged in while doing this

---

### Post by bumanie on 2008-03-25
Did you boot from the live cd? To do what you want you need to have your external drive disconnected, that's why you are getting two grub positions. As I originally said, your grub for your internal drive needs to go to (hd0,2). Instead of putting 
> grub> root (hd0,0) as you have done, you should have written** (hd0,2)**
You have now installed grub to your windows partition. Do you have a windows disc? If so, you can fix things up.

---

### Post by N1N31NCHN41L5 on 2008-03-25
josh@josh-laptop:~$ sudo grub
[sudo] password for josh:
Probing devices to guess BIOS drives. This may take a long time.
josh@josh-laptop:~$ 




so what do i do now to fix the xtnrl hd

---

### Post by bumanie on 2008-03-25
I am afraid that you will have overwritten windows mbr and that it won't boot. Before worrying about the external drive, you need to make sure your main computer is booting properly. By instructing grub to (hd0,0) you have probably made windows unbootable. You can exit the stage you are at now and reboot, but windows probably won't boot. Do you have a windows disk or not?  
Without going into details, I would personally run the external hard drive with something like qemu, but leave that until later. There are plenty of tutorials on the internet pertaining to that. First you need to make sure your computer is booting properly. Please don't go ahead with anything else until you answer whether you have a windows installation disc. It is important things are done in the correct order, with the correct command lines.

---

### Post by N1N31NCHN41L5 on 2008-03-25
my laptop is golden - it didnt execute the 0,0 so grub loads great, Ubuntu loads great an windows loads great, and YES i have recovery cd's for both ubuntu and windows

ok - now if you dont mind a little more - i also have a FULL Ubuntu install on the xtl including Grub - i booted laptop up and it is NOT seen.



THANK YOU so far

---

### Post by bumanie on 2008-03-25
I am glad that your machine did not execute the (h0,0) and that everything is fine with that computer.
As far as the external drive goes, the reason it will not boot is because grub is now pointed to your internal drive. As you know your laptop wouldn't boot when grub was on the external drive and grub was booting from it, (unless it was plugged in). If you don't have much information on the external drive, it would be best to format it and install an ubuntu .iso and boot it with an emulator such as qemu. Type qemu into a search engine and read its documentation. I have a usb pen and an external hard drive running via qemu. It is not the best emulation program but it stops grub conflicts arising and it does work. There are qemu versions for windows and linux. Good luck.

---

### Post by N1N31NCHN41L5 on 2008-03-25
> **bumanie said:**
> I am glad that your machine did not execute the (h0,0) and that everything is fine with that computer.
As far as the external drive goes, the reason it will not boot is because grub is now pointed to your internal drive. As you know your laptop wouldn't boot when grub was on the external drive and grub was booting from it, (unless it was plugged in). If you don't have much information on the external drive, it would be best to format it and install an ubuntu .iso and boot it with an emulator such as qemu. Type qemu into a search engine and read its documentation. I have a usb pen and an external hard drive running via qemu. It is not the best emulation program but it stops grub conflicts arising and it does work. There are qemu versions for windows and linux. Good luck.

ok , nub question here, what im looking for is a way to put Ubuntu on a ext HDD - what i did on this one. it has ful ubuntu istall with grub. I want to be able to take it to a friends house and run Ubuntu off of it on their computer. is that possible???

---

### Post by forrestcupp on 2008-03-25
> **N1N31NCHN41L5 said:**
> ok , nub question here, what im looking for is a way to put Ubuntu on a ext HDD - what i did on this one. it has ful ubuntu istall with grub. I want to be able to take it to a friends house and run Ubuntu off of it on their computer. is that possible???

Probably not, unless they have GRUB installed, too.  GRUB sets itself up in the MBR then gets its settings from the hard drive you installed Ubuntu on.  So they have to have GRUB in the MBR and whenever the external hard drive is unplugged, GRUB would give them an error since it won't be able to find its settings.

Edit:
Evidently, you can do it, and [here](http://ubuntuforums.org/showthread.php?t=678146&highlight=grub+usb+external+drive) is how.  You'll have to put grub on the mbr of the external and set his computer to boot from usb.

---

### Post by N1N31NCHN41L5 on 2008-03-25
ThanX to All for their help - if anyone ever figure a way out to run Ubuntu off a ext HDD without installing a grub on someone else's comp PLEASE let me know. My laptop is working again and I am happy.....

---

### Post by forrestcupp on 2008-03-25
Look at the link in my edit.  It shows you how to do it.  That link shows you how to install grub on your external drive's MBR.  If you do that, you just need to set a computer's bios to boot to usb 1st and it will load up grub on the external.

---

### Post by N1N31NCHN41L5 on 2008-03-26
MBR???
The install showed that it installed grub onto the external drive but even with bios at usb first it wont load  up????

---

