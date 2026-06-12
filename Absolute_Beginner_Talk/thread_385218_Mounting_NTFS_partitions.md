---
title: "Mounting NTFS partitions"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-15
I've been reading / following the instructions at 
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

to enable me to read the NTFS partitions on my drives and got to step 3:

It looks like it's working 
'Reading package lists... Done'
'Building dependency tree... Done'

and then stops with the error (tried to stick in a small screen shot of the error . . .) 'Couldn't find package ntfs-config'

What next? Where do I go from here?

---

### Post by Kobalt on 2007-03-15
The HowTo you followed is for reading and **writing** to NTFS partitions, not simply reading (that Ubuntu can do without installing anything). What do you exactly want to do ?
Here is [some help]("https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") on mounting and reading partitions.

---

### Post by Big-Wayne on 2007-03-15
I used the following reference to mount my windows drive;
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")
Using ntfs-3g allows you to mount the windows partition/drive on booting.

---

### Post by lwalper on 2007-03-15
I've got 4 partitions, one of which is the Linux. On the same drive, a partition containing the Win2k installation (NTFS). On another physical drive two partitions (1) 40Gb FAT32 (2) 160Gb NTFS.

I can't see anything other than the Linus partition in my file manager. I'd like to be able to read the files from the other partitions.

---

### Post by maniacmusician on 2007-03-15
did you perform the crucial "sudo apt-get update" and "sudo apt-get upgrade" commands? did they give you any errors?

basically, this is what the instructions are having you do:
- Step 1 tells your computer where to look to download packages. It says "here's a location you can download from. Contact it to find out what packages you can get from it".
- Step 2 first does the key-exchange thing so that both locations are okay with talking to each other. Then, the two apt-get commands tell your system to check the newly added locations in /etc/apt/sources.list to see what packages are in there and to upgrade if you need to.

So there are a couple of possibilities of things that went wrong. One is that you didn't add a correct location to /etc/apt/sources.list (first step). another is that you didn't issue the sudo apt-get update command. 

So, which is it?

PS: It must seem like I'm stalking you or something! I always seem to come upon your threads here and in the Cafe.

---

### Post by lwalper on 2007-03-15
Well, if you're stalking me, keep it up. Your input has been not only helpful but encouraging.

From #1 I added
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all

From #2 I issued the following:
sudo apt-get update
sudo apt-get upgrade

which I assume upgraded the OS (it downloaded and installed a bunch of files -- 130 or so)

I did not do
wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

Since it was located above the upgrade where I was instructed to "First do this ..." I neglected to do that. Maybe that's the problem?

---

### Post by lwalper on 2007-03-15
Nope, tried that too. No success finding the package file:///home/leslie/Desktop/Screenshot-leslie%40leslie-desktop%3A%20~-Desktop-ntfs-3g-1.0.png

---

### Post by maniacmusician on 2007-03-15
Remember, you have to do apt-get update again after you add the key. If you did this and still no dice, that means something is wrong...

