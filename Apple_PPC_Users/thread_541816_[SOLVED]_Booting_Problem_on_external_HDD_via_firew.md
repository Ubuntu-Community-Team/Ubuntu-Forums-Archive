---
title: "[SOLVED] Booting Problem on external HDD via firewire."
date: 2007-09-03
forum: Apple PPC Users
---

### Post by computer geek on 2007-09-03
I installed Ubuntu on an external Western Digital My Book Preimoum.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

I have a swap, OS X, ext3, and a small boot partition. When i rebooted after installed, i got os x and not yaboot or something like that.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif) :frown:

What do i do?

---

### Post by pxwpxw on 2007-09-03
External firewire needs a fix for the apple mac open firmware paths in the /etc/yaboot.conf file to get it booting. But first can you post your Apple mac type and the full title of the install CD used, and the  MacosX version .

Edit:
Later found that the WDC MyBook is OK with the current Feisty704  and earlier yaboot installer and ofpath, and should boot either from the external or the internal without any extra work, after a normal install.

Can be seen  in /proc/scsi/scsi

WDC MyBook  has 
 Type:   "Direct-Access", which is recognised by yaboot ofpath

But some others including IceCube have
 Type:   "Direct-Access-RBC", and  are not recognised by ofpath.

---

### Post by computer geek on 2007-09-03
I have a eMac G4 and and a My book preimoum. 756 RAM. I am using live ubuntu cd. And Mac OS X Tiger.

---

### Post by pxwpxw on 2007-09-03
thanks, in tiger, open a terminal, and post the output from these (with your Mybook running)
```

 diskutil list
 sudop pdisk -l
 sudo nvram boot-device

```

---

### Post by computer geek on 2007-09-03
Will this keep me from booting os x?:confused:

(i am just a beginer.)

---

### Post by pxwpxw on 2007-09-03
Those commands just list information, they dont change anything.

---

### Post by computer geek on 2007-09-03
when i did that i got a password feild.
will that do anything?

(NOTE: I used the sudo things but did not type password.)

---

### Post by pxwpxw on 2007-09-03
Just do the 
```

 diskutil list

```
it doesn't need sudo.

---

### Post by computer geek on 2007-09-03
What about the other sudo comands you poasted?

---

### Post by computer geek on 2007-09-03
ok now what.

