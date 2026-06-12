---
title: "test debian"
date: 2012-08-22
forum: Any Other OS
---

### Post by amrosama77 on 2012-08-22
Hello All,
I have win 7 on my internal hard disk
and ubuntu 12 on my external hard
can I make 40G partition on my external hard to install debian on it to test it, if yes

How to do this without killing my current system or my booting :confused:

Thank you all,

---

### Post by Laiquendi on 2012-08-22
Do you have your external drive's system available in GRUB or do you have to boot from it to start Ubuntu?
Do you have this external drive connected all the time?

In my opionion normal install should work just fine, after updating grub (if you have your external drive included in it).

---

### Post by amrosama77 on 2012-08-22
sorry I don't understand a lot of what you said

but I attache my external to be able to see the ubuntu boot menu and open ubuntu then I keep it attached all the time ,other wise I will not see it and will just open win7

so what is your advice...?

---

### Post by NikTh on 2012-08-22
Hi , 
ok it seems that you have Grub bootloader installed on Ext.HDD. 
When you install Debian , then Debian's grub will replace the current in Ext.HDD . 
You must know that Debian's installer is not so user friendly as Ubuntu's. 
It would  be an extra "safety valve" , if you could remove your internal HDD from Pc , before installation process begin. 
Thanks.

Edit: Take a look at this fresh thread --> [http://ubuntuforums.org/showthread.php?t=2042751](http://ubuntuforums.org/showthread.php?t=2042751)

---

### Post by amrosama77 on 2012-08-22
in this case I prefer not to do it ,as I can't lose my win7 for work reasons :(

thank you for the advice,

---

### Post by coldcritter64 on 2012-08-22
With the Ubuntu install on the external and Windows on the internal, yes you can add a debian setup on the external (provided sufficient space exists).

A **safety tip** is to physically disconnect the internal drive data cable (disable it) to fully protect the Windows MBR and install. 

You don't need to do this if you are very careful where you write the bootloader to. In fact you may not need to even write a bootloader with the debian installer as running the "sudo update-grub" command from Ubuntu will "see" the debian install and kernel images and list them in the grub menu.

---

### Post by amrosama77 on 2012-08-22
Do you mean that I can install debain without booting and then run boot repair from ubuntu and all done :KS ?

---

### Post by coldcritter64 on 2012-08-22
> **amrosama77 said:**
> Do you mean that I can install debain without booting and then run boot repair from ubuntu and all done :KS ?
Basically, yes. The update-grub command updates the grub menu already installed (on the external when it is booted) and will detect other linux systems installed on a scanned drive and add them to the listing (including the internal windows install if connected, will remove the windows listing if disconnected when scanned).

Physically disconnecting the internal windows drive protects your current bootable setup "absolutely", MBR and install etc, from any mistakes made while using the debian installer... very easy to do.. :smile:

---

### Post by amrosama77 on 2012-08-22
I can't do this ,it's a new labtop and I can't open it or will lose my warranty ,any other solution...?

---

### Post by coldcritter64 on 2012-08-22
> **amrosama77 said:**
> I can't do this ,it's a new labtop and I can't open it or will lose my warranty ,any other solution...?
With the Debian installer and the fact you already have grub on the drive you are wanting to install Debian to, you **do not** need to write anything to the MBR of ANY of the drives.

You will likely need to use the text installer and/or the advanced settings to tell Debian to NOT write out the bootloader to disk. In other words you need to familiarize yourself very well with the Debian installer to do this safely (as you can't physically protect the Windows install).

Only other suggestion I have is  if you have sufficient external storage is to clone/copy a complete windows install (can even be done with tools like dd in a live cd terminal) to ensure your data prior to any attempts you may make. Backing up to this extent is cumbersome but a smart move when attempting partitioning/installing like you originally posted. Cheers.

---

### Post by amrosama77 on 2012-08-22
Okay,

So what about the following steps:
1. make a new partition on my external witch is 40G (i don't have any other partition with this size not on the internal or external drives)
2. run debain from my flash key
3. start the install (advanced)
4. install on the 40G partition without booting loader

???? 

is this steps is okay?
am I able to do this steps?

---

### Post by coldcritter64 on 2012-08-22
> **amrosama77 said:**
> Okay,

So what about the following steps:
1. make a new partition on my external witch is 40G (i don't have any other partition with this size not on the internal or external drives)
2. run debain from my flash key
3. start the install (advanced)
4. install on the 40G partition without booting loader

???? 

is this steps is okay?
am I able to do this steps?

**First Step**: (can't emphasize this strongly enough). _BACKUP/CLONE YOUR WINDOWS drive to an image file on external media. Compression of the image file can be used, I don't do so personally, that is, my dd image files are the same size as the cloned drive (complete image at the device level, MBR including partition table, OS and any storage partitions).

Rest of your steps seem OK, next time you boot after completing the install you will need to go into Ubuntu and run "sudo update-grub", reboot. There should now be some Debian entries in the bootloader menu. 

I have noticed in the past doing this way the menu can get messy with the debian entries, I have found installing the grub-pc package is necessary to maintain the grub.cfg file in Debian, just don't let it write to the MBR **ever** and after updating the kernel in grub in Debian, boot into Ubuntu and run "sudo update-grub" to have it detect the new grub.cfg from Debian to keep the Debian entries tidy.

I should note: the Debian installer, to do this work, is vastly different to the Ubuntu one used and is very verbose in the Advanced mode I've always used with multibooting Linux distros. Check it out very carefully before making any changes to an important machine.

---

### Post by amrosama77 on 2012-08-22
thank you Sir, so step 0 will be >>_BACKUP/CLONE YOUR WINDOWS drive to an image file on external media. 

sorry I just ignore this as I don't know how to do it ,can you give me a link to some steps to do it :D

---

### Post by blackmail on 2012-08-22
make a bootable stick this will work fine i think, for testing purposes, the stick can hold info and it will boot very fast.

---

### Post by blackmail on 2012-08-22
also you could install the distro on a computer if you have one spare and copy the hdd, if it is not to big using the dd command, to the external drive and configure booting from usb before the hdd installed in the computer.

---

### Post by coldcritter64 on 2012-08-22
> **amrosama77 said:**
> thank you Sir, so step 0 will be >>_BACKUP/CLONE YOUR WINDOWS drive to an image file on external media. 

sorry I just ignore this as I don't know how to do it ,can you give me a link to some steps to do it :D
I use an external sata dock (takes laptop to full size sata drives), use a live cd/usb, Ubuntu will do fine.
Open a terminal, ```
sudo fdisk -l
``` that is a lower case L, and no password needed from a live environment, to identify the drive device numbers.

dd command

```
sudo dd if=/dev/sda of=/media/<device-uuid>/<path-to-image-file>/<filename>.img
```/dev/sda would be your Windows drive complete including MBR, partition tables, and any partitions and filesystems. A bit by bit, block by block, image stored into a file on external media. Your storage drive will likely be mounted automatically with the Ubuntu live cd, so I have used <device-uuid>. As far as I'm aware that is how the live cd mounts your storage drives. I have also used "<path-to-image-file>/<filename>.img", if you wish to save to an existing storage drive, alter where necessary to suit your situation.

to restore with dd in the event of a mishap, from the live cd environment and in terminal,
```
sudo dd if=/media/<device-uuid>/<path-to-image-file>/<filename>.img of=/dev/sda
``` **Warning:** this command completely overwrites the internal drive from start to finish, from the previously made image file.

**Edit: **note the image file created is exactly the same size as /dev/sda, and will be a huge file. Compression can be used to get more manageable sized backups. I don't use compression personally, but the above command could be piped to gzip etc. and the extension changed to suit.

---

### Post by amrosama77 on 2012-08-22
woooooooooooow looks great thank you so much 

so let's review the steps and get more familiar (talking to me I think :D )

0. back your internal using your last great post
1. make a new partition on my external witch is 40G ,during the debain instillation I will be able to see the partitions size or not?
2. run debain from my flash key ,boot from debain flash live to install
3. start the install (advanced), am I be able to answer all the advanced installation questions? is there any list of default answers?
4. install on the 40G partition without booting loader, any idea about the check box which I have to check or to un-check to do this step?

Thank you all,

---

### Post by coldcritter64 on 2012-08-22
> **amrosama77 said:**
> woooooooooooow looks great thank you so much 

so let's review the steps and get more familiar (talking to me I think :D )

0. back your internal using your last great post
1. make a new partition on my external witch is 40G ,**during the debain instillation I will be able to see the partitions size or not?**

2. run debain from my flash key ,boot from debain flash live to install

3. start the install (advanced),** am I be able to answer all the advanced installation questions?** **is there any list of default answers?**
4. install on the 40G partition without booting loader, any idea about the check box which I have to check or to un-check to do this step?

Thank you all,
1. The advanced Debian installer (text) I use to do this can do full partitioning and is very powerful (read hard to use, not friendly at all).

2. No live desktop with the debian installer (net-install) I've used before, text/menus etc. (ditto brackets in 1.) There is a graphical installer but I don't use it, I tend to dig into the menus and settings during the install, particularly when setting up a dualboot linux setup.

3. I can not say, but I would advise some practice installs, maybe to another usb stick (8GB would be heaps big enough- for training).
I would only advise you try it when you can identify the various devices, be they internal, usb, external eg sata, from the Debian installer (practice from within the Ubuntu terminal and live cd to to get familiar with device terminology etc) and when you get used to the menu system of the installer (very keyboard centric).

There is a graphical Debian installer, though I'm not sure if this is possible to do this type of set up with it. The previous suggestion of installing a full debian setup to a usb stick is a good one ([blackmail]("http://ubuntuforums.org/member.php?u=680912") post 14).

4. Buried deep in the menus of the text installer or in the advanced settings of the partitioner in the graphical installer (if there; as noted above I use the text installer mostly)

**My advice** would be use the Debian usb stick installer to install to another usb stick, for practice, several times if necessary to become familiar with what the Debian installer is like. Though not on a critical machine.  Or if mistakes are made then the image process I mentioned earlier can help if you can only use the laptop you mention.

---

### Post by vandorjw on 2012-08-22
@OP;

What laptop model do you have?
In my old Inspiron 1520 I could disable my internal HDD. I didn't have to open it, but it would be disabled via BIOS. No need to take the hard drive out.

@OP:
As well, did you know that debian is not depended on the computer that you installed the system on. You can install on computer #1, then attach the hard drive to computer #2 and it will usually work just fine.

If have a second computer on which you are able to physically disconnect the hard-drive, then installation via that machine is possible as well.

If you do not have a second machine, then you can always check if you are able to disable your internal HDD via bios. To enter the BIOS of your laptop, try pressing the F2, F10, F11, or Delete key on system startup.

Cheers - cc7:guitar:

---

### Post by amrosama77 on 2012-08-23
my labtop model
is HP Pavilion g6

---

### Post by amrosama77 on 2012-08-23
0. I created the img file
1. make a new partition on my external witch is 40G , done in ubuntu
next steps will be
2. run debain from my flash key ,boot from debain flash live to install
3. start the install (advanced), 
4. install on the 40G partition without booting loader, 

as I have img file for my internal hard then I think I will go directly without any practice :D wish me luck

---

### Post by coldcritter64 on 2012-08-23
> **amrosama77 said:**
> 0. I created the img file
1. make a new partition on my external witch is 40G , done in ubuntu
next steps will be
2. run debain from my flash key ,boot from debain flash live to install
3. start the install (advanced), 
4. install on the 40G partition without booting loader, 

as I have img file for my internal hard then I think I will go directly without any practice :D wish me luck

It is still possible to "nuke" your Ubuntu install on the external with this if any partitioning of the external drive goes wrong. Backing it up in the same manner would give you full coverage, depends on how important your Linux data is, maybe just a backup of your user data (home partition files/folders and a reinstall if a problem does occur).

Any partitioning should be done with as much backup coverage as possible, imo. You learn caution fast after mistakes made with installers/partitioners, particularly if advanced settings are being altered ;)

Point 4. should read as "install on the 40G partition without** installing** the bootloader to the MBR" (correction only for clarity)

Good luck, though practice does "make perfect" :smile:

---

### Post by mastablasta on 2012-08-23
why such complications. by installing debian to another partition to external drive the only thing that could happen to internal drive is that it's MBR gets overwritten by grub. which is an easy fix as long as you have original windows CD (run recovery conolse and fixmbr command [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)).
 
 
i am not sure if windows recovery disk work.

---

### Post by amrosama77 on 2012-08-23
So 
Now I try to install debian but it looks like it need to be installed using the CD-Rom, it didn't reconize the flash drive,

this was after choosing the language and the country !!!

so I think I will do CD but this is wired I think ?!!!

---

### Post by coldcritter64 on 2012-08-23
> **mastablasta said:**
> why such complications....
Installing Debian to the windows partition by accident, unlikely but possible, and potentially disastrous. The Debian installer is in use and if installation is to the wrong device -- ouch. Simpler is to disable or disconnect the internal drive, it has been discussed but doesn't seem feasible.

@ OP, yes the Debian installer is quite different, hence my suggestion to "practice" before relying on it.

---

### Post by uRock on 2012-08-23
ASking for help with Debian. Moved to ***Other OS/Distro Talk***.

---

### Post by amrosama77 on 2012-08-23
Okay,

Now I make debain CD and dboot from it and do the installation

without boot guru 
so the situation now is as follows:

when I turn on my lab without the external attached I just open my win7 (great)

when I attache the external and open the lab I see the boot menu with no option for debain at all, only ubuntu as perivuse 

but debain is installed as the debian 40G partition have now folders like /bin /sys /boot

so what to do now ???

---

### Post by amrosama77 on 2012-08-23
I guess I have to run boot repair from ubuntu ,but i will wait your advice first :)

---

### Post by coldcritter64 on 2012-08-23
> **amrosama77 said:**
> ...

but debain is installed as the debian 40G partition have now folders like /bin /sys /boot

so what to do now ???
Reboot into the Ubuntu install, open a terminal and run the command.
```
sudo update-grub
```If your debian install was done correctly the kernel images in debian should be detected by grub in ubuntu. Reboot to the grub menu screen again and check for debian entries and if there try booting into one.

---

### Post by amrosama77 on 2012-08-23
THANK YOU,
here is the result:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Debian GNU/Linux (6.0.4) on /dev/sdb4
done

it looks like debian is detected but I don't know why I have 2 win 7, I test both of them and both of them worked fine !!!

I will restart now and see if I can login to debian or not

Note: I use the same 5G swap partition for both ubuntu and debain I don't know if this will  work fine in case of hibernating both systems or what :D

---

### Post by amrosama77 on 2012-08-23
The situation now is as follow:

ubuntu menu have 2 win7 items and 2 debian items !!!

any way when I login to debain it didn't accept my credintails (username & password ) which I use during the setup !!!!

any advice ?!!

---

### Post by coldcritter64 on 2012-08-23
> **amrosama77 said:**
> THANK YOU,
here is the result:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Debian GNU/Linux (6.0.4) on /dev/sdb4
done

it looks like debian is detected but I don't know why I have 2 win 7, I test both of them and both of them worked fine !!!

I will restart now and see if I can login to debian or not

Note: I use the same 5G swap partition for both ubuntu and debain I don't know if this will  work fine in case of hibernating both systems or what :DWindows is being detected on 2 partitions, I'm not entirely sure, but I think 1 of them is like a boot partition - sorry but I can't explain that in any more depth.

Otherwise that is looking quite good so far.

Note: if you use hibernation on 1 system and then boot to another system that uses the same swap partition, the hibernation file from the first system can be overwritten/damaged, something to keep in mind to avoid.

Edit: re post 31. It has been quite a while since I've used a Debian install, hopefully someone can talk you through the debian login repair process (though I suspect you may get better support on the [[COLOR=Blue]debian forums[/COLOR]]("http://forums.debian.net/") for such an issue).

Edit 2: when adding the credentials in the installer did you by any chance use capitalization or unusual characters in your username? If you did, a suggestion is to try and log in without any capitalization (use all lower case) in the username.

---

### Post by amrosama77 on 2012-08-23
No I didn't use any capital or special characters :(

I will try to get debian support Thank you so much,

---

### Post by amrosama77 on 2012-08-25
I re-install the debian and every thing is okay now, thank you so much

---

