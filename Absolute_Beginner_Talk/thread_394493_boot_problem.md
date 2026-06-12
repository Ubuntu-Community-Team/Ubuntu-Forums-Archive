---
title: "boot problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by antoz on 2007-03-27
get the following when trying to boot:

root (hd 0,0)

filrsystem type unknown partition type 0 x 7
kernel /boot/vm linuz-2.6.15-23-386 root= ro quiet splash
Error 17:cannot mount selected partition

If anyone out there can tell what is wrong I would really apreciate it I am trying to learn something here before I restart with an other install

There is more info on my previous post earlier.thanks in advance. A
[http://www.ubuntuforums.org/showthread.php?t=394394](http://www.ubuntuforums.org/showthread.php?t=394394)

---

### Post by chewearn on 2007-03-27
I looked at the other thread, the fdisk output showed your primary boot disk has the following structure:

[ sda1 ] [ sda2 ] [ sda3 ]

sda1 NTFS (Windows boot)
sda2 Extended partition
sda3 ext3 (Linux)

Inside the Extended partition sda2, you have:
[ sda5 ] [ sda6 ] [ sda7 ] [ sda8 ]

sda5 NTFS (Windows)
sda6 FAT32
sda7 Swap (Linux)
sda8 Ext3 (Linux)

Now, from the error message you shown, grub is trying to load linux from (hd0,0), which is sda1.  Since you have Windows in this partition, obviously it fails.

To fix this, boot up from your ubuntu Live CD.  Then, mount your Linux root partition (probably its sda3, else its sda8).
Then edit the file /boot/grub/menu.lst in that partition to fix the locations of the linux kernel.

---

### Post by antoz on 2007-03-27
thanks AstalaVista tried mounting the partition but there seems to be a problem there, I think I am a bit out of my depth here.

ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/windows -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by chewearn on 2007-03-27
sda3 is linux ext3 partition.  Mount using this:
```
sudo mkdir /media/sda3
```
```
sudo mount -t ext3 /dev/sda3 /media/sda3
```

Check and confirm that sda3 is your linux root.  Then, edit menu.lst:
```
sudo gedit /media/sda3/boot/grub/menu.lst
```

If you have doubt about editing menu.lst, post the output:
```
cat /media/sda3/boot/grub/menu.lst
```

---

### Post by dstew on 2007-03-27
You can edit the grub menu by entering 'E' when the menu shows up at boot time.

---

### Post by antoz on 2007-03-27
Thanks for the code (stupid of me using the code for ntfs just copied it from aysiu's mount page)

I changed my menu lst from 0 to 2 (**dstew** also tried E at boot) both optins worked it starts to boot "uncompressing linux etc..." but then hangs waiting for root filesystem. Left it there and after a while I get a black screen with a lot of info about problems. I am really not competent enough to figure that out
will persist a bit longer with it since I am learning something if I decide to reinstall should i just install on top of it? or is it best to start from scratch and redo all my partitions.

Have a great day or night, A

---

### Post by dstew on 2007-03-27
Now you know that grub can find the kernel, but the kernel has trouble mounting the root file system. Please post the menu list item for the kernel you are trying to boot.

EDIT: I notice that the kernel line in your original post is missing the kernel root partition:

kernel /boot/vm linuz-2.6.15-23-386 root= ro quiet splash

Is that really what you have?

---

### Post by antoz on 2007-03-27
## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root= ro

## default grub root device
## e.g. groot=(hd0,2)          **changes "2 was previously 0"** that goes for all the others as well
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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root= ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root= ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[B]
I can see all the folders on sda3 but a few of them are empty, like root and system is that normal?[/B]

---

### Post by antoz on 2007-03-27
here are some screen shots of my "sda3" content

---

### Post by confused57 on 2007-03-28
As dstew mentioned, your kernel line is missing the root designation:

```
title Ubuntu, kernel 2.6.15-23-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot
```

root device is also missing in this line:
# kopt=root=/dev/sda3 ro

Try highlighting your Ubuntu entry in the grub boot menu, press "e" to edit, then change your kernel line to reflect your root=/dev/sda3, then press "b" to boot...also, make sure root is (hd0,2).

---

### Post by sandman55 on 2007-03-28
Hi antoz here is my list I think its the same as yours only you have a sata drive and I have a pata drive, my system works.
```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

```

---

### Post by sandman55 on 2007-03-28
Now that I have looked at them side by side I see a difference
```
Yours
title Ubuntu, kernel 2.6.15-23-386 
```
```
 Mine
title Ubuntu, kernel 2.6.15-28-386 
```

there are two choices when we select which Ubuntu to boot I dont know what the reason is for this I have tried both and they work perhaps someone can explain this. I have wondered if it is the version before Dapper but I'm only guessing:confused:

**EDIT:** after looking further I have the two choices  the one with the line containing 23 and the one with the line containing 28 which both work (I see these two choices when I select from Grub at bootup) and you have only the one choice with the line containing 23 , but that could be something not right in my system perhaps someone can explain this.

---

### Post by chewearn on 2007-03-28
It simply means you have two kernels in the same install.  The original one is 2.6.15-23-386.  Then, some time later, you got a kernel update 2.6.15-28-386 from the repository.

---

### Post by antoz on 2007-03-28
First thanks all of you for trying to help, I am one step further. I edited my menu lst to enter my root partition and it boots**[COLOR="Red"] BUT I now have a problem logging in,[/COLOR]** I get the following message:
? You home directory is listed as:
"/Home/my name"
but it does not appear to exist. Do you want to log in with /(root) directory as your home directory.
It is unlikely anything else wil work unless you use a failsafe session
NO - YES

Neither option works just keep coming back to the log in screen. **My Home is on "sda8"** could it be because it is on a different partition? what can I do about it?
Cheers to all of you this has been a good learning experience so far.

---

### Post by confused57 on 2007-03-28
> **antoz said:**
> First thanks all of you for trying to help, I am one step further. I edited my menu lst to enter my root partition and it boots**[COLOR="Red"] BUT I now have a problem logging in,[/COLOR]** I get the following message:
? You home directory is listed as:
"/Home/my name"
but it does not appear to exist. Do you want to log in with /(root) directory as your home directory.
It is unlikely anything else wil work unless you use a failsafe session
NO - YES

Neither option works just keep coming back to the log in screen. **My Home is on "sda8"** could it be because it is on a different partition? what can I do about it?
Cheers to all of you this has been a good learning experience so far.

If you're using Edgy, it could be that your UUID is incorrect in your /etc/fstab.  You can check your UUID's on all partitions with:
```
 ls /dev/disk/by-uuid/ -alh
```
or just sda8
```
sudo vol_id -u /dev/sda8
```

Then you compare them with the UUID's in your /etc/fstab:
```
cat /etc/fstab
```
to edit your fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```
the first command creates a backup & the 2nd will open it for editing.

One or more of your UUID mountpoints is probably wrong & needs to be corrected, you might want to read over this explanation of UUID in Edgy:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
see the section on Hard Disk installed method(editing /etc/fstab).

---

### Post by dstew on 2007-03-28
Is your partition containing your home directory mounted when your system boots? That is, is it listed correctly in your etc/fstab file? You can list it by more /etc/fstab. If you can't log in, you might have to boot from the live CD, mount your /dev/hda6 file system in a temporary directory to be able to see or edit /etc/fstab.

Also, beware of file or directory names with spaces in them, if indeed "my name" is the real name of the directory. Sometimes they will not be legible to software processes. Better to use an underscore instead of a space. Sometimes if you put single quotes around file names with spaces commands will work correctly.

---

### Post by antoz on 2007-03-28
I am using dapper

---

### Post by confused57 on 2007-03-28
> **antoz said:**
> I am using dapper
You might want to post the output of:
```
cat /etc/fstab
```
this will show if your mountpoint for /dev/sda8 is /home, in your case.

also you might want to read over the link I gave you for editing /etc/fstab...it's basically the same, except you're not using UUID's

---

### Post by antoz on 2007-03-28
here is what I get I mounted both with the live CD and they are accessible

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
ubuntu@ubuntu:~$

---

### Post by confused57 on 2007-03-28
> **antoz said:**
> here is what I get I mounted both with the live CD and they are accessible

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
ubuntu@ubuntu:~$

Here's my /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I'm not familiar with your entry "unionfs / unionfs rw 0 0", but thought my fstab "might" help you add an entry to mount your /home,  something like this?:
```
/dev/sda8   /home   ext3    defaults   0    2
```

Maybe someone else can explain  your /etc/fstab entries...make sure to create a backup of your /etc/fstab, before you edit it.

---

### Post by antoz on 2007-03-28
This is what it looks when I get it for editing, also it gave me a warning before about permissions. 

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0

I have to go out now so will get back to it later, this is all very new to me while I had installed an earlier version of Ubuntu on my old computer I never really used it much because with only 62meg of ram it was too slow.

---

### Post by dstew on 2007-03-29
antoz, you are looking at the fstab for the LiveCD, not the fstab for the linux that you installed on your hard disk. The union file system is the temporary file system that the live CD builds in the memory so it can run. Your hard disk is usually not mounted at all when running the live CD.

In order to look at your "real" fstab file, you need to mount your hard disk file system onto the union file system that the live CD is using. It is the same process you use whenever you mount any disk partition on any linux file system. There are two steps. 1, create a mount point. 2, mount the partition.

When the live CD is running, you first need to create a mount point in the union file system. You open a terminal, and enter

mkdir /media/hard_disk

You don't have to use "hard_disk", that is only my suggestion. You can use any name for the mount point. The /media folder already exists in the union fs.

Next, mount your hard disk partition to that mount point. I believe your linux system hard disk partition is /dev/sda3, correct? That is, it booted when you used this in your kernel line. If that is so, then your /etc/fstab is likely to be in that partition also. So, mount the partition on your union file system by entering this at the terminal:

mount /dev/sda3 /media/hard_disk

If that command is successful, you can now show your "real" fstab file by using

cat /media/hard_disk/etc/fstab

---

### Post by antoz on 2007-03-29
Thanks dstew but it points out more problems

ubuntu@ubuntu:~$ sudo mkdir /media/hard_disk
mkdir: cannot create directory `/media/hard_disk': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/hard_disk
mount: /dev/sda3 already mounted or /media/hard_disk busy
mount: according to mtab, /dev/sda3 is already mounted on /media/hard_disk
ubuntu@ubuntu:~$ cat /media/hard_disk/etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
ubuntu@ubuntu:~$ sudo cat /media/hard_disk/etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
ubuntu@ubuntu:~$

Tried it twice same result both times, i'ts midnight here now so I woll call it a day, will check again tommorow. A

---

### Post by confused57 on 2007-03-29
> **dstew said:**
> antoz, you are looking at the fstab for the LiveCD, not the fstab for the linux that you installed on your hard disk. The union file system is the temporary file system that the live CD builds in the memory so it can run. Your hard disk is usually not mounted at all when running the live CD.

In order to look at your "real" fstab file, you need to mount your hard disk file system onto the union file system that the live CD is using. It is the same process you use whenever you mount any disk partition on any linux file system. There are two steps. 1, create a mount point. 2, mount the partition.

When the live CD is running, you first need to create a mount point in the union file system. You open a terminal, and enter

mkdir /media/hard_disk

You don't have to use "hard_disk", that is only my suggestion. You can use any name for the mount point. The /media folder already exists in the union fs.

Next, mount your hard disk partition to that mount point. I believe your linux system hard disk partition is /dev/sda3, correct? That is, it booted when you used this in your kernel line. If that is so, then your /etc/fstab is likely to be in that partition also. So, mount the partition on your union file system by entering this at the terminal:

mount /dev/sda3 /media/hard_disk

If that command is successful, you can now show your "real" fstab file by using

cat /media/hard_disk/etc/fstab

Good point, I thought antoz was using the instructions by AstalaVista in reply#4 to mount his root partition.  Least I know what unionfs is now.

antoz,  you might want to read back over the instructions by AstalaVista, it should work.  The only difference would be after mounting, enter:
```
cat /media/sda3/etc/fstab
```

Added:  Once you get your /dev/sda3 mounted, you could probably just open nautilus from the live cd, navigate to your /media/sda3 directory...open your /etc directory & check your fstab or if there is a backup.  If there isn't a working fstab file, you could try creating one, using mine as a template...you mentioned earlier in your thread that you wanted to use this as a learning experience, but that you'd probably end up reinstalling.

---

### Post by dstew on 2007-03-29
Somehow, the hard disk is already mounted to that mount point. That is OK. The result of the cat operation shows that your system fstab file is empty, it just contains the stub line. You could at this time edit the fstab file to put in your /home partition mount instructions, but my guess is that there are other problems with your installation yet to be revealed. Maybe it is better to install again.

---

### Post by antoz on 2007-03-29
The fstab folder in etc is empty it just says UNCONFIGURED BASE SYSTEM
 Attached is a screen shot of the uuid

Thanks all of you for your help but the only one "confused" here is me

---

### Post by confused57 on 2007-03-29
> **antoz said:**
> The fstab folder in etc is empty it just says UNCONFIGURED BASE SYSTEM
 Attached is a screen shot of the uuid

Thanks all of you for your help but the only one "confused" here is me
I'll have to agree with dstew, there's probably major problems with your install that hasn't surfaced yet...if you want, you can try to make a new fstab file...just to see what happens.

Mount your sda3, then:
```
cd /media/sda3/etc
gksudo gedit fstab
```

then delete what's in the file, then copy & paste something like this:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /home           ext3    defaults        0       2
/dev/sda7       none            swap    sw              0       0
```

quit & choose save...then try to reboot, probably won't work, but you haven't lost anything by trying.

---

### Post by antoz on 2007-03-30
Thanks a lot confused this absolutely did the trick, I was able to log in for the first time, will probably have other issues down the road like getting my printer and scanner to work etc...
By the way where is Eden NC; there is an Eden here as well in New South Wales between Sydney and Melbourne (a real pretty spot)

---

### Post by confused57 on 2007-03-30
> **antoz said:**
> Thanks a lot confused this absolutely did the trick, I was able to log in for the first time, will probably have other issues down the road like getting my printer and scanner to work etc...
By the way where is Eden NC; there is an Eden here as well in New South Wales between Sydney and Melbourne (a real pretty spot)

Wow, I'm amazed & glad it worked and you probably learned a little about Linux, as well...if you want your cd drive & floppy drives to be mounted when you insert a cd or disc, you might also want to add entries similar to what I have in my /etc/fstab.   Good job, your perseverance paid off & if you need to reinstall, it'll be easier the next time to troubleshoot & configure your system.

Eden is a town in the north central part of the state of North Carolina in the US...it once was 3 separate town districts, but they merged(in the 1970's, I believe) & named the community Eden.
It's a rural area, the closest "city" is 35 miles from here...I definitely prefer living in a location away from the "hustle & bustle" of city-life, nice to visit but not reside.  

The first link in my signature is a website developed and maintained by Herman, a forum member, who also lives in Australia...seems there are quite a few forum members from Australia.
To me,  one of the great things about Linux & Ubuntu is the international community we have here...it never ceases to amaze me.

See you around in the forum...I'm sure you'll enjoy learning Ubuntu & Linux.

---