this is the output.(PDF, Atached,  Next page,&#8595;







[http://ubuntuforums.org/showthread.php?t=541816&highlight=via+firewire&page=2](http://ubuntuforums.org/showthread.php?t=541816&highlight=via+firewire&page=2)
the link is where your next poast will show.And the next place my next poast will be.

---

### Post by computer geek on 2007-09-03
Last login: Mon Sep  3 12:03:15 on ttyp1
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *153.4 GB disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:         Apple_Driver43                    28.0 KB   disk0s2
   3:         Apple_Driver43                    28.0 KB   disk0s3
   4:       Apple_Driver_ATA                    28.0 KB   disk0s4
   5:       Apple_Driver_ATA                    28.0 KB   disk0s5
   6:         Apple_FWDriver                    256.0 KB  disk0s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk0s7
   8:          Apple_Patches                    256.0 KB  disk0s8
   9:              Apple_HFS Kids Computer      153.3 GB  disk0s10
/dev/disk1
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *298.1 GB disk1
   1:    Apple_partition_map                    31.5 KB   disk1s1
   2:         Apple_Driver43                    28.0 KB   disk1s2
   3:         Apple_Driver43                    28.0 KB   disk1s3
   4:       Apple_Driver_ATA                    28.0 KB   disk1s4
   5:       Apple_Driver_ATA                    28.0 KB   disk1s5
   6:         Apple_FWDriver                    256.0 KB  disk1s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk1s7
   8:          Apple_Patches                    256.0 KB  disk1s8
   9:        Apple_UNIX_SVR2                    896.0 MB  disk1s10
  10:              Apple_HFS OS X               178.1 GB  disk1s12
  11:        Apple_UNIX_SVR2                    99.6 GB   disk1s14
  12:        Apple_Bootstrap                    19.0 GB   disk1s16
/dev/disk2
   #:                   type name               size      identifier
   0:    CD_partition_scheme                    *789.3 MB disk2
   1: Apple_partition_scheme                    687.3 MB  disk2s1
   2:    Apple_partition_map                    1024.0 B  disk2s1s1
   3:              Apple_HFS Ubuntu_PowerPC_feisty 693.1 MB  disk2s1s2
Stephen-Rhodas-Computer-2:~ Jacob$

---

### Post by pxwpxw on 2007-09-04
> **computer geek said:**
> ok now what.

this is the output.(PDF, Atached,  Next page,&#8595;

[http://ubuntuforums.org/showthread.php?t=541816&highlight=via+firewire&page=2](http://ubuntuforums.org/showthread.php?t=541816&highlight=via+firewire&page=2)
the link is where your next poast will show.And the next place my next post will be.

Got all that, thats good info, are you running macos9 as well - there seem to be lots of drivers?
Then can you try the boot-device info again and post that. Expect just one line result. 
For sudo, just type your password when asked. That runs the command as superuser ( root).
```

 nvram boot-device
## if that does nothing try
 sudo nvram boot-device

```
 
I will check out the external  firewire setup on my system, see what to do.

---

### Post by computer geek on 2007-09-04
output to "nvram boot-device"

Last login: Tue Sep  4 07:11:48 on console
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ nvram boot-device
boot-device     /pci@f4000000/firewire@e/node@0090a993e0200acf/sbp-2@c000/disk@0:3,\\:tbxi
Stephen-Rhodas-Computer-2:~ Jacob$

---

### Post by pxwpxw on 2007-09-04
got that, looks good, need a while to work out next move.

meanwhile, 

 can you tell me if MacosX is the "Apple_HFS OS X 178.1 GB disk1s12"  on the firewire drive, 

 and is there another Macos on the" 9: Apple_HFS Kids Computer 153.3 GB disk0s10" partition, on the internal drive, or is that just storage.

EDIT:

and if you have had the CD in the drive, take it out and retry, might be causing problem.

---

### Post by computer geek on 2007-09-04
yes the "10: Apple_HFS OS X 178.1 GB disk1s12" drive is the mac os x partition on the firewire drive.

And no there is not another mac os storage mounted or dected on my internal HDD.

---

### Post by pxwpxw on 2007-09-04
> **pxwpxw said:**
> got that, looks good, need a while to work out next move.

meanwhile, 

 can you tell me if MacosX is the "Apple_HFS OS X 178.1 GB disk1s12"  on the firewire drive, 

 and is there another Macos on the" 9: Apple_HFS Kids Computer 153.3 GB disk0s10" partition, on the internal drive, or is that just storage.

EDIT:

and if you have had the CD in the drive, take it out and retry, might be causing problem.


continued:

There is something wrong with that boot-device setting, it is pointing to the firewire drive, partition 3, but the ubuntu boot partition is at:

 12: Apple_Bootstrap 19.0 GB disk1s16

Which is partition number 16.

(Also far too big, but wont stop it working )

Is the WDC MyBook the only firewire device connected?
Is the CD drive the usual internal one - not another external firewire?

( Not worried about partition sizes at this stage, just want to get you restarted into ubuntu. )

We may just need to change that boot-device setting, can do that from macosx, but need to make sure first.

---

### Post by computer geek on 2007-09-04
Last login: Tue Sep  4 07:17:22 on ttyp1
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *153.4 GB disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:         Apple_Driver43                    28.0 KB   disk0s2
   3:         Apple_Driver43                    28.0 KB   disk0s3
   4:       Apple_Driver_ATA                    28.0 KB   disk0s4
   5:       Apple_Driver_ATA                    28.0 KB   disk0s5
   6:         Apple_FWDriver                    256.0 KB  disk0s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk0s7
   8:          Apple_Patches                    256.0 KB  disk0s8
   9:              Apple_HFS Kids Computer      153.3 GB  disk0s10
/dev/disk1
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *298.1 GB disk1
   1:    Apple_partition_map                    31.5 KB   disk1s1
   2:         Apple_Driver43                    28.0 KB   disk1s2
   3:         Apple_Driver43                    28.0 KB   disk1s3
   4:       Apple_Driver_ATA                    28.0 KB   disk1s4
   5:       Apple_Driver_ATA                    28.0 KB   disk1s5
   6:         Apple_FWDriver                    256.0 KB  disk1s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk1s7
   8:          Apple_Patches                    256.0 KB  disk1s8
   9:        Apple_UNIX_SVR2                    896.0 MB  disk1s10
  10:              Apple_HFS OS X               178.1 GB  disk1s12
  11:        Apple_UNIX_SVR2                    99.6 GB   disk1s14
  12:        Apple_Bootstrap 

does this work? it is without the ubuntu cd in

---

### Post by pxwpxw on 2007-09-04
Right, heres the plan. If its not clear to you, tell me.

We will just change the boot-device setting to what I think it should be. But first you need to make sure you can get restarted into MacosX in case it does not work.

You do that by resetting the Open Firmware "boot-device" to the standard setting.
("zap the pram" you may know that,  but here it is again )

ZAP the PRAM:

1. Shut-down or restart the mac.

While it is starting up, hold down the 4 keys 
Command(Apple)-Option-P-R

You should hear a second chime after a few seconds, then release the keys.
If you don't get it right it wont break anything, just try again.

Then you should start up in macosx.

2. First, see what happened to the boot-device, as before
```

 nvram boot-device

```

When you are ready, try changing the boot-device setting --

In MaxosX.

3. To set the boot-device to try booting firewire from partiton 16:
```

#### set it
 sudo nvram boot-device=fw/node/sbp-2/disk:16,yaboot
#### check it again to see that it got reset
 nvram boot-device

```
That is a short version, easier to type.

4. Then try a restart.

If it fails, it wont do any damage, just "zap the pram" as above and tell me about it.

---

### Post by computer geek on 2007-09-04
Ok,i zaped my pram and here is the output of nvram boot-device after pram was zaped.

Last login: Tue Sep  4 12:04:43 on console
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ nvram boot-device
boot-device     hd:,\\:tbxi
Stephen-Rhodas-Computer-2:~ Jacob$

---

### Post by computer geek on 2007-09-04
it did not work.

I ran it as a command and shell.

---

### Post by pxwpxw on 2007-09-05
Which step did it fail in - I have numberd the steps to help.

---

### Post by computer geek on 2007-09-05
I dont know. i did what you said but when i idid sudu in a comand it did not work.

---

### Post by pxwpxw on 2007-09-05
That should be **sudo** not sudu.
Try again.

---

### Post by computer geek on 2007-09-05
do you think it sould be, ```
sudo nvram boot-device = fw/node/sbp-2/disk:12,yaboot
```

not, ```
sudo nvram boot-device = fw/node/sbp-2/disk:16,yaboot
```

NOTE:disk:12,yaboot
           disk:16,yaboot ? Yours

---

### Post by pxwpxw on 2007-09-06
> **computer geek said:**
> do you think it sould be, ```
sudo nvram boot-device = fw/node/sbp-2/disk:12,yaboot
```

not, ```
sudo nvram boot-device = fw/node/sbp-2/disk:16,yaboot
```

NOTE:disk:12,yaboot
           disk:16,yaboot ? Yours

1. I think that it might be a good idea to try some other numbers, but to explain a bit, here is your listing from before.

/dev/disk1
#: type name size identifier
0: Apple_partition_scheme *298.1 GB disk1
1: Apple_partition_map 31.5 KB disk1s1
2: Apple_Driver43 28.0 KB disk1s2
3: Apple_Driver43 28.0 KB disk1s3
4: Apple_Driver_ATA 28.0 KB disk1s4
5: Apple_Driver_ATA 28.0 KB disk1s5
6: Apple_FWDriver 256.0 KB disk1s6
7: Apple_Driver_IOKit 256.0 KB disk1s7
8: Apple_Patches 256.0 KB disk1s8
9: Apple_UNIX_SVR2 896.0 MB disk1s10
10: Apple_HFS OS X 178.1 GB disk1s12
11: Apple_UNIX_SVR2 99.6 GB disk1s14
12: Apple_Bootstrap 19.0 GB disk1s16 

The numbers at the left side are just list item numbers, the real partition numbers are the "s" numbers in the disk1s entries, like disk1s16,  which would be partition 16 for the Apple_Bootstrap. But you should first make sure that you are in fact getting the boot-device set for partition 16, by checking it again in macosx immediately after you set it. 
```

 nvram boot-device

```
check that it prints exactly what you intended to entere after the = sign. It is easy to make a typing error.
Then please tell me exactly what happened after you restarted.

2. Here is something different to try, a lot simpler.
Hold down the Option key while you restart the commputer.
Then tell me  what you see on the first screen.
That might be an easier way to fix things.

3. But if none of that works, I think you should think about installing a small ubuntu system (say 10 GB) on your internal drive (after making a space for it from there), and just use the firewire drive for extra file storage space. But that would need you be sure you backed up anything important on the inetrnal disk, and get further advice about resizing the existing parttion.

---

### Post by computer geek on 2007-09-21
I got this

```
sudo nvram boot-device = fw/node/sbp-2/disk:16,yaboot; exit
boot-device     hd:,\\:tbxi
nvram: Error (-1) getting variable - 'fw/node/sbp-2/disk:16,yaboot'
logout
[Process completed]
```

What do i do?


P.S. I was on vacation

---

### Post by pxwpxw on 2007-09-21
> **computer geek said:**
> I got this

```
sudo nvram boot-device = fw/node/sbp-2/disk:16,yaboot; exit
boot-device     hd:,\\:tbxi
nvram: Error (-1) getting variable - 'fw/node/sbp-2/disk:16,yaboot'
logout
[Process completed]
```

What do i do?


P.S. I was on vacation

Welcome back.
Try it with and without the spaces round the equal sign, someone else had trouble with that.
And leave off the ;exit I don't know where that came from.
Like so:

```
sudo nvram boot-device=fw/node/sbp-2/disk:16,yaboot
```

---

### Post by computer geek on 2007-09-22
This is the output of

```
sudo nvram boot-device=fw/node/sbp-2/disk:16,yaboot
```


```
command: nvram boot-device
 output: boot-device     fw/node/sbp-2/disk:16,yaboot
```


Is this right?

---

### Post by pxwpxw on 2007-09-22
```

command: nvram boot-device
 output: boot-device     fw/node/sbp-2/disk:16,yaboot

```

Yes, now try a restart.

---

### Post by computer geek on 2007-09-22
it did not work.

why?

---

### Post by pxwpxw on 2007-09-22
Well, it did not work because yaboot was not on partition 16 on the firewire drive, or because I got the boot-device path wrong.
 - unless you saw something on the screen to indicate that yaboot started - it would help to know if you saw anything.

Do you have the Live Desktop ubuntu cd there, if so you coud use it to see where yaboot has gone.

You could try the other ubuntu partitions, or you could try the full (long) boot-device path, but I think you need to look at the other options now.

We need to check a few things. I think there are a lot of partitions on both of your drives that should not be there, and the ubuntu Apple_Bootstrap partition should be less than 1 Megabyte but it is 19 Gigabytes. 

This makes me think something went wrong with the installation and partitioning on both the internal disk and the external. If you are only using Tiger, you should not have all those partitions.

It might be time to start again.

Will you please confirm that you have the external drive connected using a firewire cable and NOT a usb cable.

Do you have the Apple Macosx Tiger install DVD in case you need to reinstall Tiger, or re-partition a drive.

Would you be able to repartition the internal drive and install ubunutu there - you would have to get everything off the internal and save on the external in the macosx partition, but that would be the easiest way to install ubuntu. Or you could re-partition the external drive and reinstall there.

I am off to sleep now, I will check the thread tomorrow.

---

### Post by computer geek on 2007-09-22
I don't want to partition my internal HDD.

can i try the long address?

or if that does not work i can reformat the extrnal HDD and you can tell me how to partition the drive.

i made a swap,mac os,boot,and ext3. (in disk utility.) then reformatted them in ubuntu.:(

---

### Post by pxwpxw on 2007-09-23
> **computer geek said:**
> I don't want to partition my internal HDD.

can i try the long address?

or if that does not work i can reformat the extrnal HDD and you can tell me how to partition the drive.

i made a swap,mac os,boot,and ext3. (in disk utility.) then reformatted them in ubuntu.:(

Well, there are still some of my questions unanswered, but to answer your post I think best to see if we can find yaboot using ubuntu, then think about your suggestions.

For the partitioning, its not a good idea to create the ubuntu partitions in macosx, best is to just leave free space or one partiton to be deleted, and then let ubuntu make the boot, root and swap partitions, but you can do it manually too.

1. However first, please see what happens when you start up with the Option key held down, and report on what you see - this is an easy way to detect bootable drives.

2. You have the Ubuntu Feisty Live Desktop CD.
 Start that up in its desktop and see if you can post to the forum from Firefox (I have the same desktop CD here and it works well on an ibookg4 if you have an ethernet network connection). But DON'T use the "Examples" or the "Install" icon, you dont want to install again just now.

If you can do that, you can refer to this thread from ubuntu, then you can go on to check what is on the ubuntu partitions you installed on the external drive and find yaboot if it is there. If you have some text you need to save from there you can just post it to this thread.

Then if you can find the boot partition with yaboot you can try again to boot from macosx.
If not, then the reinstall of Macosx and Ubuntu on the external drive is the best plan if you can do it. 

When ubuntu desktop starts up, it may show desktop icons for some partitions on the drives, but gives them its own names to use when it mounts them in the /media directory. Firewire partition icons  have a small orange label with a Y shape. 
[B]Edit:
If the desktop does not show the partitions, you need to open the filemanager to  Menubar->Places->Computer, and it will show the partitions. Then you can mount each one by Right Click-> Mount Volume.
[/B]
Then open a terminal from 
Top Menu-bar:Applications:Accessories:Terminal
and type 
```

 df
## and to show partition types (ext3, hfs)
 mount

```

That will give you a list of mounted partiton numbers sizes, and names for the /media directory and the desktop. You can identify them by their sizes from the df command, and their types from the mount command.

If your external drive partitions are there you can then double click them to see what files are in those partitions.

The bootstrap partition (16?) should have type "hfs" and files named: yaboot, yaboot.conf, ofboot.b

The root partition (14?) should have type "ext3" and directories named:
  bin,cdrom,etc,home,lib,media,opt, root,tmp,var,boot,dev, mnt,proc,sbin,sys,usr,

The swap partition (10?) will not be shown. 

3. If you can find the root partition but cant find the Apple_Bootstrap partition with its files, that may just mean that it needs to be mounted manually, if you post from ubuntu I can explain how to do that.

You can PM me if you need to, but my time zone is UTC+10.

---

### Post by computer geek on 2007-09-25
I don't know if this is right.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ dfmount
bash: dfmount: command not found
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   386768       268    386500   1% /lib/modules/2.6.20-15-powerpc/volatile
tmpfs                   386768       268    386500   1% /lib/modules/2.6.20-15-powerpc/volatile
varrun                  386768       100    386668   1% /var/run
varlock                 386768         0    386768   0% /var/lock
udev                    386768       196    386572   1% /dev
devshm                  386768         0    386768   0% /dev/shm
tmpfs                   386768        12    386756   1% /tmp
/dev/sda14           102755244   2203100  95332428   3% /media/disk
/dev/sda12           186748960  16627076 170121884   9% /media/OS X
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-powerpc/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-powerpc/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda14 on /media/disk type ext3 (rw,noexec,nosuid,nodev)
/dev/sda12 on /media/OS X type hfsplus (rw,noexec,nosuid,nodev)
ubuntu@ubuntu:~$ 
```

:confused::confused:

---

### Post by pxwpxw on 2007-09-25
Thats fine, the live cd will make it easier, I hope the desktop display is OK, and the Firefox browser. 
I am posting this from the ubuntu704 live cd.

Now you can run the live cd again to find yaboot.conf in the firewire ubuntu root partition, which is /dev/sda14, mounted at /media/disk when you posted.

First, when you get back into ubuntu desktop, check in terminal that it is still showing /dev/sda14 mounted on /media/disk 
```

df

```
Then open the filemanager from Menu bar-Places-Computer
Make a list of the names of the partitions (volumes ) and post them later.
 
You should see "disk" there.
Open "disk" and it should show the top level folders and files in your firewire root partition "/". 
Find the folder /etc and open it, then find yaboot.conf (right down at the bottom)
( If its not there, we are in trouble).

Open yaboot.conf in text editor.

Then please  copy and paste all of yaboot.conf to this thread. That will be very useful info.

Cloes text editor without saving (it won't let you save to that file).

Next step after this will be to check the files in the boot partition at  /dev/sda16, you will probably have to do that from a terminal, unless you see it in the file manager among the other partitions.

---

### Post by computer geek on 2007-09-25
These are the partitions in, Places,Computer.

CD Drive. disk. Intrnal HDD. OS X. Filesystem.

---

### Post by computer geek on 2007-09-25
I did a search on the "disk" partition and all was found in ```
disk/usr/
```

---

### Post by computer geek on 2007-09-25
thers yaboot in, ```
disk/usr/lib/yaboot/
```

Theres Yaboot, ofboot,and addnote

---

### Post by pxwpxw on 2007-09-26
Good.

Now we can use the information from your last posts to get more details this way: 

From the ubuntu desktop.

 open the filemanager from the Menubar-Places-Cpmputer.
 Double click "disk"
 Leave that window open.
 Now also open a terminal.
 Do each of these commands from the terminal command line and after each one, copy and paste the result to this thread.

To run each command, it is best to copy and paste the command from this thread to your terminal, then press the enter key. That will avoid any typing errors.
(These commands are what I would do if had your computer here)

```

df

```

```

cat /proc/partitions 

```

```

ls -l /media/disk/

```

```

ls -l /media/disk/etc

```

```

cat /media/disk/etc/yaboot.conf

```

```

sudo find /media/disk -name yaboot*

```

---

### Post by computer geek on 2007-09-26
in these commands,

```
ls -l /media/disk/
```


is the ```
-l 
``` a one or a l :confused:

---

### Post by pxwpxw on 2007-09-26
letter l

---

### Post by computer geek on 2007-09-26
this id the output of those commands.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   386768       268    386500   1% /lib/modules/2.6.20-15-powerpc/volatile
tmpfs                   386768       268    386500   1% /lib/modules/2.6.20-15-powerpc/volatile
varrun                  386768       100    386668   1% /var/run
varlock                 386768         0    386768   0% /var/lock
udev                    386768       196    386572   1% /dev
devshm                  386768         0    386768   0% /dev/shm
tmpfs                   386768        12    386756   1% /tmp
/dev/sda14           102755244   2203100  95332428   3% /media/disk
/dev/sda12           186748960  16627076 170121884   9% /media/OS X
ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   3     0  160836480 hda
   3     1         31 hda1
   3     2         28 hda2
   3     3         28 hda3
   3     4         28 hda4
   3     5         28 hda5
   3     6        256 hda6
   3     7        256 hda7
   3     8        256 hda8
   3     9     131072 hda9
   3    10  160704488 hda10
   3    11          8 hda11
   8     0  312571224 sda
   8     1         31 sda1
   8     2         28 sda2
   8     3         28 sda3
   8     4         28 sda4
   8     5         28 sda5
   8     6        256 sda6
   8     7        256 sda7
   8     8        256 sda8
   8     9     131072 sda9
   8    10     917504 sda10
   8    11     131072 sda11
   8    12  186765104 sda12
   8    13     131072 sda13
   8    14  104394356 sda14
   8    15     131072 sda15
   7     0     652256 loop0
ubuntu@ubuntu:~$ ls -l /media/disk/
total 88
drwxr-xr-x   2 root root  4096 2007-04-15 14:03 bin
drwxr-xr-x   2 root root  4096 2007-09-01 13:04 boot
lrwxrwxrwx   1 root root    11 2007-09-01 12:48 cdrom -> media/cdrom
drwxr-xr-x   6 root root  4096 2007-09-01 13:03 dev
drwxr-xr-x 106 root root  4096 2007-09-01 13:04 etc
drwxr-xr-x   3 root root  4096 2007-09-01 13:00 home
drwxr-xr-x   2 root root  4096 2007-04-15 13:41 initrd
drwxr-xr-x  17 root root  4096 2007-04-15 14:03 lib
drwx------   2 root root 16384 2007-09-01 12:47 lost+found
drwxr-xr-x   3 root root  4096 2007-04-15 13:53 media
drwxr-xr-x   2 root root  4096 2007-09-02 11:05 mnt
drwxr-xr-x   2 root root  4096 2007-04-15 13:41 opt
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 proc
drwxr-xr-x   3 root root  4096 2007-04-15 13:53 root
drwxr-xr-x   2 root root  4096 2007-09-01 13:04 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 13:41 srv
drwxr-xr-x   2 root root  4096 2007-04-04 11:27 sys
drwxrwxrwt   2 root root  4096 2007-09-01 13:04 tmp
drwxr-xr-x  11 root root  4096 2007-04-15 13:43 usr
drwxr-xr-x  15 root root  4096 2007-04-15 14:01 var
ubuntu@ubuntu:~$ ls -l /media/disk/etc
total 1160
drwxr-xr-x  6 root root      4096 2007-04-15 13:45 acpi
-rw-r--r--  1 root root      2657 2007-04-15 13:42 adduser.conf
-rw-r--r--  1 root root        44 2007-04-15 13:41 adjtime
-rw-r--r--  1 root root        50 2007-09-01 13:00 aliases
drwxr-xr-x  2 root root      4096 2007-04-15 14:02 alternatives
-rw-r--r--  1 root root       395 2007-03-05 08:14 anacrontab
drwxr-xr-x  6 root root      4096 2007-04-15 13:45 apm
drwxr-xr-x  4 root root      4096 2007-09-01 13:01 apt
-rw-r-----  1 root daemon     144 2007-02-20 13:43 at.deny
drwxr-xr-x  4 root root      4096 2007-04-15 13:52 avahi
-rw-r--r--  1 root root      1566 2007-04-11 00:31 bash.bashrc
-rw-r--r--  1 root root       278 2007-04-10 07:34 bash_command_not_found
-rw-r--r--  1 root root    215938 2007-04-11 00:31 bash_completion
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 bash_completion.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 belocs
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 bluetooth
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 bonobo-activation
-rw-r--r--  1 root root        33 2007-04-15 13:58 brlapi.key
drwxr-xr-x  2 root root      4096 2007-04-15 14:02 brltty
-rw-r--r--  1 root root     13262 2007-03-27 12:39 brltty.conf
-rw-r--r--  1 root root      4832 2007-04-15 13:52 ca-certificates.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 calendar
-rw-r--r--  1 root root       230 2007-04-10 07:51 casper.conf
drwxr-s---  2 root dip       4096 2007-04-15 13:52 chatscripts
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 console-setup
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 console-tools
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 cron.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:57 cron.daily
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 cron.hourly
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 cron.monthly
-rw-r--r--  1 root root       724 2006-12-20 14:50 crontab
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 cron.weekly
drwxr-sr-t  5 root lp        4096 2007-04-15 13:58 cups
drwxr-xr-x  4 root root      4096 2007-04-15 13:50 dbus-1
-rw-r--r--  1 root root      2673 2007-03-24 17:35 debconf.conf
-rw-r--r--  1 root root         4 2006-10-28 13:20 debian_version
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 default
drwxr-xr-x  4 root root      4096 2007-04-15 13:58 defoma
-rw-r--r--  1 root root       600 2006-11-28 10:47 deluser.conf
drwxr-xr-x  3 root root      4096 2007-04-15 13:48 devfs
drwxr-xr-x  4 root root      4096 2007-04-15 13:42 dhcp3
drwxr-xr-x  2 root root      4096 2007-04-15 14:03 dictionaries-common
-rw-r--r--  1 root root       646 2007-03-27 13:44 discover.conf
-rw-r--r--  1 root root       197 2007-03-27 13:44 discover.conf-2.6
drwxr-xr-x  3 root root      4096 2007-04-15 14:03 discover.d
drwxr-xr-x  3 root root      4096 2007-04-15 13:52 dpkg
drwxr-xr-x  3 root root      4096 2007-04-15 13:44 emacs
-rw-r--r--  1 root root        98 2007-09-01 13:00 environment
drwxr-xr-x  2 root root      4096 2007-04-15 13:50 esound
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 event.d
-rw-r--r--  1 root root       354 2007-03-05 08:39 fdmount.conf
drwxr-xr-x  4 root root      4096 2007-04-15 13:59 firefox
drwxr-xr-x  4 root root      4096 2007-04-15 13:49 fonts
drwxr-xr-x  3 root root      4096 2007-04-15 13:49 foomatic
-rw-r--r--  1 root root       476 2007-04-15 13:42 fstab
-rw-r--r--  1 root root        37 2007-04-15 13:41 fstab.pre-uuid
drwxr-xr-x  2 root root      4096 2007-04-15 13:53 gaim
drwxr-xr-x  2 root root      4096 2007-04-15 13:58 gamin
drwxr-xr-x  5 root root      4096 2007-04-15 13:43 gconf
drwxr-xr-x  7 root root      4096 2007-04-15 14:00 gdm
drwxr-xr-x  3 root root      4096 2007-04-15 13:47 gimp
drwxr-xr-x  3 root root      4096 2007-04-15 13:51 gnome
drwxr-xr-x  2 root root      4096 2007-04-15 14:00 gnome-app-install
drwxr-xr-x  3 root root      4096 2007-04-15 13:49 gnome-system-tools
drwxr-xr-x  4 root root      4096 2007-04-15 13:44 gnome-vfs-2.0
-rw-r--r--  1 root root     10852 2006-11-09 19:16 gnome-vfs-mime-magic
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 gre.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 groff
-rw-r--r--  1 root root       870 2007-09-01 13:00 group
-rw-------  1 root root       865 2007-09-01 13:00 group-
-rw-r-----  1 root shadow     737 2007-09-01 13:00 gshadow
-rw-------  1 root root       732 2007-09-01 13:00 gshadow-
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 gtk-2.0
drwxr-xr-x  3 root root      4096 2007-04-15 13:47 hal
-rw-r--r--  1 root root      4793 2007-03-05 04:58 hdparm.conf
-rw-r--r--  1 root root        92 2006-12-20 15:50 host.conf
-rw-r--r--  1 root root        14 2007-09-01 13:00 hostname
-rw-r--r--  1 root root       249 2007-09-01 13:00 hosts
drwxr-xr-x  2 root root      4096 2007-04-15 13:58 hp
-rw-r--r--  1 root root       121 2007-09-01 13:00 iftab
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 init.d
drwxr-xr-x  5 root root      4096 2007-04-15 13:42 initramfs-tools
-rw-r--r--  1 root root      1723 2007-04-10 21:46 inputrc
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 iproute2
-rw-r--r--  1 root root        19 2007-04-12 09:11 issue
-rw-r--r--  1 root root        12 2007-04-12 09:11 issue.net
drwxr-xr-x  3 root root      4096 2007-04-15 13:46 java
-rw-r--r--  1 root root       112 2007-04-15 13:42 kernel-img.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 ldap
-rw-r--r--  1 root root     36163 2007-04-15 14:03 ld.so.cache
-rw-r--r--  1 root root        33 2007-04-15 13:41 ld.so.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 ld.so.conf.d
-rw-r--r--  1 root root      3300 2007-03-07 14:11 lftp.conf
-rw-r--r--  1 root root        22 2006-07-01 17:00 libao.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 libgda
drwxr-xr-x  2 root root      4096 2007-03-05 21:37 libpaper.d
-rw-r--r--  1 root root      2586 2003-12-04 07:57 locale.alias
-rw-r--r--  1 root root       606 2007-09-01 13:01 localtime
drwxr-xr-x  4 root root      4096 2007-04-15 13:48 logcheck
-rw-r--r--  1 root root      9707 2006-12-19 20:36 login.defs
-rw-r--r--  1 root root       599 2006-06-19 16:51 logrotate.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:58 logrotate.d
drwxr-xr-x  2 root root      4096 2007-04-10 18:44 lsb-base
-rw-r--r--  1 root root      3786 2007-04-10 13:25 lsb-base-logging.sh
-rw-r--r--  1 root root        97 2007-04-12 06:02 lsb-release
-rw-r--r--  1 root root     10814 2006-02-20 21:55 ltrace.conf
-rw-r--r--  1 root root       111 2007-03-24 16:35 magic
-rw-r--r--  1 root root     12871 2007-04-15 14:01 mailcap
-rw-r--r--  1 root root       449 2006-12-06 18:13 mailcap.order
-rw-r--r--  1 root root      4696 2007-04-05 19:48 manpath.config
-rw-r--r--  1 root root     11742 2007-03-05 08:40 mediaprm
drwxr-xr-x  2 root root      4096 2007-04-15 13:51 menu-methods
-rw-r--r--  1 root root     20847 2006-12-06 18:13 mime.types
-rw-r--r--  1 root root       330 2007-03-28 13:46 mke2fs.conf
drwxr-xr-x  3 root root      4096 2007-04-15 14:03 modprobe.d
-rw-r--r--  1 root root       226 2007-09-01 13:03 modules
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 modutils
drwxr-xr-x  4 root root      4096 2007-04-15 13:53 mono
lrwxrwxrwx  1 root root        13 2007-09-01 12:49 motd -> /var/run/motd
-rw-r--r--  1 root root       266 2007-04-15 13:42 motd.tail
-rw-r--r--  1 root root       185 2007-09-01 13:04 mtab
-rw-r--r--  1 root root      7672 2007-02-07 11:32 nanorc
-rw-r--r--  1 root root       611 2007-03-06 02:05 Net
-rw-r--r--  1 root root      2064 2006-11-23 19:33 netscsid.conf
drwxr-xr-x  6 root root      4096 2007-04-15 13:42 network
drwxr-xr-x  3 root root      4096 2007-04-15 13:48 NetworkManager
-rw-r--r--  1 root root        91 2006-12-20 15:50 networks
lrwxrwxrwx  1 root root        28 2007-09-01 12:49 nologin -> /var/lib/initscripts/nologin
-rw-r--r--  1 root root       513 2007-04-15 13:53 nsswitch.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 openoffice
drwxr-xr-x  2 root root      4096 2007-04-15 13:41 opt
-rw-r--r--  1 root root       552 2006-12-20 17:58 pam.conf
drwxr-xr-x  2 root root      4096 2007-04-15 14:01 pam.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:50 pango
-rw-r--r--  1 root root         3 2007-04-15 13:51 papersize
-rw-r--r--  1 root root      1330 2007-09-01 13:00 passwd
-rw-------  1 root root      1316 2007-09-01 13:00 passwd-
-rw-r--r--  1 root root      3604 2007-03-07 22:02 pbbuttonsd.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 pcmcia
drwxr-xr-x  4 root root      4096 2007-04-15 13:42 perl
-rw-r--r--  1 root root      7649 2007-04-15 13:59 pnm2ppa.conf
-rw-r--r--  1 root root       342 2007-09-01 13:03 popularity-contest.conf
drwxr-xr-x  4 root root      4096 2007-04-15 13:54 power
drwxr-xr-x  8 root dip       4096 2007-04-15 13:52 ppp
drwxr-xr-x  2 root root      4096 2006-11-27 15:39 pppstatus
-rw-r--r--  1 root root       369 2007-04-15 13:42 profile
-rw-r--r--  1 root root      2478 2007-03-30 09:46 protocols
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 python
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 python2.5
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc0.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc1.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc2.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc3.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc4.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc5.d
drwxr-xr-x  2 root root      4096 2007-09-01 13:03 rc6.d
-rwxr-xr-x  1 root root       306 2007-04-15 13:42 rc.local
drwxr-xr-x  2 root root      4096 2007-04-15 13:58 rcS.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:54 readahead
drwxr-xr-x  3 root root      4096 2007-04-15 13:45 resolvconf
-rw-r--r--  1 root root        23 2007-09-01 16:33 resolv.conf
-rwxr-xr-x  1 root root       268 2006-12-18 13:45 rmt
-rw-r--r--  1 root root       887 2007-03-30 09:46 rpc
drwxr-xr-x  2 root root      4096 2007-04-15 13:54 samba
drwxr-xr-x  3 root root      4096 2007-04-15 13:53 sane.d
drwxr-xr-x  2 root root      4096 2007-04-15 13:59 scim
-rw-r--r--  1 root root      3578 2007-03-08 17:14 screenrc
-rw-r--r--  1 root root        23 2007-03-09 13:44 scrollkeeper.conf
-rw-r--r--  1 root root       994 2006-12-19 20:36 securetty
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 security
-rw-r--r--  1 root root     18038 2007-03-30 09:46 services
drwxr-xr-x  3 root root      4096 2007-04-15 13:51 sgml
-rw-r-----  1 root shadow     820 2007-09-01 13:00 shadow
-rw-------  1 root root       787 2007-09-01 13:00 shadow-
-rw-r--r--  1 root root       181 2007-04-15 13:52 shells
drwxr-xr-x  2 root root      4096 2007-04-15 13:46 skel
drwxr-xr-x  3 root root      4096 2007-04-15 13:43 sound
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 ssh
drwxr-xr-x  4 root root      4096 2007-04-15 13:52 ssl
-r--r-----  1 root root       403 2007-09-01 13:00 sudoers
-rw-r--r--  1 root root       949 2007-03-07 21:50 sysctl.conf
-rw-r--r--  1 root root      1664 2007-03-08 16:47 syslog.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 terminfo
-rw-r--r--  1 root root        29 2007-09-01 13:01 timezone
-rw-r--r--  1 root root      1260 2006-11-16 19:35 ucf.conf
drwxr-xr-x  3 root root      4096 2007-04-15 13:53 udev
-rw-r--r--  1 root root       142 2007-02-05 10:56 uniconf.conf
-rw-r--r--  1 root root       805 2007-03-05 08:39 updatedb.conf
drwxr-xr-x  2 root root      4096 2007-04-10 07:49 update-notifier
-rw-r--r--  1 root root        48 2007-09-01 13:03 usplash.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 vim
-rw-r--r--  1 root root      4622 2007-03-08 22:17 vnc.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:52 w3m
-rw-r--r--  1 root root      4221 2006-12-13 11:33 wgetrc
-rw-r--r--  1 root root      1343 2007-01-09 18:39 wodim.conf
drwxr-xr-x  2 root root      4096 2007-04-15 13:42 wpa_supplicant
-rw-r-----  1 root dialout     66 2007-04-15 13:58 wvdial.conf
drwxr-xr-x 10 root root      4096 2007-09-01 13:00 X11
drwxr-xr-x  4 root root      4096 2007-04-15 13:46 xdg
drwxr-xr-x  2 root root      4096 2007-04-15 13:50 xml
-rw-r--r--  1 root root       399 2007-03-30 09:52 zsh_command_not_found
ubuntu@ubuntu:~$ cat /media/disk/etc/yaboot.conf
cat: /media/disk/etc/yaboot.conf: No such file or directory
ubuntu@ubuntu:~$ sudo find /media/disk -name yaboot*
/media/disk/var/lib/dpkg/info/yaboot.list
/media/disk/var/lib/dpkg/info/yaboot.postinst
/media/disk/var/lib/dpkg/info/yaboot.md5sums
/media/disk/usr/sbin/yabootconfig
/media/disk/usr/share/man/de/man8/yaboot.8.gz
/media/disk/usr/share/man/man8/yabootconfig.8.gz
/media/disk/usr/share/man/man8/yaboot.8.gz
/media/disk/usr/share/man/man5/yaboot.conf.5.gz
/media/disk/usr/share/lintian/overrides/yaboot
/media/disk/usr/share/doc/yaboot
/media/disk/usr/share/doc/yaboot/yaboot-howto.html
/media/disk/usr/share/doc/yaboot/yaboot-howto.de.sgml.gz
/media/disk/usr/share/doc/yaboot/examples/yaboot.conf.multi-boot
/media/disk/usr/share/doc/yaboot/examples/yaboot.conf.rs6000
/media/disk/usr/share/doc/yaboot/yaboot-howto.sgml.gz
/media/disk/usr/lib/yaboot
/media/disk/usr/lib/yaboot/yaboot
/media/disk/usr/lib/ubiquity/ubiquity/components/yabootinstaller.py
/media/disk/usr/lib/ubiquity/ubiquity/components/yabootinstaller.pyc
/media/disk/usr/lib/ubiquity/yaboot-installer
/media/disk/usr/lib/ubiquity/yaboot-installer/yaboot-installer
ubuntu@ubuntu:~$ 

```

---

### Post by pxwpxw on 2007-09-26
Well, the bad news is that /etc/yaboot.conf is missing, which means that yaboot did not get installed from /usr/lib/yaboot to the bootstrap partition, and so thats why you could not boot it.

But the good news is I now have enough information to look at. I will try to see if it can be fixed without re-installing. Everything else seems to be installed. And there are some small free partitions on both drives that could be used for a boot partition, for example, in /proc/partitions -

  8    15     131072 sda15
    that is size 131072 Kb = 131 Megabytes.

The big boot partition you made seems to have gone into free space, but let me have a good look at it tomorrow, meanwhile, enjoy the live cd.:)

---

### Post by computer geek on 2007-09-26
ok.

---

### Post by stmiller on 2007-09-26
Hey pxwpxw, do you think it is possible to install Ubuntu via the firewire target mode? I noticed that target mode works, and is not dependent on OS X. Not that I need to do this at the moment, but I wonder if it could work. ?

---

### Post by computer geek on 2007-09-26
I would kind of like to use yaboot

---

### Post by pxwpxw on 2007-09-27
> **stmiller said:**
> Hey pxwpxw, do you think it is possible to install Ubuntu via the firewire target mode? I noticed that target mode works, and is not dependent on OS X. Not that I need to do this at the moment, but I wonder if it could work. ?
Maybe you can install to a target computer, but expect prblems sorting out O/Fware paths and device names,  because they change according to host computer system.
 Not quite  the same as installing to a firewire disk to run as a firewire on the same host. Had a thread on this somewhere, there were problems.  Try it.

---

### Post by pxwpxw on 2007-09-27
> **computer geek said:**
> I would kind of like to use yaboot

While I am thinking about fixing yaboot, would you please do these 3 commands in the ubuntu desktop terminal, and after each one copy and paste all the text to this thread, as you did before.
This will save time later with desktop graphics for the eMac.

```

 cat /etc/X11/xorg.conf 

 cat /media/disk/etc/X11/xorg.conf 

 lspci

```

---

### Post by computer geek on 2007-09-27
Here are the outputs of the commands that you gave me.




```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "iMac"
        Option          "DPMS"
        HorizSync       71-73
        VertRefresh     70-140
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200]"
        Monitor         "iMac"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
ubuntu@ubuntu:~$ cat /media/disk/etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "iMac"
        Option          "DPMS"
        HorizSync       71-73
        VertRefresh     70-140
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200]"
        Monitor         "iMac"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
ubuntu@ubuntu:~$  lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
ubuntu@ubuntu:~$ 
```

---

### Post by pxwpxw on 2007-09-27
Thats good, can you also post the output from
```

ls -l /media/disk/boot/

```

Should be able to try booting again soon.

First -

1. See if you can locate some free space on your external drive.

In the Ubuntu desktop:

open Gparted from Menubar-System-Administration-Gnome Partition Editor

Click Gparted-Devices-/dev/sda (your external firewire drive )
 Look at the bottom to see if there is an "unallocated" entry, and what size it is

See the attached screenshots, showing this for some unallocated space in my /dev/sdb.

If you have some space you can create a 2Gb hfs partition to transfer files between Macosx and Ubuntu ( I have some more screenshots for doing that).

2, Then from Macosx - copy yaboot from your Desktop CD to the root of your Masosx partition (volume)

yaboot is in the Desktop CD Install folder, size about 156 KB

You will also need a yaboot.conf file. I will post that when I have the list of files in your firewire ubuntu /boot folder.
 And I will post the instructions to boot your firewire using yaboot on the Macosx partition.

---

### Post by computer geek on 2007-09-27
Here is the output of,

```
ls -l /media/disk/boot/
```



```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ls -l /media/disk/boot
total 13764
-rw-r--r-- 1 root root  386247 2007-04-15 06:47 abi-2.6.20-15-powerpc
-rw-r--r-- 1 root root   71267 2007-04-15 05:03 config-2.6.20-15-powerpc
lrwxrwxrwx 1 root root      28 2007-09-01 13:04 initrd.img -> initrd.img-2.6.20-15-powerpc
-rw-r--r-- 1 root root 8277376 2007-09-01 13:04 initrd.img-2.6.20-15-powerpc
-rw-r--r-- 1 root root  738673 2007-04-15 06:47 System.map-2.6.20-15-powerpc
lrwxrwxrwx 1 root root      25 2007-09-01 13:04 vmlinux -> vmlinux-2.6.20-15-powerpc
-rw-r--r-- 1 root root 4572309 2007-04-15 06:47 vmlinux-2.6.20-15-powerpc
ubuntu@ubuntu:~$ 



```

---

### Post by computer geek on 2007-09-27
where is the yaboot file in osx?

there is no usr folder in the disk in osx.
and i have a 2gb camera chip.

---

### Post by computer geek on 2007-09-27
[page 6]("http://ubuntuforums.org/showthread.php?t=541816&page=6")

---

### Post by pxwpxw on 2007-09-28
> **computer geek said:**
> where is the yaboot file in osx?

there is no usr folder in the disk in osx.
and i have a 2gb camera chip.

yaboot is in the install folder on your Ubuntu Desktop CD. 
In Macosx, just open the CD and the install folder and there it is.

Or in the live ubuntu desktop, you can get the yaboot from 

       /media/disk/usr/lib/yaboot/yaboot 
copy it to your 2gb camera chip if you can, then get that from macosx.

In Macosx drag yaboot  to the root (top level) of your Macosx "startup disk"

See these pics:

---

### Post by computer geek on 2007-09-28
will i have to use my camera to boot every time i want to boot ubuntu?

Or... is there another step?

---

### Post by computer geek on 2007-09-28
or... can i put the yaboot in my intrnal hdd?

---

### Post by pxwpxw on 2007-09-28
Ah - I forgot, your macosx is on the external. Thats different.

In that case, it might be a very good idea to put yaboot on th internal Mac partition.
But I need to know what else is on that partition?

But just use Macosx to copy yaboot from the install CD to the internal Mac partition,
forget the camera, that was a bad idea.

---

### Post by computer geek on 2007-09-28
Forget the intrnal hdd.

can you tell me how to make that boot partition?

---

### Post by computer geek on 2007-09-28
ubuntu is on the extrnal hdd and mac os x is on the intrnal hdd

---

### Post by pxwpxw on 2007-09-29
From Macosx, post a screen shot of your "About This Mac" and the top right corner of the screen showing your startup disk. I need this before I can do any more.

Here is what I mean:

---

### Post by computer geek on 2007-09-29
Here!

---

### Post by pxwpxw on 2007-09-30
Not quite what I need. 
Please post it again this time showing the desktop icons in the top right exactly like my example above where I have shown the red macosx icon which is my  startup disk icon.

---

### Post by computer geek on 2007-09-30
sorry about that.

---

### Post by pxwpxw on 2007-09-30
Here is yaboot.conf for your external system to restart it.
```

######yaboot.conf##########
# this firewire boot uses the kernel files on the external root at /dev/sda14/
#
timeout=10
#
#
image=/boot/vmlinux
root=/dev/sda14
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=14
##end yaboot.conf####

```

In Macosx, 

Copy it from here to a file and name it yaboot.conf

Put it in the root of your Macosx startup disk "Computer"
with a copy of yaboot from the Ubuntu feisty CD. It is in the install folder on the CD. 

So you have yaboot and yaboot.conf in the top level of Computer,  partition #10 on the internal HD.

Picture below shows my macosx startup disk "p1" with yaboot and yaboot.conf  

Please post a similar screen shot of your "Computer" files to confirm you have it right.

Set your boot-device to try the new external boot

```

 nvram boot-device
### save the result
## then set it to boot yaboot
 sudo nvram boot-device="hd:10,yaboot"
## then chack your setting again
 nvram boot-device

```
 
Restart the computer and it should start the external ubuntu, but you wont see anything of yaboot at the start.

If you get in trouble I am assuming you can run the Ubuntu Live CD and post here for help.

Also see these two other  threads for more information.
[http://ubuntuforums.org/showthread.php?t=562193](http://ubuntuforums.org/showthread.php?t=562193)
[http://ubuntuforums.org/showthread.php?t=561167](http://ubuntuforums.org/showthread.php?t=561167)

Good luck.

---

### Post by computer geek on 2007-09-30
here is part.

```
Last login: Sun Sep 30 14:02:33 on ttyp1
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ sudo nvram boot-device="hd:10,yaboot"
Password:
Stephen-Rhodas-Computer-2:~ Jacob$ nvram boot-device
boot-device     hd:10,yaboot
Stephen-Rhodas-Computer-2:~ Jacob$ 

```

---

### Post by computer geek on 2007-09-30
I just got an airport card and i ant to use it with linix.

How?

---

### Post by computer geek on 2007-09-30
Is it all of the,

```
######yaboot.conf##########
# this firewire boot uses the kernel files on the external root at /dev/sda14/
#
timeout=10
#
#
image=/boot/vmlinux
root=/dev/sda14
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=14
##end yaboot.conf####
```


or just,

```
######yaboot.conf##########
timeout=10
#
#
image=/boot/vmlinux
root=/dev/sda14
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=14
##end yaboot.conf#### 
```

---

### Post by computer geek on 2007-09-30
ca i boot os x from yaboot? I WOULD REALLY REALLY LIKE TO DO THAT.:)

---

### Post by pxwpxw on 2007-09-30
> **computer geek said:**
> Is it all of the,

```

######yaboot.conf##########
# this firewire boot uses the kernel files on the external root at /dev/sda14/
#
timeout=10
#
#
image=/boot/vmlinux
root=/dev/sda14
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=14
##end yaboot.conf####
```


That one. The lines stating with # are just comments, they don't matter.

---

### Post by pxwpxw on 2007-09-30
> **computer geek said:**
> here is part.

```
Last login: Sun Sep 30 14:02:33 on ttyp1
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ sudo nvram boot-device="hd:10,yaboot"
Password:
Stephen-Rhodas-Computer-2:~ Jacob$ nvram boot-device
boot-device     hd:10,yaboot
Stephen-Rhodas-Computer-2:~ Jacob$ 

```

Yes that is right.

---

### Post by pxwpxw on 2007-09-30
> **computer geek said:**
> ca i boot os x from yaboot? I WOULD REALLY REALLY LIKE TO DO THAT.:)

Nope, cant do that.

---

### Post by computer geek on 2007-10-01
can we try?

Why cant we do a boot partition on the Extrnal HDD?

---

### Post by computer geek on 2007-10-01
This is what i have for yaboot.conf

```
######yaboot.conf##########
# 
#
timeout=10
#
#
image=/boot/vmlinux
root=/dev/sda14
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=14
##end yaboot.conf####
```

---

### Post by pxwpxw on 2007-10-01
Looks ok.

---

### Post by computer geek on 2007-10-01
now i will restart

---

### Post by computer geek on 2007-10-01
did not work.

I got a gray screen and then paniced and zaped the pram

---

### Post by pxwpxw on 2007-10-01
Try it again and this time wait for a few minutes, sometimes you dont see anything for a while.

---

### Post by computer geek on 2007-10-01
I left it for quite some time and got gray screen.

should we use all of the documents that install folder?

---

### Post by pxwpxw on 2007-10-01
The grey screen means you might just have the yaboot.conf file in the wrong place.

In Macosx, open a terminal, copy and paste this command into the terminal 
 and post the output.
```

sudo find -d /  -name "yab*"

```

---

### Post by computer geek on 2007-10-01
Here

```
Last login: Mon Oct  1 10:27:42 on console
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ sudo find -d /  -name "yab*"
Password:
/System Folder/Apple Menu Items/Recent Documents/yaboot.conf
/Users/Jacob/.Trash/yaboot.conf
/Users/Jacob/.Trash/yaboot.conf.rtf
/Volumes/Ubuntu_PowerPC_feisty/etc/yaboot.conf
/Volumes/Ubuntu_PowerPC_feisty/install/yaboot
/Volumes/Ubuntu_PowerPC_feisty/install/yaboot.conf
/yaboot
/yaboot.conf.txt
Stephen-Rhodas-Computer-2:~ Jacob$ 
```

---

### Post by pxwpxw on 2007-10-01
Yes thats the problem, 
yaboot.conf.txt 
should be
yaboot.conf

They are in your Computer startup disk at root level where they should be.

Just rename yaboot.conf.txt  to  yaboot.conf
and then try it all again.

---

### Post by computer geek on 2007-10-01
OK, now i am in ubuntu.

I want to use my Airport card. Can you tell me how to confugire that?


and i got no yaboot screen. it went right into ubuntu.

oh. when i put ubuntu on the whole Extrnal HDD i was able to boot os x with yaboot. probly because it had all of the yaboot install things on there.

---

### Post by pxwpxw on 2007-10-02
> **computer geek said:**
> OK, now i am in ubuntu.

Well done. :popcorn:


> 
I want to use my Airport card. Can you tell me how to confugire that?

**post output from this to see what you have**
```

 lspci

```


> 
and i got no yaboot screen. it went right into ubuntu.

That is for the temporary boot from yaboot. You will have to use the Option key at start to get a Macosx icon for now.


> 
oh. when i put ubuntu on the whole Extrnal HDD i was able to boot os x with yaboot. probly because it had all of the yaboot install things on there.

 I will post how to do a full yaboot install. That will do what you want for macosx or ubuntu.
**Please post a copy of /etc/yaboot.conf from ubuntu (on the external)**

---

### Post by computer geek on 2007-10-02
Here is the output for  ```
lspci
```

```
jacob@jacob-desktop:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
jacob@jacob-desktop:~$ 

```

---

### Post by pxwpxw on 2007-10-02
Right, you need bcm43xx-fwcutter.
Coming up.

---

### Post by computer geek on 2007-10-02
OH Oh! No yaboot in "etc/yaboot/" But in "Usr/lib/yaboot/"

---

### Post by pxwpxw on 2007-10-02
Thats ok, I forgot, that answers my question. heres the wireless info for you.

(EDITED)

To install the bcm43xx-fwcutter firmware package for your Broadcom wireless card. 

[B]EDIT: The package here does not work do not use it.
Ubuntu PowerPC FAQ
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
Setion 4. Drivers and Hardware[/B]

 [COLOR="Green"]USE The bcm43xx compwiz18.1-all.deb  package from this link
[/COLOR][http://www.speedyshare.com/214793933.html]("http://www.speedyshare.com/214793933.html")
 If the link is down there is a copy of the package attached at the bottom of this post. It is only 30Kb.

See this link for discussion.
( **makinasvp :  I have a fix for the wireless internet!!** )
[http://ubuntuforums.org/showthread.php?t=526901](http://ubuntuforums.org/showthread.php?t=526901)



1. Install the wireless driver firmware package.

**EDIT: This lengthy procedure was for xubuntu network-admin (xubuntu-system-tools package) with no menu panel Network Applet, it was simpler for ubuntu using the NetworkManager Applet in the top menu bar, as found in the Ubuntu Feisty Desktop Live CD. **
It might be easier with [COLOR="Red"]wicd[/COLOR] See post #109 further down by [ guidop]("http://ubuntuforums.org/member.php?u=32348")

2. Restart with your wireless router running.
It might work now, but you will probably have to check your network manager configuration, to enable wireless and disable the wired connection.

3. In your network manager it should show a wireless connection.

   Look at the configuration settings for the wired connection and note them in case you want to change back to a wired connection (or get screen shots) 

   Set up the wireless properties and enable it.

   Disable the wired connection in its properties and connections.

It is essential you disable the wired connnection to get the wireless started.
If you want to use local sharing, sort that out later.

4. If you have firestarter or other firewall manager,
   enable internet connection for the wireless device (eth1 or eth0 ). If it won't let you, then do this after the restart. 

5. Restart again, it should work, you might have to check the firewall again. 

If it fails, restore the wired connection settings, disable wireless, and restart, restore the firewall, and get more help.

---

### Post by computer geek on 2007-10-02
I lost my network icon in my top toolbar! how do i get it back?

---

### Post by computer geek on 2007-10-02
that is ```
 bcm43xx compwiz18.1-all.deb
```

not, ```
bcm43xx-fwcutter
```.



but i found a bcm43xx-fwcutter on a google search.

---

### Post by pxwpxw on 2007-10-02
> **computer geek said:**
> that is ```
 bcm43xx compwiz18.1-all.deb
```

not, ```
bcm43xx-fwcutter
```.

but i found a bcm43xx-fwcutter on a google search.

Wait, what have you downloaded or installed so far?
Don't try anything else just yet.

---

### Post by computer geek on 2007-10-02
I installed bcm43xx-fwcutter. but not working.

---

### Post by pxwpxw on 2007-10-02
> **computer geek said:**
> I installed bcm43xx-fwcutter. but not working.

Was that the one from the PowerPC FAQ?

---

### Post by computer geek on 2007-10-02
i don't know. but i pcked a one that said ppc.

---

### Post by pxwpxw on 2007-10-02
Is your network still working in ubuntu?

Please post the output from
```

  find /lib/  -name bcm*

```

---

### Post by computer geek on 2007-10-02
here,

```
jacob@jacob-desktop:~$ find /lib/  -name bcm*
/lib/modules/2.6.20-15-powerpc/kernel/ubuntu/wireless/bcm43xx
/lib/modules/2.6.20-15-powerpc/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/media/dvb/frontends/bcm3510.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/net/wireless/bcm43xx
/lib/modules/2.6.20-15-powerpc/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/bluetooth/bcm203x.ko
jacob@jacob-desktop:~$ 
jacob@jacob-desktop:~$ 
```

---

### Post by pxwpxw on 2007-10-02
> **computer geek said:**
> here,

```
jacob@jacob-desktop:~$ find /lib/  -name bcm*
/lib/modules/2.6.20-15-powerpc/kernel/ubuntu/wireless/bcm43xx
/lib/modules/2.6.20-15-powerpc/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/media/dvb/frontends/bcm3510.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/net/wireless/bcm43xx
/lib/modules/2.6.20-15-powerpc/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.20-15-powerpc/kernel/drivers/bluetooth/bcm203x.ko
jacob@jacob-desktop:~$ 
jacob@jacob-desktop:~$ 
```

Good. Nothing got installed, probably no harm done, but you must keep a note of what you do  and what happens,  in case there is a problem.
Do not try to install anything now until I give you more instruction, just read this.

Is your wired (ethernet) connection still OK? 

I am posting this from the Ubuntu Desktop CD, and I am using Wireless.
So I will post how to get wireless running on the Desktop CD, and you can try it that way first.
That way if anyting goes wrong, no problem, you just restart from the CD.
Then when you see how tthat goes  with the Desktop CD, you can go back and get  wireless running from your ubuntu system on the external drive.

I tried the bcm43xx-fwcutter package from the PpwerPC FAQ section 4, and it is BROKEN it DOES NOT WORK.

So I used the other  bcm43xx compwiz18.1-all.deb package, no problems, just click to download and unpack and install, then enable wireless in the Network Applet in the Menu Bar. No restart was needed. 
Do not  try to install any other packages until this one is finished.. 

Please post when you are ready, and tell me if there are any problems with your wired network connection now.

---

### Post by computer geek on 2007-10-03
I am typing from os x.

because i could nott get wirless to work.
i got 55% because i am downstairs in the basment.
but fire fox did not load one page.

---

### Post by pxwpxw on 2007-10-03
So did you get wireless set up?

---

### Post by computer geek on 2007-10-03
yes but had no way to tell that it was working.

---

### Post by pxwpxw on 2007-10-03
What about security - WEP or WPA - did you get logged into the wireless network?

---

### Post by computer geek on 2007-10-03
WPA Personal

---

### Post by pxwpxw on 2007-10-03
The standard wireless installation does not do WPA, only WEP,  you need to change your wireless router to WEP security to log in and get it going.
You can find out how to set up WPA later,

Also make sure the router is configured to accept 11Mbps "b" bitrate, it will probably be set for "b/g" which is OK,  but might be just on "g" the faster bitrate which will stop it working .

---

### Post by computer geek on 2007-10-04
I can't chang my roughter to b/g. it is a =n airport extreme base station.

---

### Post by computer geek on 2007-10-04
can i do not a standed install and do an extreme install? so i can use WPA Personal.

---

### Post by pxwpxw on 2007-10-04
> **computer geek said:**
> I can't chang my roughter to b/g. it is a =n airport extreme base station.

Look up the specs on apple.com:

(3) The AirPort Extreme Base Station is based on an IEEE 802.11n draft specification and is compatible with IEEE 802.11a, IEEE 802.11b, and IEEE 802.11g.

---

### Post by pxwpxw on 2007-10-04
> **computer geek said:**
> can i do not a standed install and do an extreme install? so i can use WPA Personal.

No

---

### Post by computer geek on 2007-10-05
these are my conforations.

---

### Post by pxwpxw on 2007-10-05
> **computer geek said:**
> these are my conforations.

Just change the Base Station [Wireless Security] to WEP 128 bit.
Set the password.
Then change Macosx to use WEP and get it working from Macosx. 

If there are other computers using the Airport base station, they will have to be changed also to let you get started with WEP. I am assumng you have your Airport Extreme Base station already set up for connection to the internet.

Then configure Ubuntu using the NetworkManager icon in the menubar, but do a restart after making changes.

For WPA your Ubuntu Feisty  should have the wpasupplicant package with wpa_supplicant alrady installed, (try man wpa_supplicant) but it needs to be configured. 

I can't help you any further with the wireless configuration. I hope someone else can.

You should read the Airport base station manual, and there are other threads about setting up for WPA or you can post another thread for help with that and the base station if you need it.

This howto has a section about configuring wpa_supplicant, you dont need to do any of the installation, that was for earlier ubuntu releases.
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

There is also some information in the Power PC FAQ
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by guidop on 2007-10-05
[**pxwpxw**]("http://ubuntuforums.org/member.php?u=85693") has done a great job of getting you this far.

As discussed in other threads, this should be a relatively easy way to get your Wireless working with WPA.  You will need to download 2 files.  If you cannot get internet connectivity using Ubuntu, use Mac OSX to download the files, then transfer them to your Ubuntu disk, and put them  somewhere convenient, like your Ubuntu /home/<your-user-name>/Desktop directory.

In this post:  [**I have a fix for the wireless internet**]("http://ubuntuforums.org/showpost.php?p=3197840&postcount=1"),  [**makinasvp**]("http://ubuntuforums.org/member.php?u=271047") points to a working version of the Airport Extreme (bcm43xx) driver with the firmware included.  Download the file from this page:
[**http://www.speedyshare.com/214793933.htm**l]("http://www.speedyshare.com/214793933.html").

In this post: [**Re: Digicom wave 54 on Ubuntu 7.04**]("http://ubuntuforums.org/showpost.php?p=3462779&postcount=1"), I give instructions to get and use Wicd for WPA on Airport Extreme under Ubuntu.  Download the "stable" version of Wicd from this page:
[**Sourceforge Wicd Files**]("https://sourceforge.net/project/showfiles.php?group_id=194573")
Wicd is a python script that gives you a GUI for managing your Wifi connections.
I use it instead of network-manager to configure WPA connections on my Powerbook, running Xubuntu 7.04 ppc.  I did this because network-manager on ppc has (or had) a bug which prevents WPA from working.

Here's what I think you need to do:

1 - Download the **bcm43xx_compwiz18.1-all.deb** file from the link above, and put it in ubuntu where you can get to them.

2 - Download the **wicd_1.3.1-all.deb** file from the link above, and put it in ubuntu where you can get to them.

3 - Install the compwiz bcm43xx driver and firmware by double-clicking on the **bcm43xx_compwiz18.1-all.deb** file icon, and following the prompts.

4 - Uninstall the gnome network-manager by typing in a terminal:  **sudo apt-get remove --purge network-manager**

5 - The packages wireless-tools and wpasupplicant should already be installed by default, if not: **sudo apt-get install wireless-tools wpasupplicant**

6 - Double click on the **wicd_1.3.1-all.deb** file and follow the prompts to install it.

7 - Reboot Ubuntu and login again, so the bcm43xx loads (there are faster ways, but this is simplest).  

8 - There should then be a Wicd selection under your "Internet" or "Network" Menu (same menu you would find Firefox browser).

9 - Start Wicd, the GUI should be reasonably self-explanatory.

It _should_ be that simple.


Since from some of your posts, it looks like you may already have working bcm43xx firmware.  You can test it by typing in a terminal: **sudo iwlist eth1 scanning**
```
# NOTE:  EDITED WIRELESS MAC ADDRESS AND ESSID - YOURS WILL BE DIFFERENT
$ sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:01:02:03:04:05
                    ESSID:"WirelessNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-37 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
```

If you see something like the above, you only need to do steps 2, 4, 6, 8 and 9. 
If you see something else, try all the steps.

---

### Post by computer geek on 2007-10-05
bad news!

That did not work!

I typed in my ip and my dns servers it conected right, but firefox did not load any pages.


NOTE: Before you gave me this setup, I installed ```
bcm43xx_fwcutter-all.deb
``` and i saw as i was uninstalling network utility it failed and both commands to remove the wireless tools.

---

### Post by guidop on 2007-10-06
OK.  Not so simple.

First, try some things to find out more about your eMac hardware and OS X setup:

1 - Boot into OSX
2 - Make sure your Airport is connected and you can access internet from OS X
3 - Run /Applications/Utilities/System Profiler
3a - Click on "Hardware" ----- Copy and post what it says.
3b - Click on "Hardware->Airport Card"   or Network -> Airport Card (Depends on whether OS 10.3 or 10.4) ----- Copy and post what it says.  
4 - Open a terminal (/Applications/Utilities/Terminal)
4a - Enter:  ifconfig -u ----- Copy and post the output.
4b - Enter:  ipconfig  getifaddr en1 ----- Copy and post the output


Next, try some things to find out about your Ubuntu install:

5 - Boot into Ubuntu
6 - Open a terminal. (I think you've done this before.)
6a - Enter:  iwconfig  ----- Copy and post the output.
6b - Enter:  lspci  -----  Copy and post the output
6c - Enter:  ifconfig  ----- Copy and post the output.
6d - Enter:  sudo iwlist eth1 scanning ----- Copy and post the output. 
6e - Enter:  uname -r ----- Copy and post the output.
6f - Enter:  type bcm43xx-fwcutter ----- Copy and post the output.
6g - Enter: type wpa_supplicant ----- Copy and post the output.
6h - Enter: type wpa_passphrase ----- Copy and post the output.
6i - Enter:  type network-manager ----- Copy and post the output.
6j - Enter:  ls -l /opt/wicd ----- Copy and post the output.
6k - Enter: cat /etc/apt/sources.list ----- Copy and post the output.


Also, can you provide a link to the exact Airport Extreme Base Station model you have?
It's been a long time since I used one.  Do you have it set to send a message to a computer when it's connected?  I don't know, but this might be a problem.

(I changed to Motorola and Linksys routers and open-source firmware to be able to configure the interfaces and firewall better.)


This should help to show what state your system is in right now, and help plan what to try next.

---

### Post by computer geek on 2007-10-07
Model number is, A1143

---

### Post by guidop on 2007-10-07
Your Airport Extreme Base Station is the current one?  Looks like this?

[http://www.apple.com/airportextreme/specs.html]("http://www.apple.com/airportextreme/specs.html")

When you connect over wireless in OS X, do you get a pop-up window with a message?
(You would probably have set this up on purpose, when you configured the base station.)

I need you to do all the other steps I listed, 1 through 6k, too.

Please, when you do a step, post both the step you did, and the output, for example:

```
Step 3b:  Apple System Profiler -> Network -> Airport Card

AirPort Card Information:

  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	405.1 (3.90.34.0.p18)
  Current Wireless Network:	AirPort is currently turned off

```

I did this on an iMac G5, using a wired Ethernet connection, running OS 10.4.10.  Here, the airport information is under "Network," not "Hardware," like it was in OS 10.3.

Edit:  I have been re-reading the posts in this thread.  I see you are running OS 10.4.10.  I see you already tried some of the steps I asked for.

Please do them again, in case something has been changed by later steps.  - Thanks.

---

### Post by computer geek on 2007-10-08
Here, ```
AirPort Card Information:

  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	405.1 (3.90.34.0.p18)
  Current Wireless Network:	Rhodaccess
  Wireless Channel:	6
```

output for ```
ifconfig -u
```

```
Last login: Sun Oct  7 07:04:55 on console
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ ifconfig -u
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
        inet 127.0.0.1 netmask 0xff000000 
        inet6 ::1 prefixlen 128 
        inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 00:0d:93:34:3f:00 
        media: autoselect (none) status: inactive
        supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback>
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::21b:63ff:fefe:4a2a%en1 prefixlen 64 scopeid 0x5 
        inet6 2002:4a8c:3b1b::21b:63ff:fefe:4a2a prefixlen 64 autoconf 
        inet 10.0.1.199 netmask 0xffffff00 broadcast 10.0.1.255
        ether 00:1b:63:fe:4a:2a 
        media: autoselect status: active
        supported media: autoselect
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 2030
        lladdr 00:0d:93:ff:fe:34:3f:00 
        media: autoselect <full-duplex> status: inactive
        supported media: autoselect <full-duplex>
Stephen-Rhodas-Computer-2:~ Jacob$ 
```

---

### Post by computer geek on 2007-10-08
```
Hardware Overview:

  Machine Name:	eMac
  Machine Model:	PowerMac6,4
  CPU Type:	PowerPC G4  (1.1)
  Number Of CPUs:	1
  CPU Speed:	1.25 GHz
  L2 Cache (per CPU):	512 KB
  Memory:	768 MB
  Bus Speed:	167 MHz
  Boot ROM Version:	4.8.8f0
  Serial Number:	YM445EQEQJ8
```

Output for ```
ifconfig getifaddr en1
```

```
Last login: Mon Oct  8 11:20:39 on ttyp1
Welcome to Darwin!
Stephen-Rhodas-Computer-2:~ Jacob$ ifconfig getifaddr en1
ifconfig: interface getifaddr does not exist
Stephen-Rhodas-Computer-2:~ Jacob$ ifconfig getifaddr en1
ifconfig: interface getifaddr does not exist
Stephen-Rhodas-Computer-2:~ Jacob$ 
```

---

### Post by guidop on 2007-10-08
Sorry, that last one should be  ipconfig, and you should see:

```
$ ipconfig getifaddr en1
10.0.1.199

```

When you also get a chance, we will want to know the local Airport base address, too.
It's probably 10.0.1.1, or maybe 10.0.1.10.  Try pinging the address (here -c 4 = ping 4 times):

```
$ ping -c 4 10.0.1.1
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=64 time=1.881 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=64 time=1.816 ms
64 bytes from 10.0.1.1: icmp_seq=2 ttl=64 time=1.853 ms
64 bytes from 10.0.1.1: icmp_seq=3 ttl=64 time=1.828 ms

--- 10.0.1.1 ping statistics ---
4 packets transmitted, 4 packets received, 0% packet loss
round-trip min/avg/max = 1.816/1.844/1.881 ms

```

This information that you gave me says we are running the same firmware, so we should be able to get the card working when we get to Ubuntu:

> ```
AirPort Card Information:

  Wireless Card Type:   AirPort Extreme
  Wireless Card Locale: USA
  Wireless Card Firmware Version:       405.1 (3.90.34.0.p18)
  Current Wireless Network:     Rhodaccess
  Wireless Channel:     6

```

The other OSX info will let us know what router address to ping, and what to expect to see when working to set things up in Ubuntu.

---

### Post by computer geek on 2007-10-09
I am so sorry guidop, i tried to put in just my DNS Servers and i conected and i am typing from firefox ubuntu. (I was putting in the IP adderess with DNS Servers.

OK pxwpxw, Can i boot osx in yaboot? Could we make that small boot partition?

---

### Post by guidop on 2007-10-09
You now have Wireless working with WPA and your Airport Extreme base station?

That would be good news!

What exactly did you do?

Are you using Wicd to configure the WPA connection?

When you have time, could you still do the other steps I asked, so others can see what works?

Thanks!

---

### Post by computer geek on 2007-10-09
Ok, first you get your airport DNS Servers, (look at first attachment.) then in Wicd  hit advanced and in there hit advanced, (click the server or wireless network that you wan't,) type in your DNS servers and click connect. once connected close Wicd and go to fire fox and type in a [www.apple.com](www.apple.com) and it should load!

---

### Post by computer geek on 2007-10-10
OK, pxwpxw can you help me some more on yaboot? I have a few questions.

1.Can we make that small boot partition? if we could, I could have a ofboot and then, boot OS X.
2.I can use the option key but that is a hassle. When I used the whole drive to boot Linux, I got a non-graphical boot screen. is that correct?

If not would you know of a way to do that,like the boot screen of choosing between Windows or Mac OS X, on intel macs. Or just have a Human boot screen that i use my arrow keys to pick between boot loaders the temporarily boot of yaboot and apple boot loader?(tell me if i am making this to complicated.)

Computer geek

---

### Post by pxwpxw on 2007-10-11
Before going any further, please post full partition information for both the external and the internal disks. 

From ubuntu (your installation on the external)
```

 sudo mac-fdisk -l

```

From Macosx
```

 sudo pdisk -l

```

---

### Post by computer geek on 2007-10-11
Here is the ```
sudo pdisk -l
```


```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:      Apple_Driver43*Macintosh                   56 @ 64       
 3:      Apple_Driver43*Macintosh                   56 @ 120      
 4:    Apple_Driver_ATA*Macintosh                   56 @ 176      
 5:    Apple_Driver_ATA*Macintosh                   56 @ 232      
 6:      Apple_FWDriver Macintosh                  512 @ 288      
 7:  Apple_Driver_IOKit Macintosh                  512 @ 800      
 8:       Apple_Patches Patch Partition            512 @ 1312     
 9:          Apple_Free                         262144 @ 1824      (128.0M)
10:           Apple_HFS Apple_HFS_Untitled_1 321408976 @ 263968    (153.3G)
11:          Apple_Free                             16 @ 321672944

Device block size=512, Number of Blocks=321672960 (153.4G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1:  23 @ 64, type=0x1
2:  36 @ 120, type=0xffff
3:  21 @ 176, type=0x701
4:  34 @ 232, type=0xf8ff

```

---

### Post by computer geek on 2007-10-11
Here is the output for,  ```
sudo mac-fdisk -l
```




```
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
/dev/sda15             Apple_Free Extra                 262144 @ 584942184 (128.0M)  Free space
/dev/sda16        Apple_Bootstrap Apple_HFS_Untitled_4  39938104 @ 585204328 ( 19.0G)  NewWorld bootblock
/dev/sda17             Apple_Free Extra                     16 @ 625142432 (  8.0k)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/hda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/hda9              Apple_Free                       262144 @ 1824      (128.0M)  Free space
/dev/hda10              Apple_HFS Apple_HFS_Untitled_1 321408976 @ 263968    (153.3G)  HFS
/dev/hda11             Apple_Free                           16 @ 321672944 (  8.0k)  Free space

Block size=512, Number of Blocks=321672960
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

jacob@jacob-desktop:~$ 


```

---

### Post by pxwpxw on 2007-10-11
Also need pdisk for the external disk, it should show that also.

---

### Post by computer geek on 2007-10-11
so like... ```
sudo mac-pdisk -l
``` or what?

---

### Post by pxwpxw on 2007-10-11
The external drive must be running
post from macosx
```

 diskutil list
 sudo pdisk -l

```

---

### Post by computer geek on 2007-10-11
output for,  ```
sudo pdisk -l
```
```
Password:

Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:      Apple_Driver43*Macintosh                   56 @ 64       
 3:      Apple_Driver43*Macintosh                   56 @ 120      
 4:    Apple_Driver_ATA*Macintosh                   56 @ 176      
 5:    Apple_Driver_ATA*Macintosh                   56 @ 232      
 6:      Apple_FWDriver Macintosh                  512 @ 288      
 7:  Apple_Driver_IOKit Macintosh                  512 @ 800      
 8:       Apple_Patches Patch Partition            512 @ 1312     
 9:          Apple_Free                         262144 @ 1824      (128.0M)
10:           Apple_HFS Apple_HFS_Untitled_1 321408976 @ 263968    (153.3G)
11:          Apple_Free                             16 @ 321672944

Device block size=512, Number of Blocks=321672960 (153.4G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1:  23 @ 64, type=0x1
2:  36 @ 120, type=0xffff
3:  21 @ 176, type=0x701
4:  34 @ 232, type=0xf8ff


Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:      Apple_Driver43*Macintosh                   56 @ 64       
 3:      Apple_Driver43*Macintosh                   56 @ 120      
 4:    Apple_Driver_ATA*Macintosh                   56 @ 176      
 5:    Apple_Driver_ATA*Macintosh                   56 @ 232      
 6:      Apple_FWDriver Macintosh                  512 @ 288      
 7:  Apple_Driver_IOKit Macintosh                  512 @ 800      
 8:       Apple_Patches Patch Partition            512 @ 1312     
 9:          Apple_Free Extra                   262144 @ 1824      (128.0M)
10:     Apple_UNIX_SVR2 swap                   1835008 @ 263968    (896.0M)
11:          Apple_Free Extra                   262144 @ 2098976   (128.0M)
12:           Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)
13:          Apple_Free Extra                   262144 @ 375891328 (128.0M)
14:     Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)
15:          Apple_Free Extra                   262144 @ 584942184 (128.0M)
16:     Apple_Bootstrap Apple_HFS_Untitled_4  39938104 @ 585204328 ( 19.0G)
17:          Apple_Free Extra                       16 @ 625142432

Device block size=512, Number of Blocks=625142448 (298.1G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1:  23 @ 64, type=0x1
2:  36 @ 120, type=0xffff
3:  21 @ 176, type=0x701
4:  34 @ 232, type=0xf8ff

```


output for, ```
diskutil list
```
```
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *153.4 GB disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:         Apple_Driver43                    28.0 KB   disk0s2
   3:         Apple_Driver43                    28.0 KB   disk0s3
   4:       Apple_Driver_ATA                    28.0 KB   disk0s4
   5:       Apple_Driver_ATA                    28.0 KB   disk0s5
   6:         Apple_FWDriver                    256.0 KB  disk0s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk0s7
   8:          Apple_Patches                    256.0 KB  disk0s8
   9:              Apple_HFS Computer           153.3 GB  disk0s10
/dev/disk1
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *298.1 GB disk1
   1:    Apple_partition_map                    31.5 KB   disk1s1
   2:         Apple_Driver43                    28.0 KB   disk1s2
   3:         Apple_Driver43                    28.0 KB   disk1s3
   4:       Apple_Driver_ATA                    28.0 KB   disk1s4
   5:       Apple_Driver_ATA                    28.0 KB   disk1s5
   6:         Apple_FWDriver                    256.0 KB  disk1s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk1s7
   8:          Apple_Patches                    256.0 KB  disk1s8
   9:        Apple_UNIX_SVR2                    896.0 MB  disk1s10
  10:              Apple_HFS OS X               178.1 GB  disk1s12
  11:        Apple_UNIX_SVR2                    99.6 GB   disk1s14
  12:        Apple_Bootstrap                    19.0 GB   disk1s16

```

---

### Post by pxwpxw on 2007-10-12
Thanks.

Next
I want to check exactly what is on your external drive in partition 16 this way:

Just run these commands one at a time and in this order, in ubuntu terminal. 
You can copy and paste each command  into your terminal to avoid typing errors.

Then post a copy of everything from the terminal screen,  commands and results (good or bad) from start to finish. I want to see everything that happens as if I was doing it, that way if something goes wrong I can see exactly what happened. It wont do any harm:

```

 sudo mkdir aaa
 sudo mount /dev/sda16 aaa
 ls -la aaa
 df
 mount
 sudo umount aaa

```

---

### Post by computer geek on 2007-10-12
Here,


```
jacob@jacob-desktop:~$ sudo mkdir aaa
Password:
mkdir: cannot create directory `aaa': File exists
jacob@jacob-desktop:~$ sudo mount /dev/sda16 aaa
mount: special device /dev/sda16 does not exist
jacob@jacob-desktop:~$ ls -la aaa
total 8
drwxr-xr-x  2 root  root  4096 2007-10-12 07:27 .
drwxr-xr-x 40 jacob jacob 4096 2007-10-12 07:27 ..
jacob@jacob-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda14           102755244   3061680  94473848   4% /
varrun                  386768       100    386668   1% /var/run
varlock                 386768         0    386768   0% /var/lock
procbususb              386768       196    386572   1% /proc/bus/usb
udev                    386768       196    386572   1% /dev
devshm                  386768         0    386768   0% /dev/shm
lrm                     386768       268    386500   1% /lib/modules/2.6.20-16-powerpc/volatile
/dev/sda12           186748960  16601836 170147124   9% /media/OS X
jacob@jacob-desktop:~$ mount
/dev/sda14 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-powerpc/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda12 on /media/OS X type hfsplus (rw,noexec,nosuid,nodev)
jacob@jacob-desktop:~$ sudo umount aaa
umount: aaa: not mounted
jacob@jacob-desktop:~$ 

```

---

### Post by computer geek on 2007-10-12
UM, pxwpxw, the commands you gave me put a folder called, aaa, in my home folder, should i delete it? (it hast a lock icon on it.)

---

### Post by pxwpxw on 2007-10-12
> **computer geek said:**
> UM, pxwpxw, the commands you gave me put a folder called, aaa, in my home folder, should i delete it? (it hast a lock icon on it.)

Just leave it for now, no harm.  See next post.

---

### Post by pxwpxw on 2007-10-12
```

/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
/dev/sda15             Apple_Free Extra                 262144 @ 584942184 (128.0M)  Free space
[B]/dev/sda16        Apple_Bootstrap Apple_HFS_Untitled_4  39938104 @ 585204328 ( 19.0G)  NewWorld bootblock
[/B]/dev/sda17             Apple_Free Extra                     16 @ 625142432 (  8.0k)  Free space

```

Good information in all your posts now, that shows that sda16-Apple_Bootstrap has not been properly formatted and so there was no yaboot installed. It was not a problem with the external drive. Ubuntu can boot from WDC MiBook firewire with a normal installation. Your problem was because the partitioning went wrong when you tried to do it instead of letting the installer do it, the bootstrap was not used. One reason is that 19G is too big for that format. But 19GB is a good size for a ubuntu root partition.

The only way I can go any further with you on this is to simply do another ubuntu install on the 19GB  space from sda16. That should fix everything. Anything else is too difficult and time consuming for now.

That should be a good installation, you can add other features when you have more experience. You have already done 2 installs, so you know what to expect, but this one needs to be a bit different to avoid the problems, and to get all the boot menu options.

Here is an idea of what needs to be done for that, see what you think.

There is only one thing you need to do for partitioning, that is to make one continous free space large enough for the whole ubuntu installation, 19GB would be good, and make sure the installer uses that space on the external disk (when the Partitioner gets to the "Ready to Install" step you can abort it).

This time you can just delete the sda16 Apple_Bootstrap partition using mac-fdisk in a ubuntu terminal (DO NOT try to use the Gnome Partition Editor in the desktop for this - it is very confusing ). That will make an Apple_Free partition of 19GB in which you can install another Ubuntu system, using the Partitioner option "Guided - Use largest continuous space". 

This should install the full bootstrap and menu on the external drive as you did before with the whole disk. This should not affect your existing mac HFS  and ubuntu on the external drive, but you should back up anything you dont want to risk losing - that is your responsibility, no guarantees. 

The installer will work out how to divide the space up for root, swap and the bootstrap.
It will create the Apple_Bootstrap partition and also format it and write the boostrap files to it, including an option to boot Macosx.

That is why it worked and completed the yaboot installation when you used the entire disk.

I can post an example of mac-fdisk deleting a partition for you if you need it, very easy but be careful. The mac-fdisk way is best, because you can just quit without writing the changes if it looks wrong, and try again. And you can save a copy of everything from the terminal. 

I did a trial install like that on an external firewire HDD to check it all out with the <ubuntu 704 feisty desktop CD> on iBookG4, went well. But trying to use manual partitioning with the Desktop CD was a disaster, no need for it.

Pleas excuse any typos, its late.

---

### Post by computer geek on 2007-10-12
well um can i use your little fix for yaboot on[ poast]("http://ubuntuforums.org/showthread.php?t=562193")?

(click the poast word,) could you tell me how to use that in the installer?

Thanks, That would be a big HELP!

---

### Post by computer geek on 2007-10-12
or could i resize the boot partition?

---

### Post by pxwpxw on 2007-10-12
> **computer geek said:**
> or could i resize the boot partition?

You could perhaps do that  and then it would lead to more questions and detailed help.
Or you can just delete it and do the reinstall as I suggested, but it is for you to decide.
There are several other possibilities with varying degree of difficulty for you, but I can not  help you any further now.
It is time to wrap this up.


Good luck.

---

### Post by computer geek on 2007-10-13
When i type mac-fdisk in terminal it does not work, i have used something like that but i forgot it.

could i use a partition that is unallocated and use it as a boot partition, it is about 128.6 MB big.

What should i do? (i have users and a lot of progress and would hate to erase.)

---

### Post by pxwpxw on 2007-10-13
> **computer geek said:**
> When i type mac-fdisk in terminal it does not work, i have used something like that but i forgot it.

could i use a partition that is unallocated and use it as a boot partition, it is about 128.6 MB big.

What should i do? (i have users and a lot of progress and would hate to erase.)

You can read about any commands using the linux manual
```

 man mac-fdisk

```


For changes to the partition table, you have to give mac-fdisk the name of the disk, so you would use
```

 sudo mac-fdisk /dev/sda

```
The advantage of doing it in the terminal is that you can save a copy of everything you did.

 Your 19GB Apple_Bootstrap is partition 16 on /dev/sda, make sure you get the right one, you can identify it by the size. The freed partition gets merged with the small one above it to make one free partition.

 mac-fdisk just uses the "d" command and then the partition number to change  the partition type to Apple_Free for the installer to use.

 In mac-fdisk, always check with the "p" command before and after you do anything.

 If you  quit using "q",  without writing, nothing will be changed that time, you can do it again.

 When you do write the partition table, then quit and re-run mac-fdisk /dev/sda again to make sure /dev/sda16 is all free.

This example is from the terminal in a test I did to show you how it goes: 
I deleted partition 6 on /dev/sdc, but you will be deleting  partition 16 on /dev/sda.
This test was just some small  partitions I had on a USB stick which showed up as /dev/sdc.

```

admax@bigmac:~$ sudo mac-fdisk /dev/sdc
/dev/sdc

**Command (? for help): ?**

Notes:
  Base and length fields are blocks, which are 512 bytes long.
  The name of a partition is descriptive text.

Commands are:
  h    help
  p    print the partition table
  P    (print ordered by base address)
  i    initialize partition map
  s    change size of partition map
  b    create new 800K bootstrap partition
  c    create new Linux partition
  C    (create with type also specified)
  d    delete a partition
  r    reorder partition entry in map
  w    write the partition table
  q    quit editing (don't save changes)

**Command (? for help): p**

/dev/sdc
        #                    type name                length   base    ( size )  system
/dev/sdc1     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/sdc2               Apple_HFS Apple_HFS_Untitled_1  792784 @ 64      (387.1M)  HFS
/dev/sdc3               Apple_HFS Apple_HFS_Untitled_2  792784 @ 792848  (387.1M)  HFS
/dev/sdc4               Apple_HFS Apple_HFS_Untitled_3  792784 @ 1585632 (387.1M)  HFS
/dev/sdc5               Apple_HFS Apple_HFS_Untitled_4  792784 @ 2378416 (387.1M)  HFS
[COLOR="Red"]/dev/sdc6               Apple_HFS Apple_HFS_Untitled_[/COLOR]5  792688 @ 3171200 (387.1M)  HFS
/dev/sdc7              Apple_Free                         16 @ 3963888 (  8.0k)  Free space

Block size=512, Number of Blocks=3963904
DeviceType=0x0, DeviceId=0x0

**Command (? for help): d**

**Partition number: 6**

**Command (? for help): p**

/dev/sdc
        #                    type name                length   base    ( size )  system
/dev/sdc1     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/sdc2               Apple_HFS Apple_HFS_Untitled_1  792784 @ 64      (387.1M)  HFS
/dev/sdc3               Apple_HFS Apple_HFS_Untitled_2  792784 @ 792848  (387.1M)  HFS
/dev/sdc4               Apple_HFS Apple_HFS_Untitled_3  792784 @ 1585632 (387.1M)  HFS
/dev/sdc5               Apple_HFS Apple_HFS_Untitled_4  792784 @ 2378416 (387.1M)  HFS
[COLOR="Red"]/dev/sdc6              Apple_Free Extra[/COLOR]               792704 @ 3171200 (387.1M)  Free space

Block size=512, Number of Blocks=3963904
DeviceType=0x0, DeviceId=0x0

Command (? for help):  

**Command (? for help): w**

IMPORTANT: You are about to write a changed partition map to disk. 
For any partition you changed the start or size of, writing out 
the map causes all data on that partition to be LOST FOREVER. 
Make sure you have a backup of any data on such partitions you 
want to keep before answering 'yes' to the question below! 

**Write partition map? [n/y]: y**

The partition map has been saved successfully!

Syncing disks.

Partition map written to disk. If any partitions on this disk 
were still in use by the system (see messages above), you will need 
to reboot in order to utilize the new partition map.

**Command (? for help): q**
admax@bigmac:~$ 

```

### that was my test 

Then re-run "sudo mac-fdisk /dev/sda" to check that the partition is Apple_Free.

Then when you run the Desktop CD Install Partitioner, you choose 

     [COLOR="Red"]Guided use the largest continuous free space[/COLOR]


 That will automatically fit everything into the 19GB free space, not harming existing partitions.
 Then when the Partitioner gets to the "Ready to write " page, you can check to see what partition numbers it is using, 
It will not show the Apple_Bootstrap, just the 2 root and swap partitions. The Apple_Bootstrap it makes is only about 1MB. You can quit the installer there if something looks wrong, but it should be ok. But whatever you do, you have to backup anything you cant afford to lose, that is your responsibility. However I dont think you should have any problem if you do it this way.


XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

---

### Post by computer geek on 2007-10-13
Could i save everything if i put my users in the installer after the partitioning!

---

### Post by pxwpxw on 2007-10-14
> **computer geek said:**
> Could i save everything if i put my users in the installer after the partitioning!
Which users and settings are you worried about, is there much to back up?

There is nothing on the partition 16 Apple_Bootstrap to save.

All your existing Ubuntu system will still run after the new install - you should get a startup menu to choose  Macoax, or the old ubuntu, or the new ubuntu, and you can use them both. You will be able to access all the files in both ubuntu systems.

It is best to use the same login user names for the new install as you use for the first install. You can also import some settings stuff during the install.

You could copy any very important stuff to the Macosx partition on the internal drive, you would need to turn off journalling in Macosx for that.

 If you are careful and take it quietly you should not have a problem, you have done 2 Ubuntu installs and OSX before and survived.

---

### Post by computer geek on 2007-10-14
could i use this [howto?]("https://help.ubuntu.com/community/BootFromFirewireHardDisk?highlight")
Could you give me step by step how to prepare for this?

Now it says in mac fdisk that i can make a 800k boot partition or something.Do i need 145MB or not, then could you tell me how to mount the boot partition?

---

### Post by computer geek on 2007-10-14
is a 800KB boot partition good? of do i need a 128MB partition.

how big do i make the first block?

```
jacob@jacob-desktop:~$ mac-fdisk /dev/sda
/dev/sda
Command (? for help): ?
Notes:
  Base and length fields are blocks, which are 512 bytes long.
  The name of a partition is descriptive text.

Commands are:
  h    help
  p    print the partition table
  P    (print ordered by base address)
  i    initialize partition map
  s    change size of partition map
  b    create new 800K bootstrap partition
  c    create new Linux partition
  C    (create with type also specified)
  d    delete a partition
  r    reorder partition entry in map
  w    write the partition table
  q    quit editing (don't save changes)
Command (? for help): p
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
/dev/sda15             Apple_Free Extra                 262144 @ 584942184 (128.0M)  Free space
/dev/sda16        Apple_Bootstrap Apple_HFS_Untitled_4  39938104 @ 585204328 ( 19.0G)  NewWorld bootblock
/dev/sda17             Apple_Free Extra                     16 @ 625142432 (  8.0k)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

Command (? for help): d
Partition number: 16
Command (? for help): p
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
/dev/sda15             Apple_Free Extra               40200264 @ 584942184 ( 19.2G)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

Command (? for help): b
First block: 
First block:   

```

---

### Post by pxwpxw on 2007-10-15
> **computer geek said:**
> is a 800KB boot partition good? of do i need a 128MB partition.

how big do i make the first block?

```
jacob@jacob-desktop:~$ mac-fdisk /dev/sda
/dev/sda
Command (? for help): ?
Notes:
  Base and length fields are blocks, which are 512 bytes long.
  The name of a partition is descriptive text.

Commands are:
  h    help
  p    print the partition table
  P    (print ordered by base address)
  i    initialize partition map
  s    change size of partition map
  b    create new 800K bootstrap partition
  c    create new Linux partition
  C    (create with type also specified)
  d    delete a partition
  r    reorder partition entry in map
  w    write the partition table
  q    quit editing (don't save changes)
Command (? for help): p
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
/dev/sda15             Apple_Free Extra                 262144 @ 584942184 (128.0M)  Free space
/dev/sda16        Apple_Bootstrap Apple_HFS_Untitled_4  39938104 @ 585204328 ( 19.0G)  NewWorld bootblock
/dev/sda17             Apple_Free Extra                     16 @ 625142432 (  8.0k)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

Command (? for help): d
Partition number: 16
Command (? for help): p
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9              Apple_Free Extra                 262144 @ 1824      (128.0M)  Free space
/dev/sda10        Apple_UNIX_SVR2 swap                 1835008 @ 263968    (896.0M)  Linux swap
/dev/sda11             Apple_Free Extra                 262144 @ 2098976   (128.0M)  Free space
/dev/sda12              Apple_HFS Apple_HFS_Untitled_2 373530208 @ 2361120   (178.1G)  HFS
/dev/sda13             Apple_Free Extra                 262144 @ 375891328 (128.0M)  Free space
/dev/sda14        Apple_UNIX_SVR2 Apple_HFS_Untitled_3 208788712 @ 376153472 ( 99.6G)  Linux native
[COLOR="Red"]/dev/sda15             Apple_Free Extra               40200264 @ 584942184 ( 19.2G)  Free space
[/COLOR]

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

[COLOR="red"]XXXXX you dont make a bootstrap partition, the installer will do that[/COLOR]

Command (? for help): b
First block: 
First block:   

```

[COLOR="red"]You DO NOT MAKE A BOOTSTRAP , the installer will do that, you just write the changed partition table after you get the 19.2G Apple_Free /dev/sda15, 
 Then when you do the install, choose  
Guided partitioning use largest continuous free space.[/COLOR]

The installer will make a bootstrap partition and a root and swap, all inside the 19.2G Free space..

Any other way is too difficult for you.

.

---

### Post by computer geek on 2007-10-15
Please, I want 100.00GB for linux if i do that it will probably go eather go to my intrnal HDD or my mac os partition(os partition on extrnal HDD) Could i use the fix on this [site?  ]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607")

or can i do what you did on [here?]("http://ubuntuforums.org/showthread.php?t=562193")

or what you had some buddy else [do]("http://ubuntuforums.org/showthread.php?t=561167")....  

or prepare me for This [Page]("https://help.ubuntu.com/community/BootFromFirewireHardDisk?highlight=%28bootfromfirewireharddisk%29")!!

Please reply!

---

### Post by pxwpxw on 2007-10-15
> **computer geek said:**
> Please, I want 100.00GB for linux if i do that it will probably go eather go to my intrnal HDD or my mac os partition(os partition on extrnal HDD) Could i use the fix on this [site?  ]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607")

or can i do what you did on [here?]("http://ubuntuforums.org/showthread.php?t=562193")

or what you had some buddy else [do]("http://ubuntuforums.org/showthread.php?t=561167")....  

or prepare me for This [Page]("https://help.ubuntu.com/community/BootFromFirewireHardDisk?highlight=%28bootfromfirewireharddisk%29")!!

Please reply!

You can try whatever you like, you could just leave things as they are for now.
I have given you my recommendation,  sorry I can't help any further sorting out your problems, I am out of ideas for you. 
I will leave it for you to seek other advice now, maybe someone else can assist.

---

### Post by computer geek on 2007-10-15
well do you know anything about that patch, how to use it?

---

### Post by computer geek on 2007-10-15
Why can't I do what you did in that one poast?

---

### Post by computer geek on 2007-10-15
Can Anybody Else  Help!!!!!!!!!!!!!!!!

---

### Post by oswaldkelso on 2007-10-16
This is how i setup dual boot on ppc macs.
in osx download carbon copy cloner. (ccc). plug in an external firewire harddrive ( ihave used 30gb firewire ipod) clone your hd onto it.

use the osx install disk to partition your hd with osx on the first partitooon. the rest as free space.

startup from your firewire hard drive (hold the alt key down on boot and select your cloned drive) clone your data back off the external hd onto the first partion

install debian onto the free space. ubuntu for you

A few things to note it must be a firewire hd not usb

if you have a firewire to firewire cable (6 pin) you can clon straight on to a drive in another mac

I have done this several times but backup your data first Smile

This method is easy to do and by swopping you can arrange and resize you partitions as needed. but it does use osx on the external drive and a small osx partiton on the first part of your internal HD (i use it as a rescue partition as my install disk in scratched)
_________________
emac 1.333 Smile osx, and Debian. G4 digital audio 867 osx . Some real old 567mhz pc debian and absolute linux. Mac classic os6. And an amd 300mhz debian sarge.

---

### Post by computer geek on 2007-10-16
What do you mean clone my Clone my hd to it?  Clone my intrnal hdd to the extrnal hdd? I don't know if i want osx on my extrnal hdd and ubuntu on my intrnal hdd, I wan't to yaboot it, OS X on intrnal for leopard in 10 days and ubuntu on the extrnal, Ubuntu 7.10.  DOES ANYONE KNOW HOW TO Use THE PATCH AND CHECK-SUM ON THIS [WEBSITE.]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607")

Please HELP!!!!!!!!!!!!!!!!!!!

---

### Post by computer geek on 2007-10-17
sorry about that poast,(149) i got a little desperate.
:):):):):popcorn::popcorn::popcorn::)

---

### Post by Tommy on 2007-10-17
> **computer geek said:**
> I don't know if i want osx on my extrnal hdd and ubuntu on my intrnal hdd, I wan't to yaboot it, OS X on intrnal for leopard in 10 days and ubuntu on the extrnal, Ubuntu 7.10.  DOES ANYONE KNOW HOW TO Use THE PATCH AND CHECK-SUM ON THIS [WEBSITE.]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607")

Are you sure this patch applies to your situation? 

I thought you had a successful Ubuntu install, and you were just trying to add an easier boot menu. Installing a linux software patch generally requires having the source code for the packages, and re-compiling some or all of them. 

The checksum verifies that the author's copy and your copy are identical. The patch file tells the editor how to make the changes the patch's author made. If you are new to these concepts, an installation is NOT the time to be learning them!

pxwpxw recommended you use the existing software because to do something more complicated requires more knowledge and experience than people are able to supply in this forum! The installer does a lot of work to make the install easy. If you second-guess the installer, you are bypassing the work the knowledgeable developers have done before.

Besides, it's MUCH easier starting from scratch because then you are in the same place as every other new installation. You will not "lose" everything you have done in the first installation because you have gained experience.

I suggest you might use a second external drive to make a backup of your first external drive and start the installation over from the very beginning as described several times in this thread. If there is something you really need on your current Ubuntu installation you can mount the second external drive and copy the settings from there. 

Alternate suggestion: Write down or print the settings and/or configuration files you have changed so far so you can manually enter them again when necessary.

---

### Post by computer geek on 2007-10-17
Can i please use the Harder way?

---

### Post by computer geek on 2007-10-17
I would very much appreciate some help.

Thanks

---

### Post by computer geek on 2007-10-18
Please Post

---

### Post by computer geek on 2007-10-22
Please?

---

### Post by computer geek on 2007-11-22
Ok... I went and searched up some info from google. I created a boot partition. then i ran, ```
yabootconfig
``` and then I ran, ```
sudo nano /etc/yaboot.conf
```. Than i ran the command to put yaboot, yaboot.conf, and ofboot. Here is my yaboot.conf,

```
## yaboot.conf generated by yabootconfig 1.0.8
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of: 
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda9
device=/pci@f4000000/firewire@e/node@0090a993e0200acf/sbp-2@c000/disk@0:
partition=14

delay=10
defaultos=macosx
timeout=120
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

image=/boot/vmlinux
	label=l
	read-only
	initrd=/boot/initrd.img
	initrd-size=8192

macosx=/dev/hda10
enablecdboot
fgcolor=black
bgcolor=red
```

And here is one i wrote,

```
boot=/dev/sda9
magicboot=/usr/lib/yaboot/ofboot
macosx=/dev/hda10
delay=10
timeout=60
root=/dev/sda14
device=/pci@f4000000/firewire@e/node@0090a993e0200acf/sbp-2@c000/disk@0:


image=/boot/vmlinux
	partition=14	
	lable=l
	read-olny
	initrd=/boot/initrd.img
	initrd-size=8192

enablecdboot
fgcolor=black
bgcolor=red
```

Hope this can help.:)

P.S. I you don't know what i am asking, I would like to get a dual boot menu so a can save a lot of work. instead of holding down the option key to boot into os x and the default os  being linux.

Thanks!:popcorn:

---

### Post by computer geek on 2007-11-30
OK, something is weird here. When i start up my computer, i get a gray screen for a few seconds and then it goes to a black screen and there is where is seems to be loading yaboot, i a get a flacsing folder icon with a ?, then a folder with mac os x and boots that.

I don't know if that is my yaboot.conf file or something.

But here is my yaboot.conf file.

```
## yaboot.conf generated by yabootconf
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda9
device=/pci@f4000000/firewire@e/node@0090a993e0200acf/sbp-2@c000/disk@0:
partition=14
root=/dev/hda14
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda10

image=/boot/vmlinux
	label=l
	read-only
	initrd=/boot/initrd.img
	initrd-size=8192


defaultos=macosx
fgcolor=black
bgcolor=red
```


Thanks! Hope you can help!:popcorn:

---

### Post by computer geek on 2007-12-09
Ok, I stupidly messed up booting, But i have one question, You know in Boot Camp, could I use that to partition my drives? and, will it install a Boot loader? And then, is there a way to get linux to not install yaboot?

I want to dual boot, if I can't dual boot linux, i will probably use VMWare.

Geek

---

### Post by Tommy on 2007-12-10
> **computer geek said:**
> Ok, I stupidly messed up booting, But i have one question, You know in Boot Camp, could I use that to partition my drives? 

from my reading, you DON'T want to use Boot Camp to partition your drives because it has to do some stuff to make Windows happy that won't make linux any easier. 

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)



...and here's a link with some more technical background if you want it: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

---

### Post by computer geek on 2007-12-11
Will iBoot work?

[iBoot]("http://sourceforge.net/projects/iboot/")

or, will Grub Work?

---

### Post by computer geek on 2007-12-13
Will LILO (LInux LOader) work?

Or does LILO work on PCs?




Geek

---

### Post by computer geek on 2008-01-09
Thanks to me I reinstalled some how and now I am back in Ubuntu with a Dualboot menu.
:lolflag::lolflag::guitar::guitar::):popcorn::KS:guitar:

---

### Post by computer geek on 2008-01-09
Thanks! All of your help was a BIG help Too.

It is OK to post more

---

