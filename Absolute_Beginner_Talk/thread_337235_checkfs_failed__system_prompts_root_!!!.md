---
title: "checkfs failed / system prompts root !!!"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-12
Hi,
Everytime at start up, before I get into the login screen, I get the following error and it directly prompt me to root,where when I type "shutdown now" and it get into the login screen and system works normally. Each time getting this error is annoying and I want to resolve this issue with your help. Here is the error on the black screen so I type by hand:

[I]fsck.ext3	Unable to resolve 'UUID=9617953f-c14f-462b-8ab5-2bfceddbf284'			fsck died with exit status 8								
File system check failed
/var/log/fsck/checkfs
Please repait the file system manually
A maintanence shell will be started
Control-D will terminate this shell and resume system boot
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found
root@username:~#
[/I]
then if I type shutdown now, I get into login screen and evrything seems to wok fine.

**You may ask after when this happened????**
Here is what I did before this error occurred:
I reinstalled ubuntu on different partition. Originally I had ubuntu in dev/sda5, while dev/sda1 was windows and sda3 was extra linux partition left when I shrinked dev/sda1 and formatted to linux partition to become /dev/sda3. I made a mistake in linux (long story) so I decided to install ubuntu on sda3, and I have been using this ubuntu since then. After I tranferred my files from /sda5 ubuntu, I decided to reformat /sda5 naturally. Attached is the current partition (screenshot.png).

Partition shows that linux swap is /sd6 (as if left from the previous ubuntu install, it is just nect to sda5). Should I make a new swap next to sda3? How much size should I give, 600 mb seems small.
thank you,
findik

---

### Post by hal10000 on 2007-01-12
Next time when you are directed to the root shell. look into the file /var/log/fsck/checkfs. you can do thi by typing: cat /var/log/fsck/checkfs

There you see the reason why th file system check was failing and on which partition it failed.

As an examle, here is mine:
```

cat /var/log/fsck/checkfs

Log of fsck -C -R -A -a
Wed Jan 10 15:16:01 2007

fsck 1.39 (29-May-2006)
/dev/hdd1: clean, 53833/5248992 files, 8550939/10486420 blocks
/dev/hda3: clean, 245809/979200 files, 1664083/1955913 blocks
/dev/hdd5: clean, 1205/4816896 files, 3674210/9616902 blocks

Wed Jan 10 15:16:01 2007

```

You see in this example, everthing is clean.

