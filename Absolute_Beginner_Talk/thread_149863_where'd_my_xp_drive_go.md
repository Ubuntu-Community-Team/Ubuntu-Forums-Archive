---
title: "where'd my xp drive go??"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by geek_overlord on 2006-03-24
I installed Ubuntu on my xp drive and liked it so much that I decided to get another hard drive. During the install I had the option of which drive I wanted to partition. The volumes were the same but the original drive was sata and the new one is ide. I installed Linux on the ide and as expected everything went smoothly but now I can't boot into XP. When grub comes up I have the option to hit esc and select which drive I want to boot into but I can't see the xp drive in there at all. I don't think I wiped it by accident so I'm assuming I'm just missing something. Can anyone tell me what I need to do from here? I'm not too familiar with the command line but I can type so if you need to see a report or something just let me know. Thanks in advance for the help.

---

### Post by Pragmatist on 2006-03-24
We definitely need some info, so please type these commands in a terminal and cut & paste the output in a post here:

```
dmesg |grep drive
```

```
mount
```

For this next one, the extension .lst contains a lower-case L not a #1.
```
cat /boot/grub/menu.lst
```

```
ls -l /dev/sd*
```
```
ls -l /dev/hd*
```

When you type this next one in the terminal, a window will open (kinda like Window's "device manager").  Let us know what you find about your drives.
```
hal-device-manager
```

---

### Post by ncappel1 on 2006-03-24
Winblows doesn't like to be installed on any disk that isn't the master. I had to find this out the hard way... Watch out for this, or else you'll run up against some problems!

---

### Post by geek_overlord on 2006-03-24
Yeah just what I need... a @#$ little os that throws a hissy fit because it can't be first. No worries though. It'll be replaced soon enough. On to the important stuff. Here's what I got for the first part. 

~$ dmesg |grep drive
~$ mount
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

(note that nothing came up for the first command.)

~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/mapper/Ubuntu-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-386 root=/dev/mapper/Ubuntu-root ro single
initrd          /initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro single
initrd          /initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

 ls -l /dev/sd*
brw-rw----  1 root disk 8, 0 2006-03-24 06:46 /dev/sda
brw-rw----  1 root disk 8, 1 2006-03-24 06:46 /dev/sda1
brw-rw----  1 root disk 8, 2 2006-03-24 06:46 /dev/sda2
brw-rw----  1 root disk 8, 5 2006-03-24 06:46 /dev/sda5

ls -l /dev/hd*
brw-rw----  1 root cdrom 22, 0 2006-03-24 06:46 /dev/hdc

here's what came up in the terminal

<gtk.Menu object (GtkMenu) at 0xb6b3ae8c>
/usr/share/hal/device-manager/DeviceManager.py:45: GtkWarning: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
  LaunchpadIntegration.add_items (widget, -1, False, True);

Now as for the device manager I can see my Nforce ide controller but my dvd drive is listed as the master. I should see two channels as the ide hdd is on the primary cable with the dvd drive on the secondary. It's odd that it doesn't show up here. I also see my sata controler and the hdd (reported as a scsi drive. don't know why it always does that. same thing in windows.) I'm pretty familiar with device manager and everything looks the same as it always has been in here. So regarding partitions, I'm pretty sure sda5 was a left over swap drive from suse. Before I installed the ide drive there was an icon on my desktop for sda1 so I'm assuming that is my sata drive. beyond that your guess is as good as mine. I said this before but it bears repeating... man this is a fast forum. Thanks for the help.

---

### Post by Jason_25 on 2006-03-24
Yikes those are alot of commands he had you post.

```

sudo fdisk -l

```
and
```

mount

```
Will show you all your disks/partitions and where they are mounted.

---

### Post by geek_overlord on 2006-03-24
Here's what I got for sudo

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       24321   195109425    5  Extended
/dev/sda5              32       24321   195109393+  8e  Linux LVM

and for mount

/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

### Post by Jason_25 on 2006-03-24
That shows that you only have one hard drive.  A 200GB (probably sata).  No other drives were found.  Also you don't seem to have a swap file either.  Check that your IDE drive is still powered and connected.

---

### Post by geek_overlord on 2006-03-24
That's really odd because when I partitioned the drives I was sure it listed two distinct  hard drives. So at this point I guess I've hosed my xp partition and it's all Ubuntu? I still need to have XP for some things but I know it should be installed first. So do I wipe my Linux drive and start over again? This is very frustrating.](*,)

---

### Post by Jason_25 on 2006-03-24
It looks like a hardware problem to me.  No matter the state of the partitions on the drives, fdisk should list them.  That's why I asked you to check the connections.

---

### Post by geek_overlord on 2006-03-24
ok I'll open the box up and have a look at the drive. brb

---

### Post by akiro.yamamoto on 2006-03-24
Check the BIOS setting and ensure that the PATA drives are still enabled.
I suspect that with the addition of the SATA drive the configuration was changed
to SATA only and the PATA was disabled.

---

### Post by geek_overlord on 2006-03-24
ok the primary ide channel has my new drive hooked up as the master with no other devices on the channel. Per the instructions from Seagate I have installed two jumpers (odd because I've never seen that before but I guess they know what they're talking about) on the pins. My dvd burner is the primary device on the second ide channel. All my molexes are plugged in and I verified the sata is also plugged in. I think I'm going to wipe the sata drive and start again.

---

### Post by geek_overlord on 2006-03-24
Interestingly enough the bios never gave an option to boot from pata or sata but I have never had a problem booting into xp with my sata drive. I did check the bios right after I had this problem and I still had my dvd burner listed as the first device in the boot order. I changed it to hdd0 but I still went right back into Ubuntu. I then changed it to hdd1 with the same results. there is another option in the menu to "boot other device". Should I enable that instead?

---

### Post by akiro.yamamoto on 2006-03-24
Don't......
The primary ide drive (PATA) just re-check that the jumper on the drive is set for MASTER (there is usually a key / label) and the BIOS settings.
A re-install of Ubuntu will not help.

---

### Post by akiro.yamamoto on 2006-03-25
Is your PATA drive listed (with drive goementry info) in the BIOS.
That double jumper setting seems wrong to me.....

---

### Post by geek_overlord on 2006-03-25
btw Akiro, nice icon you have there. I'm a big fan of the first matrix.

---

### Post by geek_overlord on 2006-03-25
seems wrong to me too but I found that configuration on the seagate site. I've never even seen that before. Ok I'm gonna remove the second pin so that it's set to master and restart the system. Can you tell for sure if I hosed my xp partition? What kind of issues will I have if I try to install it with linux already there?

---

### Post by akiro.yamamoto on 2006-03-25
[quote=geek_overlord]btw Akiro, nice icon you have there. I'm a big fan of the first matrix.[/quote]

Thanks.... ;)
I cant even remember where I picked it up....:rolleyes:
Here.... Although the I can't use the animated .gif as my Avatar ](*,)

---

### Post by akiro.yamamoto on 2006-03-25
Your PATA drive is not even listed....
Therefore your computer is not even seeing it.........
That double jumper setting seems WRONG.... and I have done this type of thing
over 100 Times (I build systems ;) )