I made a virtual machine of Edgy a few days ago just for support purposes (I'm testing Feisty now) so I'll go and try to replicate this problem there and tell you how it goes.

---

### Post by maniacmusician on 2007-03-15
Okay, it works perfectly fine for me, so you must have done something wrong. I suspect that it might be in Step 1. It's possible that you didn't add the right entry (though you probably did, if you can copy and paste), or perhaps you didn't put it in the right place.

When you opened /etc/apt/sources.list (with the command **gksu gedit /etc/apt/sources.list**), were there other entries in there already? There should have been lots of lines similar to this one but pointing to different URLs, and you were supposed to add your line to the rest.

After that, you have to add the key, and **then perform "sudo apt-get update && sudo apt-get upgrade" after adding the key**. 

Then, when you do "sudo apt-get install ntfs-config". it should want to install the package "ntfs-config" along with a couple of other packages as well.

---

### Post by lwalper on 2007-03-16
OK, so, I just went through the steps, beginning with #2 "first upgrade your system." Everything goes well until It hits the last line re: fetch NTFS stuff

#1, checked the repository entry, copied/pasted from the site and saved the sources.list file.

#2 Ran wget  [http://flomertens.free.fr/ubuntu/givre_key.asc](http://flomertens.free.fr/ubuntu/givre_key.asc) -O- | sudo apt-key add -

Seems to go OK.

Ran sudo apt-get update and receive the following

leslie@leslie-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                        
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                     
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg               
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US    
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                     
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release

Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release [739B]                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                               
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                   
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages
Fetched 933B in 1s (595B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


There's an error under Get:4 and then the errors listed at the end.

---

### Post by givré on 2007-03-16
There is no error, just a warning about the wine repo.
Your ntfs-3g repo should be ok.
Just run :
 ```
sudo apt-get update
sudo apt-get install ntfs-config
```

---

### Post by lwalper on 2007-03-16
OK, thanks. That seemed to work --- or at least run through the installation (or whatever it did). I still don't see my other partitions. Does it need a reboot?

---

### Post by givré on 2007-03-16
lwalper, did you run ntfs-config ?

---

### Post by lwalper on 2007-03-16
Thanks for your help.

Yes I did run ntfs-config, and have since restarted the computer. Still no partitions. After restarting I have now re-run ntfs-config and did get a dialog this time that did not appear the last time -- says that a partition has been identified. I have named the mount point and selected the read/write enable option. I do now have access to that partition -- it is the second partition on my primary drive (where Win2K is installed).

How do I find the others? There is a second drive with two partitions, a 40Gb FAT32 and a 160Gb NTFS. I'm not seeing those.

---

### Post by Griffiss on 2007-03-16
A very simple procedure which allowed me to read my NTFS drive.

(From taurus' post at [http://ubuntuforums.org/showthread.php?t=384314](http://ubuntuforums.org/showthread.php?t=384314))
> 
Edit /etc/fstab
```

gksudo gedit /etc/fstab
```
and add this line to the end of it.

```

/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
[Note that you will have to input the logical name of *your* partition instead of 'hdb1' - Griff]

Save it. Then, create a new mount point and mount it.

```

sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Griffiss on 2007-03-16
forgot to say - find the logical name for your partition by inputting:```
sudo fdisk -l
```

---

### Post by Jormanks on 2007-03-16
and when one partition isn't recognized by ubuntu?

---

### Post by lwalper on 2007-03-16
So, I ran sudo fdisk -l and got this information:


Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3987    32025546    7  HPFS/NTFS
/dev/hda2            3988        9762    46387687+  83  Linux
/dev/hda3            9763       10011     2000092+   5  Extended
/dev/hda5            9763       10011     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

Disk /dev/sda: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         983      251632    6  FAT16

*******************************************************
What's next? The drive I need to access is the 200Gb with two partitions -- one 40Gb FAT32 and one 160Gb NTFS.

---

### Post by Griffiss on 2007-03-16
Hmmm,

Your hdb1 says it's an OnTrackDM6 system. You may have to do something different than what you would do for NTFS (FAT32 requires a different treatment as well). As I said, the method I give above is just what I did to read my NTFS drive. I'm new to ubuntu myself so can't help in depth!

Have a look at [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html) and perhaps [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

....or google?

---

### Post by lwalper on 2007-03-16
I have re-formatted the FAT32 partition to NTFS. Now when I run 'sudo fdisk -l' I get the following:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3987    32025546    7  HPFS/NTFS
/dev/hda2            3988        9762    46387687+  83  Linux
/dev/hda3            9763       10011     2000092+   5  Extended
/dev/hda5            9763       10011     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

**********************************
The 200Gb is the second physical drive with two NTFS partitions. In the file manager i can see hdb1, but it is "empty" and cannot be written to. I have run the NTFS configuration tool with no success in locating either the second partition or making the first writable.

---

### Post by lwalper on 2007-03-16
[QUOTE=lwalper;2309867]I have re-formatted the FAT32 partition to NTFS. Now when I run 'sudo fdisk -l' I get the following:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3987    32025546    7  HPFS/NTFS
/dev/hda2            3988        9762    46387687+  83  Linux
/dev/hda3            9763       10011     2000092+   5  Extended
/dev/hda5            9763       10011     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

**********************************
The 200Gb is the second physical drive with two NTFS partitions. In the file manager i can see hdb1, but it is "empty" and cannot be written to. I have run the NTFS configuration tool with no success in locating either the second partition or making the first writable.

The reply above says I need to "input the logical name of *your* partition instead of 'hdb1'" What ids the name of my partition? I don't know what OnTrackDM6 is. Win2K tells me it's an NTFS partition.

---

### Post by maniacmusician on 2007-03-17
> **lwalper said:**
> [QUOTE=lwalper;2309867]I have re-formatted the FAT32 partition to NTFS. Now when I run 'sudo fdisk -l' I get the following:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3987    32025546    7  HPFS/NTFS
/dev/hda2            3988        9762    46387687+  83  Linux
/dev/hda3            9763       10011     2000092+   5  Extended
/dev/hda5            9763       10011     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

**********************************
The 200Gb is the second physical drive with two NTFS partitions. In the file manager i can see hdb1, but it is "empty" and cannot be written to. I have run the NTFS configuration tool with no success in locating either the second partition or making the first writable.

The reply above says I need to "input the logical name of *your* partition instead of 'hdb1'" What ids the name of my partition? I don't know what OnTrackDM6 is. Win2K tells me it's an NTFS partition.
sorry, which partitions are  you trying to read again? hda1 and hdb1?

and you already got access to hda1?

I think the OnTrackDM6 thing is what's messing with the config. I have no clue what that is....maybe some fancy  hardware-based encryption? care to google it?  I would do it, but I'm dead tired and may just keel over if I don't go to bed now. 

see you tomorrow

---

### Post by david_kt on 2007-03-17
Just issue below two command to read your ntsf drive.

 Make mount point:

[INDENT]sudo mkdir /media/windows[/INDENT]

And then followed by:

[INDENT]sudo mount /dev/hda1 /media/windows -t ntsf -o nls=utf=8,umask=0222[/INDENT]

after that browse to media/windows, your partition should be there.

Regards,
DK

---

### Post by lwalper on 2007-03-17
Well, that did change something. I now have a folder in the file browser named /media/windows as well as /media/hdb1 --- still can't read either one. Hmmm??

---

### Post by Griffiss on 2007-03-17
The sudo mkdir /media/windows command is what made the folder appear - it means 'make directory'.

I think this OnTrackDM6 thing is confusing things, because with NTFS, it should say (as far as I know) HPFS/NTFS instead. I did a google search for it and not much comes up - a lot of obscure-looking sites, many in chinese...

Can you post your /etc/fstab file?```
gksudo gedit /etc/fstab
```to see what it looks like.

---

### Post by lwalper on 2007-03-17
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=75c638a4-101b-4e0b-a620-5759911657c1 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=62c34fc8-8017-4525-ab40-5bd39120f2e6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/D\040160Gb ntfs-3g defaults,locale=en_US.UTF-8 0 0

****************************
The mount point for the partition I *can* read is the 160Gb. That's not actually the  partition that is being read (though, at the time of naming the mount point I thought it would be) so try not to get confused by that. That mount point is actually looking at the second partition (31Gb or so) on the primary drive. An icon has actually appeared on the desktop pointing to that partition. Can I rename that mount point to reflect where it is actually looking?

It is the secondary drive and partitions that I cannot read --- the hdb1 drive.

---

### Post by Griffiss on 2007-03-17
You need to sort out the OnTrackDM6 business - I don't think you can treat it the same as NTFS. Have a look at this:

[http://bbs.archlinux.org/viewtopic.php?pid=119602](http://bbs.archlinux.org/viewtopic.php?pid=119602) (ctrl+F and find 'ontrackdm6')

and this:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2003-12/4585.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2003-12/4585.html)

I think they'll get you closer, but the sites are quite dated.

Their instructions are to add 'hdb=remap63' to the kernel line of the grub.conf file. I did a search for this file on my system and the closest thing that comes up is 'kpkg_grub.conf' which I'm not sure is the same, but it does have a line that says: grub_kernel_partition="" but also a line that says: kernel_boot_options="root=/dev/hda2"

So I'm thinking that you need to add 'hdb=remap63' to one of these lines, in order to make your hdb partitions visible to the kernel. You should check with someone more experienced first though....

---

### Post by dstew on 2007-03-17
The disk you are trying unsuccessfully to mount, hdb, has an on-disk disk manager program called OnTrack. The sectors are shifted by 63 from where linux expects to find them. Linux can still mount the partitions on this disk, but you need to add an option to the kernel boot line in your /boot/grub/menu.lst file. As Griffiss said, the option is:

hdb=remap63

Here is a nice link explaining a bit more about the OnTrack disk manager:

[http://www.linux.com/howtos/Large-Disk-HOWTO-8.shtml](http://www.linux.com/howtos/Large-Disk-HOWTO-8.shtml)

You can get rid of the disk manager after you mount the partitions, if you want to.

---

### Post by david_kt on 2007-03-17
> **lwalper said:**
> Well, that did change something. I now have a folder in the file browser named /media/windows as well as /media/hdb1 --- still can't read either one. Hmmm??

Sorry I make a typing error in previous post:

[INDENT]sudo mount /dev/hda1 **/media/windows** -t ntsf -o **nls=utf=8**,umask=0222[/INDENT]

It should be:

[INDENT]sudo mount /dev/hda1 **/media/windows/ **-t ntsf -o **nls=utf8**,umask=0222[/INDENT]

Hopefully it solves your problem.
By the way, when did you create /media/hdb1? It is a folder, for mount point, not the partition itself.

Regards,
DK

---

### Post by david_kt on 2007-03-18
After I read again carefully this thread, seems like it is not ntfs file system mounting issue, but OnTrackDM6  file system.

And I have check the thread, you have created /media/hdb1 from Griffis instruction, and /media/windows through my instruction. You can delete either of this folder as you only need one mount point.

And the partition you want to mount is /media/hdb1, I thought previously it was /media/hda1 as that is the only NTFS partition you have.

For OnTrackDM6 file system, I have no experience before, but through google, I found this instruction may be could help you:

[http://ramses.smeyers.be/varia/OnTrackDM6/](http://ramses.smeyers.be/varia/OnTrackDM6/)

OnTrackDM6 in Linux

Use the following instruction to mount an type OnTrackDM6 partition in Linux.

/dev/hdc1   *           1        1653      833111+  54  OnTrackDM6

Adapt your bootloader and add the option hd<x>=remap63 for your kernel where x is your disk.

Now reboot your system and the partition is visibale as (for example)

/dev/hdc1   *           1         826      832576+   6  FAT16

Mount this partition as read-only and copy your data from it

Regards,
DK

---

### Post by lwalper on 2007-03-18
Hey all,

With all this information about OnTrack I may have been premature, but it struck me that the large disk LBA manager was what was causing the problem --- so . . .

I archived everything off the primary 80Gb drive, reformatted, repartitioned (30Gb on C:\ for programs -- the remainder on D:\ for data) with Win2K SP4 with all the updates. Am now in the process of archiving the 200Gb drive and plan on partitioning / installing Ubuntu on that drive with about 30Gb for programs and 170Gb for data. If Linux will support the large drive that should eliminate the OnTrack generated problems.

I needed to do some spring cleaning anyhow! I'll print off all this good content and hopefully get things up and running like they should in a couple of days. Ubuntu should have no problem reading the Windows D:\ drive NTFS data. Instead of running a VMWare environment I'll just dual-boot into Windows when I need the Adobe CS2 stuff. I haven't really found a suitable replacement for InDesign -- and Photoshop's hard to beat.

---

### Post by david_kt on 2007-03-19
I am not sure about lba, but I just wanted to inform you about Adobe Photoshop. It was reported could be run on linux/ubuntu:

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

If you want to do clean install, you could try to set up your wine using winetools first:

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

but make sure you install old wine, version Wine versions 0.9.1, 0.9.2,0.9.3 up to 0.9.5. Because for later seems there is some problems with winetools set up.

Or, if you want an easy way, you could try crossover office which is commercial application to help you setup wine:

[http://www.codeweavers.com/compatibility/browse/name?app_id=8](http://www.codeweavers.com/compatibility/browse/name?app_id=8)

Regards,
DK

---

### Post by lwalper on 2007-03-22
After re-partitioning/formatting/installing both Win2K and Ubuntu. Win2K is on hda1 (30Gb) with a second primary partition on hda2 (NTFS). The Ubuntu installation is on a second drive (hdb1 (30Gb etc3), with a second primary partition (150Gb NTFS) on hdb2 and a 2Gb Linux swap partition on hdb3. I now have the following:

------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=62ec8b86-1074-4984-abab-7f1407211d63 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=62C0B453C0B42EE3 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6EA82D40A82D07E3 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb2       /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=129589f0-13e0-4d9c-b0b4-9d8643245458 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---------------------------------------------------------------

I can read all drives, but cannot write to any of the NTFS partitions. Using the etc3 formatting of the large drive seems to have eliminated the need for any extra large disk support so OnTrack is no longer an issue.

How do I set the drives to write as well as read?

---

### Post by david_kt on 2007-03-23
To write ntsf, you need to install ntsf-3g. Please follow instruction in this link:

[http://www.ubuntuforums.org/showthread.php?t=217009&page=1](http://www.ubuntuforums.org/showthread.php?t=217009&page=1)

DK

---

### Post by lwalper on 2007-03-23
OK, that worked. For some reason the NTFS partition created by the Ubuntu installation was not readable by ntfs-3g. I rebooted in Windows, formatted that recognizable but Win2K unreadable partition (using the Windows disk manager) into a NTFS partition. Restarted Ubuntu and -- there it was on the desktop with the other two NTFS partitions.

I just ran the NTFS configuration tool (ntfs-3g) GUI System tools -- it now read/writes without a problem.

Thanks a bunch!!

---