To verify what happened, post this output. (I suppose it's something on your /dev/sda3 Partition.)

---

### Post by findik1 on 2007-01-13
Here is the output:
Log of fsck -C -R -A -a
Fri Jan 12 17:55:18 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 6849 files, 1060112/1278917 clusters
fsck.ext3: Unable to resolve 'UUID=9617953f-c14f-462b-8ab5-2bfceddbf284'
fsck died with exit status 8

Fri Jan 12 17:55:21 2007

---

### Post by hal10000 on 2007-01-13
We need additional informations from some commands/files:
It's better to gain these infos from a terminal window. Please post the outputs of these commands here (you can mark the outputs with your mouse and then paste them to your browser with the middle mouse key)

1. [COLOR="Red"]ls -l /dev/disk/by-uuid[/COLOR]
2. [COLOR="Red"]cat /etc/fstab[/COLOR]
3. [COLOR="Red"]sudo fdisk -l /dev/sda[/COLOR]

4. [COLOR="Red"]gedit /boot grub/menu.lst[/COLOR] Here you should post everything between the following lines:
[COLOR="Red"]### BEGIN AUTOMAGIC KERNELS LIST [/COLOR]
[COLOR="Red"]### END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR]

I suppose something went wrong with allocation between UUID and partition names and we might have to fix this manually.

---

### Post by findik1 on 2007-01-13
1. total 0
drwxr-xr-x 2 root root 140 2007-01-12 17:55 .
drwxr-xr-x 6 root root 120 2007-01-12 12:55 ..
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 1B33-0A00 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 25aaea84-fb54-4d92-97aa-10410840e478 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 5ef0eb00-5ab2-4491-ba7d-d3b21e763938 -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 664C41F04C41BC15 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 c71d7c64-263d-4a81-b4e7-e22ff0799a60 -> ../../sda6

2.  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5ef0eb00-5ab2-4491-ba7d-d3b21e763938 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=664C41F04C41BC15 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1B33-0A00  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9617953f-c14f-462b-8ab5-2bfceddbf284 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=c71d7c64-263d-4a81-b4e7-e22ff0799a60 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


3.  
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            6658        7296     5125680   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            2551        4746    17639370   83  Linux
/dev/sda4            4747        6657    15350107+   5  Extended
/dev/sda5   *        4747        6576    14699443+  83  Linux
/dev/sda6            6577        6657      650601   82  Linux swap / Solaris
Partition table entries are not in disk order

4. Could not open the file /boot.

Thanks!

---

### Post by findik1 on 2007-01-13
PLease note that:

3. I notice that it says:
Partition table entries are not in disk order

4. it could not open at all.
thanks again

---

### Post by hal10000 on 2007-01-13
Sorry I've made a mistake in step 4. Here's the correct command:

gedit /boot/grub/menu.lst

---

### Post by findik1 on 2007-01-13
Here is the output:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5ef0eb00-5ab2-4491-ba7d-d3b21e763938 ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by hal10000 on 2007-01-13
This is the decisive prt in you /etc/fstab file, which causes the error:
> 
# /dev/sda5
UUID=9617953f-c14f-462b-8ab5-2bfceddbf284 /media/sda5 ext3 defaults 0 2


Change it to:
```

# /dev/sda5
UUID=25aaea84-fb54-4d92-97aa-10410840e478 /media/sda5 ext3 defaults 0 2

```

and it hopefully will be ok.

But there are some really curious things on your harddrive --->specially with your /dev/sda2 partition. Are you really sure it's a windows partition?
if so, then it may be somehow damaged. Try to get access to it. Is there important data on it?

---

### Post by findik1 on 2007-01-13
sda1 is the windows partition. sda2 is a ibm laptop default files, I guess, ibm put for recovery of the system, so in windows I dont have access to that drive also. I dont have any imprtant files in windows anyway.
So I edit with :
sudo gedit /etc/fstab  ?

---

### Post by hal10000 on 2007-01-13
Yes, edit with sudo gedit /etc/fstab (or better gksudo instead of sudo)

---

### Post by findik1 on 2007-01-13
ok it solved the problem! thank you very much!  Do you understand by any chance my partition output that GParted gives:
for example, why sda5 is still seen as "boot", under sda5 there is no linux or any files, since I formatted this partition. 
/sda3 should be main "boot" linux, since I re installed ubuntu there, I see /. /dev/.static/dev, what does this mean? Is linux scaw is in the correct place, sd6?
THanks again anyway you solved my main problem
best
findik

---

### Post by hal10000 on 2007-01-13
The boot-flag is only important for older windows (95,98,ME,2000) systems, under linux it's doesn't matter wether it is set or not.

I also wonder what the /. and /dev.static/dev is use for, but dont change it if it works.

btw, I'm almost sure, if you ever will use your recovery from sda2 your ubuntu will be destroyed. Those recovery systems usually clean up the whole harddisk and will (re-)install only your windows system. So, be careful.

And, last, I see that your windows partition is empty. Do you have no windows installation? If you install windows after you installed ubuntu, then you will also run into trouble if you do not prior backup your master boot record (mbr), because the windows installation procedure wipes out the existing boot manager without asking you. So you won't be able then to boot your ubuntu if you didn' backup your mbr (and resrtored it after windows installation.

---

### Post by hal10000 on 2007-01-13
Your ubuntu is stored in /dev/sda3, /dev/sda6 is your swap partition.

---

### Post by findik1 on 2007-01-14
./ /dev/static/dev occurred after I installed ubuntu under dev/sda3, while there was already a ubuntu on dev/sda5, but I could not login to ubuntu in dev/sda5, therefore I decided to new install into a different partition, sda3.

thanks for the advice regarding dev/sda2, maybe I should format it.

yes /dev/sda6 is swap, as it was from the previous install of ubuntu on /dev/sda5. My question was should swap be next to /dev/sda3 now, since ubuntu is there, but I assume it does not matter.
thank you for the clearing things.
best

---

### Post by findik1 on 2007-01-14
yes, windows looks empty but I checked and it is there! I can loginto windows. Laptop came with windows, I installed ubuntu after windows. 
In fact I can get into windows files from ubuntu since during ubuntu install, I made windows partitions as mounted. If you check attached png file you see that ibm_preload is my windows partition, I can get acces the files of windows, ibm_service is I guess it is the /dev/sda2, that I mentioned and sda5 is now free partiton I will be using as file storage.

---

### Post by findik1 on 2007-01-14
desktop screenshot is attached now!

---

### Post by findik1 on 2007-01-14
seems there was an stg in the attacment, I retry

---

### Post by findik1 on 2007-01-14
sorry images were not sent previously due to size limits. Now it should be OK.

---

### Post by Lil_Eagle on 2007-01-23
Thanks to this thread I think I can solve my problem.  I ran into the same error (different UUID) after installing Debian Etch.  The curious thing is that it's my home partition, which I told Debian to Keep (and it did).

I used a different user name so that the in case there were configuration issues with the desktop, all data would reside in separate home directories, thinking that everything would be safe.  Incidentally, Debian and Sabayon boot just fine, and so does Edgy if I mount /home manually.

I guess I should just be happy with Ubuntu and stop playing with these other distros.  But how am I to learn about Linux if everything just works?

I just have one question.  Why do we need UUID's for partitions?  They never had them before.

---