---

### Post by geek_overlord on 2006-03-25
ok I'm powering down so I can crawl into the box and remove the second jumper. I'll post results when I get back on line. $#@^% seagate.The thing that kills me is that I shoulda known better. brb

---

### Post by akiro.yamamoto on 2006-03-25
This is what I get from fdisk -l cammand.

---

### Post by geek_overlord on 2006-03-25
Yeah I get no drive geometry for the pata drive in the bios. I used both the master setting and the csel (I have the right kind of cable for that) with no results. I guess I got a bad drive. I double checked the cables and nothing seems out of place. Back to Compusa tomorrow for a replacement.

---

### Post by akiro.yamamoto on 2006-03-25
[quote=geek_overlord]Here's what I got for sudo

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       24321   195109425    5  Extended
/dev/sda5              32       24321   195109393+  8e  Linux LVM

and for mount

/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)[/quote]

Now according to this Ubuntu has taken over the SATA drive.
I thought you had One PATA (IDE) Hard drive => With Ubuntu Installed to it
And One SATA Hard drive with XP installed to it.

Isn't the PATA the new drive you bought recently, and the SATA the original Drive?

---

### Post by akiro.yamamoto on 2006-03-25
What is the specifications of :
1) Motherboard (name and model# )
2) SATA drive (name and model#)
3) PATA drive (name and model#)

We may have to track down why these parts seem not to want to play nice together. Perhaps there is a proceedure specific to your MB to enable the PATA.

---

### Post by geek_overlord on 2006-03-25
Sorry for the confusion. The sata is the original drive which had windows on it. Recently I installed Ubuntu on that drive as well and they coexisted just fine. I went out and bought the pata drive (the source of the problems) so I could have more room for Ubuntu.

---

### Post by akiro.yamamoto on 2006-03-25
How many hard drives do you have installed on your system???
1 SATA and 1 PATA or 
2 SATA and 1PATA ? 

I'm not trying to be difficult ;) It's just that your losing me a little......
Because if you have only 1 SATA drive (The original drive) which is the one
XP was installed to...... well I think I have some bad news for you......
'cause it appears that you no longer have a NTFS partition on that HD, therefore
you no longer have XP..... :(

---

### Post by geek_overlord on 2006-03-25
1 sata and 1 pata. Fortunately I had most of my data backed up but it's gonna be a pain in the neck to do this all over again. Everything worked well when xp and Ubuntu shared the same drive but I had to go screw it up. I knew I shouldn't have bought this !@$#@^ ide drive. So if I install xp on the sata with linux what kind of problems will I have with the mbr?

---

### Post by akiro.yamamoto on 2006-03-25
This may seem like a pain, but unless you have done extended changes to the Ubuntu install. I would recommend :
1) Backup personal data ( /home ) from the Ubuntu Install.
2) Pop in the XP cd. Erase all partitions.....
3) Create a 20GB NTFS Partition ( For XP)
4) Install XP
5) Use the Ubuntu Install CD... Boot , Partition / , /home , <swap> (you can also
 create a 50GB EXT3 part. to exchange files between XP and Ubuntu).
6) When the install is complete. Go [** HERE !!! **](http://www.fs-driver.org/) for the Win Ext File System driver (this enables Win to read and write
ext2 and ext3 partitions 8) ).

The reason I would recommend this approach is that it will be the easiest way.
In order to install XP you will have to resize the current partitions. Then install XP, finally redo the GRUB installer. Which can be frustrating at best, with many steps involved (each partition has to be sized and moved)....

---

### Post by geek_overlord on 2006-03-25
I'll do that. Thanks for all your help with this. I'll be back.

---

### Post by akiro.yamamoto on 2006-03-25
Your system should look something like this:
/dev/sda1 ntfs 20GB /media/win_xp (WinXP)
/dev/sda2 Reiserfs 20GB /  (ubuntu)
/dev/sda4 Reiserfs 100GB /home
/dev/sda5 ext3  59GB /media/data
/dev/sda6 <swap> 1GB <SWAP>

---

### Post by akiro.yamamoto on 2006-03-25
We still have not isolated the problem with the PATA drive.
I would recommend re-reading the mother board manual for any PATA configuration settings references. If you don't have a hard copy you can try the
manufacture's website for a .pdf copy and look for any update to your BIOS as well.

---

