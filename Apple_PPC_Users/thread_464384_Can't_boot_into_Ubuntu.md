---
title: "Can't boot into Ubuntu"
date: 2007-06-04
forum: Apple PPC Users
---

### Post by stylecramper on 2007-06-04
Just finished a fresh install of Ubuntu 7.04 on a G5 dual 1.8Ghz. I have a Firewire external drive that I've partitioned into one HFS+ volume and four partitions for Ubuntu (1GB swap, 10GB /, 6.5GB /home, 1MB NewWorld). When I hold the Option key while booting, I get to the startup disk chooser and I get a button for Linux. Clicking it takes me to a black screen with the following white text:
[COLOR="RoyalBlue"]
First Stage Ubuntu Bootstrap

Press l for Gnu/Linux,
x for MacOSX,
c for CDROM

Stage 1 Boot:[/COLOR]

After pressing any key, or just waiting five seconds, this line appears:
[COLOR="RoyalBlue"]
Loading second stage bootstrap...[/COLOR]

But then I'm immediately taken back to the startup disk choice screen again.

Any suggestions would be welcome!

---

### Post by thelocust on 2007-06-04
What bootloader are you using it doesn't look like GRUB.

---

### Post by jrlohr on 2007-06-04
here read through this post 

[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

but most likely it is in the device="??" line of the yaboot.config so hopefully this thread helps u

---

### Post by stylecramper on 2007-06-04
> **thelocust said:**
> What bootloader are you using it doesn't look like GRUB.

Sorry, no idea - I'm a total Linux newbie.

---

### Post by jrlohr on 2007-06-04
> **stylecramper said:**
> Sorry, no idea - I'm a total Linux newbie.

The screen you are at is the yaboot loader which is the first stage the second stage is grub.

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> The screen you are at is the yaboot loader which is the first stage the second stage is grub.

As I mentioned, I never get to the second stage, I just get kicked back to the startup disk chooser screen.

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> here read through this post 

[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

but most likely it is in the device="??" line of the yaboot.config so hopefully this thread helps u

I went through that thread, and tried the steps outlined in post #18 by stmiller. When I got to trying this part:

> **stmiller said:**
> Root filesystem: pick /dev/sda3 (That's what worked on my system. Yours may be different.)
[if that doesn't work, choose 'GO BACK'
then select 'rescue mode' and pick another partition option. You can't hurt anything by trying a different one. It will only let you use the real root partition.]

The list of options were as follows:
/dev/sdb1
/dev/sdb2
/dev/sdb3
/dev/sdb4
/dev/sdb6
/dev/sdc1
/dev/sdc2
/dev/sdc3
/dev/sdc4
/dev/sdc5
/dev/sdc6

Every one of these didn't work - none apparently had a root fiilesystem.

In any case, I don't see how these options reflect the state of my hard drives. I have two internal HDs with two partitions each, and one external Firewire drive with one Mac HFS+ partition and four partitions for Ubuntu.

---

### Post by Auria on 2007-06-04
I unfortunately don't have the answer - but pleas eignore anyone talking about GRUB. They obviously have never used the PPC version of Ubuntu and their answers can only mislead you. (GRUB is use in the x86 version, the PPC one uses yaboot)

---

### Post by jrlohr on 2007-06-04
I know where the problem is and i will try to explain. 

first I need to see the yaboot.conf file so boot to a live cd and mount the HD that has the ubuntu install on it and post the file.

via 

sudo mount /dev/???? /mnt  (????= your partion with Ubuntu)

cat /etc/yaboot.conf

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> I know where the problem is and i will try to explain. 

first I need to see the yaboot.conf file so boot to a live cd and mount the HD that has the ubuntu install on it and post the file.

via 

sudo mount /dev/???? /mnt  (????= your partion with Ubuntu)

cat /etc/yaboot.conf

Thanks for the help. Unfortunately I have another problem, which is that I've never been able to boot Ubuntu from the live CD. I can start up from the CD and get past the black logo screen with progress bar. After that, an error appears: "Failed to start the X server", and I'm shown a text screen that asks if I want to view some output. Whether I choose Yes or No, after that an error message comes up that says "bcm43xx_microcode5.fw not available or load failed" and this message repeats indefinitely while I am unable to do anything.

The G5 has an ATI Radeon 9600 added to it, but otherwise nothing unusual. Any suggestions would be welcome.

---

### Post by stylecramper on 2007-06-04
I think my best option is just to ditch the whole project. I've been banging my head against it for a couple of weeks now and I'm starting to think that having Linux on my Mac just isn't worth the amount of time this is taking.

---

### Post by jrlohr on 2007-06-04
Which monitor do u have with your G5, Is it the one with the power button and plastic or the newer sliver one?

---

### Post by stylecramper on 2007-06-04
It's actually a Samsung 19" LCD running off an ATI Radeon 9600.

---

### Post by jrlohr on 2007-06-04
when booting from the cd have u tried  the "video=ofonly" option?

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> when booting from the cd have u tried  the "video=ofonly" option?

OK, tried that. This time the logo and progress bar were pixely and rainbow-coloured. After they disappeared, the screen was black. After a while the CDROM stopped spinning, and after several minutes of black screen I pressed the power button to shut down.

---

### Post by jrlohr on 2007-06-04
Well i am not sure why it wont boot from the cd. 

How did you get it installed?

---

### Post by stylecramper on 2007-06-04
I also have the Alternate cd, and installed from that.

---

### Post by jrlohr on 2007-06-04
Well I have not worked with the alt cd yet.

Are u on the machine that has it installed and if so, what OS are you in?

---

### Post by jrlohr on 2007-06-04
Well I will look into it to see if what need to be done can be done from the alternate cd and will get back to u tomarrow

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> Well I will look into it to see if what need to be done can be done from the alternate cd and will get back to u tomarrow

Much appreciated, thanks!

---

### Post by stylecramper on 2007-06-04
> **jrlohr said:**
> Well I have not worked with the alt cd yet.

Are u on the machine that has it installed and if so, what OS are you in?

I'm using the same machine, OS X 10.4.9. OS X is installed on its original internal drive, and Ubuntu is installed on my Firewire external drive.

---

### Post by stmiller on 2007-06-04
Okay seems like the problem is the boot partition which has yaboot written to it does not know where to point to the kernel image on that external drive. This is somewhat of a crazy problem. You'll have to have a somewhat particular yaboot.conf for this setup.

And also the Feisty installer seems to crap out and not write a correct yaboot at the end for some people. This may have happened here too.

The people in irc.freenode.net on #ubuntu-powerpc #debian-ppc or #gentoo-ppc can help if you need immediate help.

---

### Post by pxwpxw on 2007-06-05
**stylecramper**

You can run ubuntu on an external firewire drive on a powermac g5, but it does require some initial tweaks to the yaboot installation, to get it running smoothly.

If you can use the terminal appliction in macosx and post your current boot settings, then we can see what editing of yaboot.conf is needed, and how best to restart into ubuntu to reinstall the bootloader. (possible from the macosx or using the rescue64 option from  your Alternate instll cd.)

The problem with graphics may not happen with the installation, but anyway it comes after the restart problem.

First thing, run these 2 commands from terminal in macosx and post the results.

```

 nvram boot-device
 
 sudo pdisk -l

```

---

### Post by jrlohr on 2007-06-05
Boot into the alt cd and run the rescue at start up follow the prompt and load into the root file sys for that drive then run 

cat /etc/yaboot.conf

and write down these lines from the file and post.

device="??????"
macosx="?????"

---

### Post by stylecramper on 2007-06-05
> **pxwpxw said:**
> Firt thing, run these 2 commands from terminal in macosx and post the results.

```

 nvram boot-device
 
 sudo pdisk -l

```

Result of first command:

boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:8,\\:tbxi

Result of 2nd command:

Partition map (with 512 byte blocks) on '/dev/rdisk2'
 #:                type name                   length   base     ( size )
 1: Apple_partition_map Apple                      63 @ 1       
 2:          Apple_Free Extra                  262144 @ 64       (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1 41680896 @ 262208   ( 19.9G)
 4:          Apple_Free Extra                  262144 @ 41943104 (128.0M)
 5:     Apple_Bootstrap ubroot               20217856 @ 42205248 (  9.6G)
 6:          Apple_Free Extra                  262144 @ 62423104 (128.0M)
 7:     Apple_UNIX_SVR2 swap                  1835008 @ 62685248 (896.0M)
 8:     Apple_Bootstrap NewWorld                 8192 @ 64520256 (  4.0M)
 9:          Apple_Free Extra                  262144 @ 64528448 (128.0M)
10:     Apple_UNIX_SVR2 Ubhome               13365680 @ 64790592 (  6.4G)
11:          Apple_Free Extra                      16 @ 78156272

Device block size=512, Number of Blocks=78156288 (37.3G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:          Apple_Free                         262144 @ 64        (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1  83623936 @ 262208    ( 39.9G)
 4:          Apple_Free                         262144 @ 83886144  (128.0M)
 5:           Apple_HFS Apple_HFS_Untitled_2  72153184 @ 84148288  ( 34.4G)
 6:          Apple_Free                             16 @ 156301472

Device block size=512, Number of Blocks=156301488 (74.5G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:          Apple_Free                         262144 @ 64        (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1  41686880 @ 262208    ( 19.9G)
 4:          Apple_Free                         262144 @ 41949088  (128.0M)
 5:           Apple_HFS Apple_HFS_Untitled_2 356085840 @ 42211232  (169.8G)
 6:          Apple_Free                             16 @ 398297072

Device block size=512, Number of Blocks=398297088 (189.9G)
DeviceType=0x0, DeviceId=0x0

---

### Post by stylecramper on 2007-06-05
> **jrlohr said:**
> Boot into the alt cd and run the rescue at start up follow the prompt and load into the root file sys for that drive then run 

As I mentioned above, I can't load into the root filesystem in rescue mode. Trying every option presented gives me a version of the following error:

Mount failed
An error occcurred while mounting the device you entered for your root filesystem (/dev/sdb1) on /target.

---

### Post by stylecramper on 2007-06-05
BTW, thanks so much for all the help people!

---

### Post by haftan on 2007-06-05
Ubuntu thinks it is hdd0 by default (I think).  My Dell laptop has 4 partitions, and the OS is on the third one.  Soooo... I have to edit /boot/grub/menu.lst to change the root(hd0,0) to root(hd0,2) to let it find itself.  Maybe this works for you too.

---

### Post by jrlohr on 2007-06-05
> **stylecramper said:**
> Result of first command:

boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:8,\\:tbxi

Result of 2nd command:

Partition map (with 512 byte blocks) on '/dev/rdisk2'
 #:                type name                   length   base     ( size )
 1: Apple_partition_map Apple                      63 @ 1       
 2:          Apple_Free Extra                  262144 @ 64       (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1 41680896 @ 262208   ( 19.9G)
 4:          Apple_Free Extra                  262144 @ 41943104 (128.0M)
 5:     Apple_Bootstrap ubroot               20217856 @ 42205248 (  9.6G)
 6:          Apple_Free Extra                  262144 @ 62423104 (128.0M)
 7:     Apple_UNIX_SVR2 swap                  1835008 @ 62685248 (896.0M)
 8:     Apple_Bootstrap NewWorld                 8192 @ 64520256 (  4.0M)
 9:          Apple_Free Extra                  262144 @ 64528448 (128.0M)
10:     Apple_UNIX_SVR2 Ubhome               13365680 @ 64790592 (  6.4G)
11:          Apple_Free Extra                      16 @ 78156272

Device block size=512, Number of Blocks=78156288 (37.3G)
DeviceType=0x0, DeviceId=0x0



is partition 5 the root file sys on this drive for Ubuntu?  if it is,then  it is the wrong type it should be the same type as partition 10 and the only way i know how to change is to reinstall ubuntu.

If you are going to reinstall leave partition 3 untouched and clear the rest.

But everything else looks fine.

---

### Post by stylecramper on 2007-06-05
> **jrlohr said:**
> is partition 5 the root file sys on this drive for Ubuntu?  if it is,then  it is the wrong type it should be the same type as partition 10 and the only way i know how to change is to reinstall ubuntu.

If you are going to reinstall leave partition 3 untouched and clear the rest.

But everything else looks fine.

When I ran the partitioner, I set up that partition as:

[COLOR="RoyalBlue"]Use as: XFS Journaling file system
Mount point: /
Mount options: defaults
Label: ubroot
Bootable flag: on[/COLOR]

Does any of that look incorrect?

---

### Post by jrlohr on 2007-06-05
Are u reinstalling?  if u are once the partitioner is loaded select manual then create free space buy deleting the old partitions but **not touching OSX** then select the free space and press enter then select the 2nd option which will automatically set up the correct partitions.

---

### Post by stmiller on 2007-06-05
> **haftan said:**
> Ubuntu thinks it is hdd0 by default (I think).  My Dell laptop has 4 partitions, and the OS is on the third one.  Soooo... I have to edit /boot/grub/menu.lst to change the root(hd0,0) to root(hd0,2) to let it find itself.  Maybe this works for you too.

haftan: PowerPC Linux does not use grub. That is for x86 hardware only.

---

### Post by stylecramper on 2007-06-05
> **jrlohr said:**
> Are u reinstalling?  if u are once the partitioner is loaded select manual then create free space buy deleting the old partitions but **not touching OSX** then select the free space and press enter then select the 2nd option which will automatically set up the correct partitions.

OK, did that. The result is the same: holding the Option key gets me to the startup disk chooser, I choose the Linux startup and click the arrow, black screen with First Stage Ubuntu Bootstrap and the three choices, any key takes me back to the startup disk chooser.

Output of [COLOR="Red"]nvram boot-device[/COLOR] is now:
[COLOR="RoyalBlue"]boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi[/COLOR]

Output of [COLOR="Red"]sudo pdisk -l[/COLOR] is now:
[COLOR="RoyalBlue"]Partition map (with 512 byte blocks) on '/dev/rdisk2'
 #:                type name                   length   base     ( size )
 1: Apple_partition_map Apple                      63 @ 1       
 2:     Apple_Bootstrap NewWorld                 1954 @ 41943104
 3:           Apple_HFS Apple_HFS_Untitled_1 41680896 @ 262208   ( 19.9G)
 4:     Apple_UNIX_SVR2 Ubroot               34605469 @ 41945058 ( 16.5G)
 5:     Apple_UNIX_SVR2 swap                  1605761 @ 76550527 (784.1M)
 6:          Apple_Free Extra                  262144 @ 64       (128.0M)

Device block size=512, Number of Blocks=78156288 (37.3G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:          Apple_Free                         262144 @ 64        (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1  83623936 @ 262208    ( 39.9G)
 4:          Apple_Free                         262144 @ 83886144  (128.0M)
 5:           Apple_HFS Apple_HFS_Untitled_2  72153184 @ 84148288  ( 34.4G)
 6:          Apple_Free                             16 @ 156301472

Device block size=512, Number of Blocks=156301488 (74.5G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name                    length   base      ( size )
 1: Apple_partition_map Apple                       63 @ 1        
 2:          Apple_Free                         262144 @ 64        (128.0M)
 3:           Apple_HFS Apple_HFS_Untitled_1  41686880 @ 262208    ( 19.9G)
 4:          Apple_Free                         262144 @ 41949088  (128.0M)
 5:           Apple_HFS Apple_HFS_Untitled_2 356085840 @ 42211232  (169.8G)
 6:          Apple_Free                             16 @ 398297072

Device block size=512, Number of Blocks=398297088 (189.9G)
DeviceType=0x0, DeviceId=0x0[/COLOR]

---

### Post by jrlohr on 2007-06-06
> **stylecramper said:**
> 

Output of [COLOR="Red"]nvram boot-device[/COLOR] is now:
[COLOR="RoyalBlue"]boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi[/COLOR]

Output of [COLOR="Red"]sudo pdisk -l[/COLOR] is now:
[COLOR="RoyalBlue"]Partition map (with 512 byte blocks) on '/dev/rdisk2'
 #:                type name                   length   base     ( size )
 1: Apple_partition_map Apple                      63 @ 1       
 2:     Apple_Bootstrap NewWorld                 1954 @ 41943104
 3:           Apple_HFS Apple_HFS_Untitled_1 41680896 @ 262208   ( 19.9G)
 4:     Apple_UNIX_SVR2 Ubroot               34605469 @ 41945058 ( 16.5G)
 5:     Apple_UNIX_SVR2 swap                  1605761 @ 76550527 (784.1M)
 6:          Apple_Free Extra                  262144 @ 64       (128.0M)

Device block size=512, Number of Blocks=78156288 (37.3G)
DeviceType=0x0, DeviceId=0x0




ok now the partition table is fixed you should be able to boot into rescue mode from the alt CD and mount the root drive and from the looks of the drive layout it should be sdc4 when read by linux then it will prompt you to open a terminal on root select sdc4 to open terminal and run 

cat /etc/yaboot.conf

and post the results for the lines where

device="?????"
osx="?????"

then we will go to the next step.

---

### Post by pxwpxw on 2007-06-06
**stylecramper**

That reinstall looks good, the same result is to be expected, not a problem with your installation. Now yaboot.conf needs work.

If you prefer getting a copy of yaboot.conf using macosx, heres how:

It is in your small Apple_Bootstrap partition, at /dev/disk2s2
Note that you use /dev/disk2 here not /dev/rdisk2 as pdisk shows.

Using yout terminal in macosx again, make a directory called aaa, mount the bootstrap partition, list the files, and open yaboot.conf, post a copy of the terminal text,
unmount the partition.

```

mkdir aaa

sudo mount -t hfs /dev/disk2s2 aaa

ls -l aaa

cat aaa/yaboot.conf

sudo umount aaa

```

Post the whole terminal text with the output of the <ls -l aaa>, and yaboot.conf text.

Also please confirm your drive configuration (referring to the pdisk lists):

 disk2 37G is external firewire with ubuntu and a 20GB macos partition.
 disk1 74G is internal sata 
 disk0 189G is interrnal sata with "OS X 10.4.9. OS X is installed on its original internal drive"
 
That is,  macosx system is on disk0s3?

When you try to boot ubuntu from the graphical selector, does the linux icon show the firewire symbol (like a Y).

(Note of encouragement:I am posting this from xubuntu running on an external firewire 160GB.)

---

### Post by pxwpxw on 2007-06-06
> **stylecramper said:**
> I went through that thread, and tried the steps outlined in post #18 by stmiller. When I got to trying this part:

The list of options were as follows:
/dev/sdb1
/dev/sdb2
/dev/sdb3
/dev/sdb4
/dev/sdb6
/dev/sdc1
/dev/sdc2
/dev/sdc3
/dev/sdc4
/dev/sdc5
/dev/sdc6

Every one of these didn't work - none apparently had a root fiilesystem.

In any case, I don't see how these options reflect the state of my hard drives. I have two internal HDs with two partitions each, and one external Firewire drive with one Mac HFS+ partition and four partitions for Ubuntu.

Good point:

(I have just checked this with feisty Alternate Install CD - rescue-powerpc64 mode.)
With an external firewire drive and 2 internal sata drives. (These are not bugs, just facts and dont normally matter, and applies also to previous versions)

 1. the drive names in the installer/rescue first stage are not the same as for the final system.
 2. the rescue menu does not show the firewire drive.
  -- the external firewire drive can not be selected for rescue from the main menu (this can be done by dropping to a console and mounting it manually, bind proc and sys, chroot, somewhat messy process to explain)
 
  If the normal linux  drive names are-------------------rescue disk sees:
  /dev/sda = the macosx main drive---------------/dev/sdb
  /dev/sdb = the second internal drive------------/dev/sdc
  /dev sdc = the external firewire-------------------/dev/sda 
But then /dev/sda is not shown as an option in the rescue selector because it is firewire.

So you would need to mount a partition from /dev/sda from the rescue console in order to rescue what is normaly  on /dev/sdc.

In this case, the macosx option to get it all done is sounding even better.

---

### Post by stylecramper on 2007-06-06
> **pxwpxw said:**
> **stylecramper**

Using yout terminal in macosx again, make a directory called aaa, mount the bootstrap partition, list the files, and open yaboot.conf, post a copy of the terminal text,
unmount the partition.

```

mkdir aaa

sudo mount -t hfs /dev/disk2s2 aaa

ls -l aaa

cat aaa/yaboot.conf

sudo umount aaa

```

Post the whole terminal text with the output of the <ls -l aaa>, and yaboot.conf text.

Output:
[COLOR="RoyalBlue"]Brainiac:~ matt$ ls -l aaa 
total 309
-rwxr-xr-x   1 matt  matt    3106 Jun  5 18:34 ofboot.b
-rwxr-xr-x   1 matt  matt  153124 Jun  5 18:34 yaboot
-rwxr-xr-x   1 matt  matt     702 Jun  5 18:34 yaboot.conf

Brainiac:~ matt$ cat aaa/yaboot.conf
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:
partition=4
root=/dev/sda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"[/COLOR]

> **pxwpxw said:**
> Also please confirm your drive configuration (referring to the pdisk lists):

 disk2 37G is external firewire with ubuntu and a 20GB macos partition.
 disk1 74G is internal sata 
 disk0 189G is interrnal sata with "OS X 10.4.9. OS X is installed on its original internal drive"
 
That is,  macosx system is on disk0s3?

No, it's actually on disk1s3. Your other assumptions are right though.

> **pxwpxw said:**
> When you try to boot ubuntu from the graphical selector, does the linux icon show the firewire symbol (like a Y).


Yes.

---

### Post by stylecramper on 2007-06-06
> **pxwpxw said:**
> 
 2. the rescue menu does not show the firewire drive.

That's what I'd suspected.

---

### Post by pxwpxw on 2007-06-06
Reading it now.
You have the same as me, my original 80Gb disk, then added a 160GB.

Yep, think I can edit that, then you do the same procedure as before to mount the bootstrap from the external, and copy it back (after making a backup copy of the original there.) Then I can show you how, from macosx, set the boot-device to boot yaboot on the bootstrap, then restart and it should auto-boot into ubuntu (if I get it right).  You will be able to get back into macosx using the graphical boot selector. (99% sure).
The object is to see if we can get ubuntu running and get its version of the drive names from the installed system, then a final tweak of yaboot.conf in the ubuntu root, and should bee able to boot ubuntu from the graphic. The installer called it /dev/sda, but will be sdc.
The best arrangement is to put a bootstrap partition on disk0s2, which can be done, so you can get a faster boot selection. But best get ubuntu running first, use experience to get a final install just as you want.
I need a 1/2 hr or so to get a revised yaboot.conf to suit your system.

---

### Post by stylecramper on 2007-06-06
Thanks for the amazing effort!

---

### Post by pxwpxw on 2007-06-06
This should work, next post will explain how to boot from yaboot using macosx to set boot-device.

###############################################



########## edited for initial boot ubuntu root /dev/sdc4 on firewire
## this is only for booting yaboot directly for inital run of ubuntu root.
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ
##################################
## boot is where its installed, irrelevant for now, its alredy there, have to fix later
## boot=/dev/sda2
boot=/dev/sdc2
## device is for the image section, and this is wrong, but a valid full path for /dev/sda
## in open firmware language, but not for firewire, aliases are much shorter
##
## device=/ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:
## partition goes with the image section - do it that way later when multibooting
### partition=4
### root goes with each image and its sdc4
### root=/dev/sda4
## ofboot is needed in the final install, not when booting yaboot initially
ofboot=fw/node/sbp-2/disk:2
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
#### macosx=  will need changing before reinstalling the bootstrap, to an open firmware path, wont affect initial boot yaboot. 
### and macosx is on /dev/sda3. Sounds wierd, checking it.  
### macosx=/dev/sdb3
macosx=sd0:3

image=/boot/vmlinux
root= /dev/sdc4
label=UBU
read-only
initrd=/boot/initrd.img
##append="quiet splash"
## this is an alias format for the single firewire disk 
device=fw/node/sbp-2/disk:
partition=4
######above stuff applies to the ubuntu boot image only

######comment all this out
##image=/boot/vmlinux.old
##label=old
##read-only
##initrd=/boot/initrd.img.old
##append="quiet splash"
#############

---

### Post by pxwpxw on 2007-06-06
Boot yaboot this way. dont be alarmed, not much to do.

All assumes your firewire bootstrap is still at /dev/disk2s2  or macosx.

paste the edited yaboot.conf into textedit, save to a file yaboot.edit, open the file and check it is ok. If something doesnt work here, it may be a typo on my part, so let me know. 

mount the bootstrap partition /dev/disk2s2 as before.

```

sudo mount -t hfs /dev/disk2s2 aaa
ls -l aaa
cp aaa/yaboot.conf yaboot.conforig
sudo cp yaboot.edit aaa/yaboot.conf
ls -l aaa
cat aaa/yaboot.conf
sudo sync
sudo umount aaa

```

To set the boot-device to boot yaboot, which should show its small menu on a black sceen when your restart:

First, shut down the G5 (power down), make sure the firewire external is powered ON and running, then restart the G5, back into macosx.
In terminal:

```

nvram boot-device
sudo nvram boot-device = fw/node/sbp-2/disk:2,yaboot
nvram boot-device

```
(to chack before and after, you can save your terminal text for reference)

Then restart. If/when it boots into ubuntu, dont worry if you dont get a desktop sceen at first try. 
See if Command Alt F2 gets a terminal or just restart using the power button. 
 If you can use a text console or a desktop terminal 
```

df
sudo mac-fdisk -l

```
will show drive names - need that info to finish. If not, no matter, just need to know if it boots and where to. Hope it gives you full GUI desktop.
 Restart from ubuntu console:
```

sudo reboot

```

 If necessary, the rescuedisk can be used to set ubuntu to boot into text console mode to sort out the finishing off, but thats a well discussed part of getting started that happens, not due to a bad install. 

The yaboot.conf edited is on the bootstrap partition. For the final boot, the yaboot.conf in the /etc directory of your ubuntu root / partitiion has to be edited.

---

### Post by stylecramper on 2007-06-06
> **pxwpxw said:**
> mount the bootstrap partition /dev/disk2s2 as before.

```

sudo mount -t hfs /dev/disk2s2 aaa
ls -l aaa
cp aaa/yaboot.conf yaboot.conforig
sudo cp yaboot.edit aaa/yaboot.conf
ls -l aaa
cat aaa/yaboot.conf
sudo sync
sudo umount aaa

```


Small snag. I deleted the original aaa directory from last time, and created a new one before starting the above commands. Here's the result:

[COLOR="RoyalBlue"]```
Brainiac:~ matt$ mkdir aaa
Brainiac:~ matt$ sudo mount -t hfs /dev/disk2s2 aaa
mount_hfs: Invalid argument
```[/COLOR]

This worked last time. I also reissued the [COLOR="RoyalBlue"]sudo pdisk -l[/COLOR] command and everything was the same as before. I tried restarting and redoing it a couple of times with no success.

---

### Post by pxwpxw on 2007-06-07
Edited - I am getting the same mount  problem as you, never seen before, I am chasing it now. Arrrrrrrrgh.
========================


===========================
Also important, drive names and numbers - just rechecked here and the mapping of macosx to linux is:
========================== 
macosx -------------  linux
 disk2----------------- sdc-----my external firewire
 disk1----------------- sda----original  sata internal
 disk0-----------------sdb-----added sata

Not quite what I said before. I dont think it affects yaboot.conf so far, I will check and post shortly.

Added this comment in yaboot,edit posted above.
#### macosx= will need changing before reinstalling the bootstrap, to an open firmware path, wont affect initial boot yaboot.
### and macosx is on /dev/sda3. Sounds wierd, checking it.
### macosx=/dev/sdb3
macosx=sd0:3
(thats a zero)

---

### Post by pxwpxw on 2007-06-07
**stylecramper **

No progress here with the macosx mounting problem.From mcosx I can mount the bootstrap partitions I have on the internal disks, or I can mount other partitions on the firewire,  and I can boot the firewire ubuntu and mount the bootstrap in ubuntu. But suddenly I cant mount the firewire bootstrap in macosx now. Im sure something must be ruuning interference but cant find it.

Im out of sleep, I am going to power down the lot over night and see if that does anything. Have not had this happen before. You could mount the partition before also

If I cant fix this hiccup, the alternative is to reinstall (again) on firewire, but make it put the 
bootstrap files in the Apple_Free 128M partion at your internal sata macosx disk1s1, or if that worries you, the other sata disk0s2 Apple_Free, that will get the firewire out of the initial problem, I normally boot firewire that way. Then that should be accessible from macosx, or probably a rescue disk. But just now I dont feel very happy with this, suggest leave it for next day, all switched off if possible, to see if something comes good. If you had some spare space on the sata disks, you could instal a minimal ubuntu install in around 5GB or less.


OK got the answer, Plan B - can boot firewire from your macosx partition using  only yaboot and yaboot.conf. Probably easier. See next post.

---

### Post by pxwpxw on 2007-06-07
Plan B:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc64/netboot/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc64/netboot/)

Index of /ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc64/netboot
  
[   ] yaboot     15-Apr-2007 13:03  150K  


Just download yaboot ( in macosx, use safari) 

(dont need the yaboot.conf from there, and not about to do a netboot)

I think its the same small binary file for all recent dists. It just loads
the kernel.

Thats all you need + the edited yaboot.conf posted above.

Put these together in the main macosx system partition top level.
(Not in  a folder)
 You can boot your ubuntu firewire initially from those 2 files, 
 yaboot.conf  as edited may not need any change at this stage.(i.e. it might work, I wil check)

Then do the boot-device setting as explained before but the boot device is changed (easier).

If you put them on yout macosx partition at disk1s3, boot-device is sd0:3 (or if its not sd0:3 then its sd1:3) The name reversals are a bit confusing until you can get a linux listing.
so 
 >>>>EDIT: note, the = sign was omitted inprevious posts too<<<<
```

nvram boot-device
sudo nvram boot-device = sd0:3,yaboot
nvram boot-device

```
Save a copy of the previous setting.

Then log out of macosx and restart.

If it fails to boot it wont do any damage, but you will probably have to power off and restart, or it just wont go anywhere.

If you get as far as the yaboot menu hit <tab>, you should see UBU, but may have to fix yaboot.conf if it sticks there.

I will give it a test run here ASAP on my g5, and last time I tried that it worked from a macosx extended journalled partition, anything fro there down to macos standard.
===========================
OK, it works on g5 here, but I get no yaboot menu display, just a couple of grey screens and then it boots ubuntu (only choice)
Can stil boot back into macosx by option - icon selector.

---

### Post by stylecramper on 2007-06-07
> **pxwpxw said:**
> Plan B:

...

If you put them on yout macosx partition at disk1s3, boot-device is sd0:3 (or if its not sd0:3 then its sd1:3) The name reversals are a bit confusing until you can get a linux listing.
so 
 >>>>EDIT: note, the = sign was omitted inprevious posts too<<<<
```

nvram boot-device
sudo nvram boot-device = sd0:3,yaboot
nvram boot-device

```


OK, snag. Entering the commands above got this result:

[COLOR="RoyalBlue"]Brainiac:~ matt$ nvram boot-device
boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
Brainiac:~ matt$ sudo nvram boot-device = sd0:3,yaboot
boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
nvram: Error (-1) getting variable - 'sd0:3,yaboot'[/COLOR]

---

### Post by stylecramper on 2007-06-07
Just reread your previous post and thought I'd try [COLOR="RoyalBlue"]sudo nvram boot-device = sd1:3,yaboot[/COLOR] - the result was the same error.

---

### Post by jrlohr on 2007-06-07
> **pxwpxw said:**
> 
Added this comment in yaboot,edit posted above.
#### macosx= will need changing before reinstalling the bootstrap, to an open firmware path, wont affect initial boot yaboot.
### and macosx is on /dev/sda3. Sounds wierd, checking it.
### macosx=/dev/sdb3
macosx=sd03
(thats a zero)

pxwpxw the line macosx=sd03 should be macosx=sd0:3 you need the colon.

---

### Post by jrlohr on 2007-06-07
> **stylecramper said:**
> OK, snag. Entering the commands above got this result:

[COLOR="RoyalBlue"]Brainiac:~ matt$ nvram boot-device
boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
Brainiac:~ matt$ sudo nvram boot-device = sd0:3,yaboot
boot-device     /ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@0/disk@0:2,\\:tbxi
nvram: Error (-1) getting variable - 'sd0:3,yaboot'[/COLOR]

do a man on nvram but here is the short the stuff after the = sign must be in " ????" because it only excepts strings

---

### Post by stylecramper on 2007-06-07
> **jrlohr said:**
> do a man on nvram but here is the short the stuff after the = sign must be in " ????" because it only excepts strings

OK, it looks like it was having trouble with the spaces around the equals sign. If I run [COLOR="RoyalBlue"]nvram boot-device[/COLOR] now, the output is [COLOR="RoyalBlue"]sd0:3,yaboot[/COLOR].

After restarting, my Mac does attempt to boot into Ubu now. However, I get the same error as I do when I try to boot from the Live CD: an error appears with something like"Failed to start the X server", and I'm shown a text screen that asks if I want to view some output. After that I can get to a command prompt and an error message repeatedly comes up that says "bcm43xx_microcode5.fw not available or load failed".

Also, in the list of things that are [OK], one item is [Failed] - 
[COLOR="RoyalBlue"]"Starting pbbuttonsd
ERROR: The object '/dev/adb' doesn't exist".[/COLOR]

I issued the [COLOR="RoyalBlue"]sudo reboot[/COLOR] command and was able to get back to Mac OSX by holding the Option key during restart.

I guess we're getting somewhere anyway!

---

### Post by pxwpxw on 2007-06-08
Brilliant, sorry about all the  hiccups. If you are getting to a text console, you have all the access you need to sort out the x server. 

The bcm43xx error is just the OS trying to bring up airport - annoying, can be turned off, or set up fully for wireless

The adb error I get at startup, forget it, someone will tell you how to stop it looking for that, dont think it matters.

You fix the x server config using
```

dpkg-reconfigure xserver-xorg

```

When it gets to video drivers, select     "nv" if you have nvidia, if you have sonething else,
maybe "ati"  see whats on the list.

When it gets to autodetect monitor (or something like that) choose the "medium"
option, and select your screen resolutuion only.

You can probably work out the other settings, but can be a bit diffficult sometimes.

When you exit the dpkg-reconfigure, to try it just run
```

startx

```

if that works, reboot and it should go. If you need mre help about getting set up in ubuntu, probably  another thread for that.


As for the needed yaboot re-install, suggest get the xserver going while booting as at now,
then more to do to get a more sensible way of starting up - xwindows will probably make things simpler to  do from ubuntu such as using browser etc..

I will continue to help  with the yaboot reinstall when you are ready.

---

### Post by pxwpxw on 2007-06-08
> **jrlohr said:**
> pxwpxw the line macosx=sd03 should be macosx=sd0:3 you need the colon.

Yes, thanks, fixed, very important. 
Fortunately does not affect yaboot booting linux, but needed later on.

---

### Post by pxwpxw on 2007-06-08
[B]stylecramper
[/B]
Here is a minimal yaboot.conf to replace the one you are using to boot via the macosx partition. It does the same job booting firewire, but with only the essential items. You can boot ubuntu anywhere on your system just by changing the 2 values for  device= and  partition= from macosx.

There was a lot of confusing stuff in the edited version that is irrelevant when booting yaboot directly, but needed when installing on the bootstap partition.
Timeout is set to 1 second. Checked OK on my system.

```

## minimal yaboot.conf for booting yaboot and linux kernel on external firewire
# timeout (secs*10) is needed else it will wait forever
timeout=10

image=/boot/vmlinux
label=firewire
read-only
root=/dev/sdc4
initrd=/boot/initrd.img
device=fw/node/sbp-2/disk:
partition=4
#
# halt is a yaboot command to drop back into open firmware
# restart from open firmware by entering "shut-down" or "reset-all"
image=halt
label=H
#

```

---

### Post by pxwpxw on 2007-06-08
Some outstanding points:

 == nvram boot-device: errors.

In macosx when the nvram boot-device= command is run, it will error if the target external drive was not switched on at the time off restart.

 == USB sticks

If a USB flash drive is plugged in at restart, it gets into the drive list, and can change the order for ather drives, e.g. from /dev/sdc to dev/sdd for my firewire. EDIT: not repeated on recheck.
Causing ubuntu restart to fail, init cant find anything.
No problem if plugged in after start. In general, changeing drive config at startup causes problems.

EDIT: still not sure about USB sticks, disregard.

 == getting into open firmware from macosx

```

 nvram auto-boot?
 sudo nvram auto-boot?=false

```
 Will restart into the open firmware grey screen. easier than using 4 fingers.
Warning:  the mac Option key - graphical icon boot selector needs auto-boot? true.
 From open firmware:
```

0> printenv auto-boot?
0> setenv auto-boot? true

```

 == Setting open firmware variables from ubuntu:

```

man nvsetenv

```
nvsetenv can do same things as nvram in macosx.

 == bcm43xx:

 bcm43xx (wireless) can be disabled by blacklisting it: (unwanted console logging was causing me problems)
  in  /etc/modprobe.d/blacklist ---- blacklist bcm43xx

---

### Post by pxwpxw on 2007-06-08
**macbug**

the macosx 
 mount -t hfs /dev/sdc2 aaa
 error blah blah

It was due to macosx excommunicating the Apple_Bootstrap partition after a previous session when it was mounted. ( macosx doesnt like imposters).

In  ubuntu: 

man hattrib hfsutils 

The partition can be re-blessed by using hattrib -b.

```

hmount /dev/sdc2
hls -l
hvol
hattrib -b :
humount

```

Then it mounts again.

Then I think the blessing lasts until the host mac is shutdown, I shut down overnight, or it might be a periodic macosx cleanup.

---

### Post by stylecramper on 2007-06-08
> **pxwpxw said:**
> You fix the x server config using
```

dpkg-reconfigure xserver-xorg

```

When it gets to video drivers, select     "nv" if you have nvidia, if you have sonething else,
maybe "ati"  see whats on the list.

When it gets to autodetect monitor (or something like that) choose the "medium"
option, and select your screen resolutuion only.

You can probably work out the other settings, but can be a bit diffficult sometimes.

When you exit the dpkg-reconfigure, to try it just run
```

startx

```

That had some problems. There were a lot of choices to make there; I had no idea on many  of them but tried to leave it at the default or make my best guess. I did select "ati" since I have a Radeon 9600. After issuing startx, I got the following screen:

[screenshot]("http://backattheranch.ca/matt/screen.jpg")

---

### Post by stylecramper on 2007-06-08
> **pxwpxw said:**
> [B]stylecramper
[/B]
Here is a minimal yaboot.conf to replace the one you are using to boot via the macosx partition. 

OK, I've updated that.

---

### Post by stylecramper on 2007-06-08
> **pxwpxw said:**
>  == bcm43xx:

 bcm43xx (wireless) can be disabled by blacklisting it: (unwanted console logging was causing me problems)
  in  /etc/modprobe.d/blacklist ---- blacklist bcm43xx

Thanks, it's good not to be bothered by that any more.

---

### Post by stylecramper on 2007-06-08
> **pxwpxw said:**
> Some outstanding points:

 == nvram boot-device: errors.

In macosx when the nvram boot-device= command is run, it will error if the target external drive was not switched on at the time off restart.

The drive was definitely on, but the command did work when I used it without spaces around the = sign.

---

### Post by pxwpxw on 2007-06-09
> **stylecramper said:**
> That had some problems. There were a lot of choices to make there; I had no idea on many  of them but tried to leave it at the default or make my best guess. I did select "ati" since I have a Radeon 9600. After issuing startx, I got the following screen:

[screenshot]("http://backattheranch.ca/matt/screen.jpg")

Got all those posts I think, thanks.

Screenshot: 

That bcm43xx error is nothing to do with X windows, its just splats over the screen and makes things difficult. Did you do the blacklist - should have stopped it at the next restart.

Or you can see if bcm43xx module is loaded:
```

 lsmod | less
#### unload it:
 sudo rmmod bcm43xx

```

I assume you are not using wireless at this stage.

The full log of X startup problems and the current X configuration are in
2 files - need to see thenm in full.

```

  /var/log/Xorg.0.log
  /etc/X11/xorg.conf
#####If you cant find them look here:
  ls -l /var/log | less
  ls -l /etc/X11 | less

####you can read them
  less /etc/X11/xorg.conf

```

If you post the text from these, I might be able to see the problem.

 But please advise your monitor screen native resolution.

 You need to be able to get text files from ubuntu to macosx for posting until you have X and desktop.

 If you have a macos <extended (but not journalled)> partition, you can mount that in linux and copy files to and from it. (journalled is not writeable from ubuntu)
 
 If not, use a USB stick, dos format (vfat) is ok, or hfs.
 A usb stick will probably be /dev/sdd. you can check its name quickly in /dev/
```
 
   ls /dev/sd* 

```
then:
```

  mkdir xxx
  sudo mount /dev/sdd xxx
  ls -l xxx
  cp /etc/var/log/Xorg.0.log  xxx/
  cp /etc/X11/xorg.conf  xxx/
  sudo sync
  sudo umount xxx

```

use man for help:
   man less nano

If you already knew that, good.

Oh, and could you please post the output from these 2 commands, it is for a related bug report I am working on. Relates to different firmware details btween G5s and yaboot installer.

```

 find /proc/device-tree/ -name compatible | grep sata >> pxwinfo
 find /proc/device-tree/ -name name | grep sata >> pxwinfo

```
copy pxwinfo to macos and post the text (only a few lines).

---

### Post by stylecramper on 2007-06-09
> **pxwpxw said:**
> Did you do the blacklist - should have stopped it at the next restart.

I did, I'm not seeing that error any more.

> **pxwpxw said:**
> The full log of X startup problems and the current X configuration are in
2 files - need to see thenm in full.

Xorg.0.log is [here]("http://backattheranch.ca/matt/Xorg.0.log")
xorg.conf is [here]("http://backattheranch.ca/matt/xorg.conf")


> **pxwpxw said:**
>  But please advise your monitor screen native resolution.

It's a 19" Samsung SyncMaster; I'm pretty sure the native resolution is 1280 x 1024.

> **pxwpxw said:**
> Oh, and could you please post the output from these 2 commands, it is for a related bug report I am working on. Relates to different firmware details btween G5s and yaboot installer.

```

 find /proc/device-tree/ -name compatible | grep sata >> pxwinfo
 find /proc/device-tree/ -name name | grep sata >> pxwinfo

```
copy pxwinfo to macos and post the text (only a few lines).

pxwinfo is [here]("http://backattheranch.ca/matt/pxwinfo.txt")

---

### Post by pxwpxw on 2007-06-10
Reading now. Thanks for pxwinfo - it solves my problem re g5 differences and yaboot/ofpath. Checking x info now.

---

### Post by pxwpxw on 2007-06-10
Xorg.0.log

There are only 2 errors, 1st might be non-fatal, 2nd looks nasty, not a problem with your configuration, monitor and ati card looks ok.  Looking further now (compare on my system).

> 
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting
(EE) end of block range 0xefffffff < begin 0xf0000000


> 
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): No legacy BIOS found -- trying PCI
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:f0:10.0/rom: got 76KB

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x94) [0x10090c04]


Any one else with the solution, please see full log and conf links in OPs post above.

---

### Post by pxwpxw on 2007-06-10
Xorg.0.log

 The rom BIOS 76KB in the 3rd line of the extract below from your log, is a bit strange, and seems to lead to the abort. 

 Would you please list the "rom" file to see what length it shows, probably should b 0 or 128KB (131072 bytes) as shown here for my g5 result but from an nvidia card. Not too sure of that. Seems to detect the rom OK elsewhere in the log.

```

$ ls -l /sys/bus/pci/devices/0000:f0:10.0/rom
-r-------- 1 root root    **131072 **  2007-06-10 20:50 /sys/bus/pci/devices/0000:f0:10.0/rom
$ 

```
What do you get?

 AGP card - had any problems? Unusual for a mac.
 X windows is a bit picky even about things you might not even use.

 From your Xorg.0.log:
```

(II) RADEON(0): initializing int10
(II) RADEON(0): No legacy BIOS found -- trying PCI
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:f0:10.0/rom: got 76KB
----
## leading to: 

Fatal server error:
Caught signal 7.  Server aborting

```

Only other thing I can think of is in xorg.conf, could try disabling DRI by commenting it out:
 
/etc/X11/xorg.conf
```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
####	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"

```

use nano for editor
```

cd /etc/X11
ls -l
sudo cp xorg.conf xorg.conf00
sudo nano xorg.conf
ls -l
cd
pwd

```

Check by rerunning startx, but allow also for a restart for final verdict.

---

### Post by stylecramper on 2007-06-10
> **pxwpxw said:**
> 
```

$ ls -l /sys/bus/pci/devices/0000:f0:10.0/rom
-r-------- 1 root root    **131072 **  2007-06-10 20:50 /sys/bus/pci/devices/0000:f0:10.0/rom
$ 

```
What do you get?

131072

 > **pxwpxw said:**
> AGP card - had any problems? Unusual for a mac.
 X windows is a bit picky even about things you might not even use.

No, it's always worked fine.

> **pxwpxw said:**
> Only other thing I can think of is in xorg.conf, could try disabling DRI by commenting it out:
 
/etc/X11/xorg.conf
```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
####	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"

```

use nano for editor
```

cd /etc/X11
ls -l
sudo cp xorg.conf xorg.conf00
sudo nano xorg.conf
ls -l
cd
pwd

```

Check by rerunning startx, but allow also for a restart for final verdict.

Did that and restarted, but it's the same.

---

### Post by pxwpxw on 2007-06-11
=========
X windows:
=========

 Beats me.

 There are people with that G5 model and AGP card who can probably help, but take it to the  "**Multimedia & Video**" forum to get more usefull advice. They will need the conf and log text in full.

Seems like an [ATI Radeon - X windows]  problem rather than Applemac specific.

 ** But first - search for "radeon" or "radeon bios" in that forum**.

 RadeonDriver
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

 My feeling is that it is in the BIOS interface, maybe a simple solution (i.e. tell X  not to use it, or the cause maybe elewehere) I dont know. If you look at <man radeon> there is some interesting but out of date stuff there, the log shows the submodule radeon is being loaded, but there may be a problem with module versions. I assume you are running Feisty.

(My g5 uses nvidia, which does not seem to use the BIOS interface, likewise the ibookg4 which has ATI but ignores BIOS rom)

 You should recheck the latest Xorg.0.log to see if the "got 76KB" is a consistent result. There is a whole chunk of stuff missing from that log that normally comes after there.

============================
Bootloader:
==========
**Edit: the yabootconfig method depends on ofpath giving correct paths for both sata and firewire. I am checking this on my g5 with a new version of ofpath.**

 I think you can probably finish off the booting issue by simply running 
```

man yabootconfig
sudo yabootconfig -b /dev/sds2

```

 If it works, this  will (a) rewrite yaboot.conf for you (b) reformat and rewrite the bootstrap partition /dev/sdc2.
 But depends on getting a correct answer out of <ofpath /dev/sdc2> for the firewire path.
 (I will add that info briefly below).

 That should get you a bootable icon for firewire. Your macosx boot, and the yaboot on macosx should be unaffected.
 You can also put a much faster 3rd alternative bootloader on one of the small 128MB Apple_Free partitions on your main sata drives, using <mac-fdisk> to set the type to Apple_Bootstrap, and then <mkofboot -b /devsdx> to format it and write the files.  Consult man.  
 The icon booting method is slow, and with the firewire drive in sleep mode, my system took 1 minute for the icon to even appear, before it was selectable.

---

### Post by pxwpxw on 2007-06-11
Not so brief but here it is:

If you get the right result here, <yabootconfig> is the easiest way to reinstall the boot partition. It needs the utility </usr/sbin/ofpath> to work for firewire drives.
From previous posts, ofpath is returning good paths for the sata disks on your g5.

1. Find the right answer for firewire (result for for my g5)
```

 find /proc/device-tree/ -name disk* | grep sbp
 /proc/device-tree/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0

```

2.  Check result from ofpath for the firewire drive /dev/sdc.

```

 ofpath /dev/sdc
 /ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0:

```
(that agrees, ofpath will add the colon :  )

3. If ofpath fails, yabootconfig wont work, ofpath needs a patch for that method. Skip the rest.

4. If ofpath is correct you can use yabootconfig. It rewrites /etc/yaboot.conf and does the complete boot partition installation. Needs to be told the boot partion you want (-b). It will reset the boot-device to boot directly from firewire, you can reset that manualy. It writes a very simple yaboot.conf, you can add macosx and change the timeout later. (see it in /etc/yaboot.conf)

Below is the output you see when you run yabootconfig, you answer y here: 
 check the boot-device before and after.
```

$ sudo nvsetenv boot-device
## returns boot-device
$ sudo yabootconfig -b /dev/sdc2
## the result to expect: 
yaboot is the Linux Loader for PowerPC.  yabootconfig sets up your system 
to boot directly from your hard disk, without the need for a boot CD, floppy
 or a network boot.

Install yaboot bootstrap on /dev/sdc2 to boot Linux from /dev/sdc6? [Yes] y
Creating a simple /etc/yaboot.conf...
Running mkofboot to make the disk bootable...
Done
## recheck the boot-device
$ sudo nvsetenv boot-device
boot-device=/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0:2,\\:tbxi

```

 the boot-device setting will boot directly into firewire/ubuntu.
5. Restart (option key) and try the penguin firewire icon.
===========================================================

---

### Post by stylecramper on 2007-06-12
Result of [COLOR="RoyalBlue"]find /proc/device-tree/ -name disk* | grep sbp[/COLOR]
[COLOR="DarkRed"]/proc/device-tree/ht@0,f2000000/pci@3/firewire@e/node@0030e000e0000858/sbp-2@c000/disk@0[/COLOR]

Result of [COLOR="RoyalBlue"]ofpath /dev/sdc[/COLOR]
[COLOR="DarkRed"]ofpath: Driver: sg is not supported[/COLOR]

---

### Post by pxwpxw on 2007-06-12
OK, I have a fix for that, no problem, but the local electric power is going off here for some hours, so I will be back after that.

---

### Post by pxwpxw on 2007-06-13
patchofp (patch for /usr/sbin/ofpath VERSION=1.0.7)
 
See following post for explanation.

The patch file is attached as patchofp.txt

Save it to  "patchofp" for use as explained in the following post.

---

### Post by pxwpxw on 2007-06-13
A patch for ofpath to enable firewire, usb, and sata paths, for yabootconfig and ybin. 
 ( Attached as patchofp.txt -  save to patchofp )
 $ ls -l patchofp
    -- --  2831 2007-06-16 00:33 patchofp

 The files /usr/sbin/ofpath and yabootconfig and ybin, are fom the ubuntu yaboot  package, used  for yaboot bootloader installation.  ( yaboot_1.3.13a-1ubuntu3_powerpc.deb )
  ofpath is a small executable script, currently does not support firewire, usb and some G5 sata configurations.

 The patchfile "patchofp" makes minor changes to ofpath, to fix these problems.

 It is my test version, subject to the usual "use at own risk" warnings,  I have tested it and yabootconfig on my external firewire xubuntu704, and no problem, booted from the result now. 

==============================================

  From your ubuntu firewire installation:

 (I assume you have ubuntu 704, the patch is for the current yaboot version but please check this first.)

 Should get these results:
```

 $ dpkg -s yaboot | grep Version
 Version: 1.3.13a-1ubuntu3
 
$ ofpath -V
 ofpath 1.0.7

```

 Assuming you name the patch file "patchofp".

 Do the patch and then run yabootconfig, with a few checks included:
============================
```

$ sudo patch -b --verbose /usr/sbin/ofpath patchofp 
## several lines report

$ ofpath -V
  ofpath 1.0.7.pxw.test.01

$ ls -l /usr/sbin/ofp*
-rwxr-xr-x 1 root root 26446 2007-06-13 22:35 /usr/sbin/ofpath
-rwxr-xr-x 1 root root 25820 2007-03-14 00:46 /usr/sbin/ofpath.orig

```
=================================
 ( patch -b saves a backup at /usr/sbin/ofpath.orig).

 See if it worked:
```

$ ofpath /dev/sdc2
/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0:2

```

Assuming thats ok, run yabootconfig, checking the boot-device before and after.
 Not that yabootconfig over writes or creates /etc/yaboot,conf, and resets the open firmware boot-device,
 The following  assumes that your boot partition is at /dev/sdc2, and yabootconfig is run from your firewire ubuntu system.

```

$ sudo nvsetenv boot-device
boot-device=sd0:2,\\:tbxi

$ sudo yabootconfig -b /dev/sdc2
yaboot is the Linux Loader for PowerPC.  
yabootconfig sets up your system to boot directly
from your hard disk, without the need for a boot CD,
floppy or a network boot.
Install yaboot bootstrap on /dev/sdc2 to boot Linux
 from /dev/sdc6? [Yes] y
Creating a simple /etc/yaboot.conf...
Running mkofboot to make the disk bootable...
Done

$ sudo nvsetenv boot-device
boot-device=/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0:2,\\:tbxi
$

```

Restart.

---

### Post by stylecramper on 2007-06-15
Everything to do with the patch seemed to go well.

When I first did [COLOR="RoyalBlue"]sudo nvsetenv boot-device[/COLOR], the result was:

[COLOR="DarkRed"]boot-device=sd0:3,yaboot[/COLOR]

At first I assumed I should do [COLOR="RoyalBlue"]sudo yabootconfig -b /dev/sdc3[/COLOR] next, but that failed. [COLOR="RoyalBlue"]sudo yabootconfig -b /dev/sdc2[/COLOR] was a success.

The second issue of [COLOR="RoyalBlue"]sudo nvsetenv boot-device[/COLOR] gave this result:

[COLOR="DarkRed"]boot-device=/ht@0,f2000000/pci@3/firewire@e/node@0030e000e0000858/sbp-2@c000/disk@0:2,\\:tbxi[/COLOR]

After rebooting and holding the Option key, the icons for the Mac OS disk and the Linux (firewire) disk had changed places - the Linux disk had always been on the right and is now on the left.

---

### Post by pxwpxw on 2007-06-15
Ah,  what a relief.
yes, sdc2 is the boot partition.

But did the new firewire Linux disk button work now - that will prove that the firewire boot partition is correct now? 

Then you should also get booted into firewire if you simply restart without any keys, let it default.

If all is ok, I can post  an edited yaboot.conf with all the optional extras and a yaboot startup menu.

---

### Post by pxwpxw on 2007-06-16
**stylecramper**

X windows.

If you are still unable to startx, one other possibility 

In /etc/X11/xorg.conf, make just one change, it may bypass that BIOS problem and get you a desktop. Dont change anything else.
Comment out the "ati" driver and replace by "fbdev"
 
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
#	Driver		"ati"
	Driver		"fbdev"
	BusID		"PCI:240:16:0"
EndSection

Section "Monitor"

```

```

sudo cp /etc/X11/xorg.conf xorg.confbak
sudo nano /etc/X11/xorg.conf

```

When I do this for an ibook normally using ati, it has that result, may work for the g5.

Run startx again, and post Xorg.0.log, I will compare it with the previous log from the ati driver, might be a clue..

---

### Post by stylecramper on 2007-06-17
> **pxwpxw said:**
> Ah,  what a relief.
yes, sdc2 is the boot partition.

But did the new firewire Linux disk button work now - that will prove that the firewire boot partition is correct now? 

Yes, it worked.

> **pxwpxw said:**
> Then you should also get booted into firewire if you simply restart without any keys, let it default.

Yes, but that was happening before already.

---

### Post by stylecramper on 2007-06-17
> **pxwpxw said:**
> Comment out the "ati" driver and replace by "fbdev"
 
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
#	Driver		"ati"
	Driver		"fbdev"
	BusID		"PCI:240:16:0"
EndSection

Section "Monitor"

```

When I do this for an ibook normally using ati, it has that result, may work for the g5.

Run startx again, and post Xorg.0.log, I will compare it with the previous log from the ati driver, might be a clue..

Uh...holy crap! When I ran startx I immediately went to a gorgeous desktop! I think we're there! Thanks so much for all the help. Log below.

[Xorg.0.log]("http://backattheranch.ca/matt/Xorg.0.txt")

---

### Post by pxwpxw on 2007-06-18
Thats good.
Maybe some cleaning up to do, I will check later.
 
 It is also a good idea to install a second Apple_Bootstrap partition on one of the sata internal drives, faster boot that way. You can use one of the Apple_Free 128MB partitions for that without upsetting disk partition numbers.

 And would you please post for my info, related to the firewire boot:

```

 cat /proc/cpuinfo
 cat /proc/scsi/scsi
 ls -l /proc/scsi

```
  =============================
 
 Here is a better yaboot.conf for your existing firewire boot, with additions to the minimal job that yabootconfig produces.
  ============================

 Edit for /etc/yaboot.conf which was generated by yabootconfig.

 Should be right for your system, but check it please.   

 Will give a first stage menu with additional options.
 Backup/rename the current version yaboot.conf first:
  
 Assumes:
 Apple_Bootstrap partition is /dev/sdc2
 ubuntu root partition is /dev/sdc4.
 macosx partition is /dev/sda3

  You must run ybin to update the boot partition from new /etc/yaboot.conf.
  ybin also up dates boot-device ( man ybin ), you can use ybin -v --nonvram to prevent that.
```

 sudo ybin -v

```

## yaboot.conf generated by yabootconfig 1.0.8
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of: 
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sdc2


#####THIS device= SETTING WAS MINE, YOURS IS DIFFERENT, GET IT WITH ofpath /dev/sdc########
### device=/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0:
###THIS CORRECTION uses aliases, same for g5s

device=fw/node/sbp-2/disk:


partition=4
root=/dev/sdc4
#### timeout in 1/10 secs is for 2nd stage boot:
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

#### additions for more 1st stage selections #######

## delay in secs for ist stage menu
delay=10
enablecdboot
enableofboot
enablenetboot
## use open firmware pathname for /dev/sda3
macosx=sd0:3
defaultos=macosx

#### additions end #######

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	initrd-size=8192

###============================
## add second stage abort 
image=halt
label=abort

##====

---

### Post by stylecramper on 2007-06-18
Dang, now it's hooped...when I restarted, I got the little menu and typed L. The result was:

[COLOR="DarkRed"]device=/ht@0,f2000000/pci@5/firewire@e/node@0001d200e08c0030/sbp-2@c000/disk@0: Unable to open file, invalid device[/COLOR]

I have to turn off my firewire HD to boot into OS X.

---

### Post by pxwpxw on 2007-06-19
Sorry about that, see my (too late) edit on my yaboot.conf post, 
That was my device path, wrong for your system.  It has to be corrected.

The yaboot.conf you produced by running yabootconfig had the correct device= path.
That can also be seen from your post above where you ran nvsetenv boot-device successfully.
However, I missed correcting that when editing my results.

The easiest way is to get back into ubuntu, using the original macosx  method to boot from the yaboot file on your macosx partition. (Plan B post #46 of this thread)

Then edit /etc/yaboot.conf to make the correction, I have shown that in my edited yaboot.conf post.

```

 sudo nano /etc/yaboot.conf

## change the device= line to
 device=fw/node/sbp-2/disk:

```

That uses aliases that are the same for  g5s, and is easier to type correctly than the full path.

Then to reconfigure the bootstrap partition rerun ybin
```

 sudo ybin -v

```

  Alternately:
 Go back to running yabootconfig which wiil rewrite a mini yaboot.conf for you, and allow you to boot ubuntu as before the change to yaboot.conf. Then post the yaboot.conf from that.

---

### Post by pxwpxw on 2007-06-19
See above,  and re:

> **stylecramper said:**
> Dang, now it's hooped...
I have to turn off my firewire HD to boot into OS X.

 Zap the pram - should put you back to macosx  (resets the boot-device).
 Comand Option p r 
 while starting up until 2 chimes.

---

### Post by stylecramper on 2007-06-20
OK, looks like we're good now. Finally - a working dual-boot machine. Thanks again for going above and beyond! I couldn't have done it without your help.

---

### Post by stylecramper on 2007-06-20
On a semi-related note...any suggestions as to how to get my Airport Extreme card working? It doesn't even show up in Network Settings.

---

### Post by pxwpxw on 2007-06-21
> **stylecramper said:**
> OK, looks like we're good now. Finally - a working dual-boot machine. Thanks again for going above and beyond! I couldn't have done it without your help.


Good to hear success at last, enjoy.

I would like to have some data about your system for my info if you could please, output from these:

```

 cat /proc/cpuinfo
 cat /proc/scsi/scsi
 ls -l /proc/scsi

```

**Airport:**

You will need to unblacklist bcm43xx ref post 55 - (/etc/modprobe/blacklist ) and see:

**PowerPC**
 [https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC)

**PowerPCFAQ**
 4. Drivers and Hardware
   1. Will my wireless work? 
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

( search for "airport" if that doesnt work, I have not used it here.)

=====================

---

### Post by stylecramper on 2007-06-21
> **pxwpxw said:**
> I would like to have some data about your system for my info if you could please, output from these:

```

 cat /proc/cpuinfo
 cat /proc/scsi/scsi
 ls -l /proc/scsi

```

See below:

```
matt@ubuntumatt:~$ cat /proc/cpuinfo
processor       : 0
cpu             : PPC970, altivec supported
clock           : 1310.960000MHz
revision        : 2.2 (pvr 0039 0202)

processor       : 1
cpu             : PPC970, altivec supported
clock           : 1310.960000MHz
revision        : 2.2 (pvr 0039 0202)

timebase        : 33333333
platform        : PowerMac
machine         : PowerMac7,3
motherboard     : PowerMac7,3 MacRISC4 Power Macintosh 
detected as     : 336 (PowerMac G5)
pmac flags      : 00000000
L2 cache        : 512K unified
pmac-generation : NewWorld

matt@ubuntumatt:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST380013AS       Rev: 3.05
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 6L200M0   Rev: BANC
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Maxtor 6 Model: E040L0           Rev:     
  Type:   Direct-Access-RBC                ANSI SCSI revision: 04
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: LEXAR    Model: JUMPDRIVE ELITE  Rev: 1000
  Type:   Direct-Access                    ANSI SCSI revision: 02

matt@ubuntumatt:~$ ls -l /proc/scsi
total 0
-r--r--r-- 1 root root 0 2007-06-21 09:29 device_info
dr-xr-xr-x 2 root root 0 2007-06-21 09:29 sata_svw
dr-xr-xr-x 2 root root 0 2007-06-21 09:29 sbp2
-r--r--r-- 1 root root 0 2007-06-21 09:29 scsi
dr-xr-xr-x 2 root root 0 2007-06-21 09:29 sg
dr-xr-xr-x 2 root root 0 2007-06-21 09:29 usb-storage
```

> **pxwpxw said:**
> You will need to unblacklist bcm43xx ref post 55 - (/etc/modprobe/blacklist ) and see:

Oh right, I thought that was just to block the error message...I've done that now. I'll check out those other resources, thanks.

---

