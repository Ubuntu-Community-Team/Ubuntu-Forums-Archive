---
title: "PowerMac G5 Booting Error"
date: 2007-02-19
forum: Apple PPC Users
---

### Post by randyjrsteffens on 2007-02-19
Hello!

I installed Ubuntu on a free internal hard drive in my G5, from the Live CD. Everything went great!  When I hold down the "option" key during start up, I am presented with a choice of which OS I want to boot.  I can select the OS X icon, or the Linux icon.  When I select Linux, I am presented with another screen asking me to hit l for Linux, x for OS X, and c for booting from CD.  However, when I hit l, I am taken back to the screen with the HD icons.  When I chose Linux once again, I am again presented with the screen asking me to hit l,x, or c.  If I hit l, I am taken back to the previous screen once again, in an endlessly repeating  cycle.  How can I successfully boot Ubuntu?

Thanks for any help you can provide!

Randy

---

### Post by didg on 2007-02-19
Did you move the hard drive?

---

### Post by randyjrsteffens on 2007-02-19
No, I never touched it.  I have two hard drives in my machine, and both are internal.  I allowed the Ubuntu installer to erase the entire second hard drive.  The first drive is running mac OS X.

Thanks for your help!

---

### Post by randyjrsteffens on 2007-02-19
Oh, by the way, I re-installed Ubuntu, with no change in the booting error.

---

### Post by didg on 2007-02-19
Weird, because what's your seeing is typical of a moved drive, ie you have the a boot partition because you can see it in the Mac chooser but the bootloader, which is loaded  (the second screen),  can't find yaboot and reboot, on the other hand I never installed Ubuntu on a G5, only run the live CD. 

Which version are you using?
If you restart with the live CD are you seeing your partition? If yes what's in /media/something/etc/yaboot.conf?

---

### Post by randyjrsteffens on 2007-02-20
I am using version 6.10. 

  When I run from the live CD, choose system>GNOME partition editor, and select my second drive from the drop down list, here is what I get:

The partition "/dev/sdb1" has a triangular warning symbol next to it, and the file system is "unknown".  

The next partition, "/dev/sdb2", is an "hfs" filesystem, that is flagged as "boot". 

"/dev/sdb3" is an "ext3" filesystem. 

"/dev/sdb4" is marked as "linux-swap" filesystem, flagged as "swap".

When I use the file browser to select the "media" folder, it appears to have nothing in it.

 Thanks!   --Randy

---

### Post by grazie on 2007-02-20
You need a bootstrap partition to boot linux. It's hopefully on your other drive /dev/sda. You didn't state what method you used to install Ubuntu. You get three options something like

1. Wipe  and use whole disk
2. Use largest free space
3. Set up disk partitions manually

Which selection did you make?

It would also be useful to post the outputs from the followiing

```
$ sudo mac-fdisk -l /dev/sda
$ sudo mac-fdisk -l /dev/sdb
```

---

### Post by randyjrsteffens on 2007-02-20
I chose the first option, "erase entire hard drive".  I didn't have anything on it I wanted to save.

Here is the result of the first query (sudo mac-fdisk -l /dev/sda)
           #                               type name                               length   base         (size ) system
/dev/sda1                 Apple_partition_map   Apple                         63 @ 1           (31.5k) Partition map
/dev/sda2                 Apple_Free                                            262144@64          (128.0M) Free Space
dev/sda3                  Apple_HFS Apple_HFS_Untitled_1       770662504@262208    (367.5G) HFS
dev/sda4                  Apple_HFS eDrive                       10498040 @ 770924712    (  5.0G)  HFS
/dev/sda5                Apple_Free Extra                                    16 @ 781422752   (   8.0k) Free Space

Block size=512,          Number of Blocks=781422768
DeviceType=0x0,        DeviceId=0x0


I will list the results of the second query in another post below.

Thanks!    Randy

---

### Post by randyjrsteffens on 2007-02-20
Here are the results for the query: sudo mac-fdisk -l /dev/sdb

# type name length base (size) system
/dev/sdb1      Apple_partion_map Apple        63@1    (31.5k) Partition map
/dev/sdb2      Apple_Bootstrap untitled            1954@64 (977.0k) NewWorld bootlock
/dev/sdb3     Apple_UNIX_SVR2 untitled          959144532@2018 (457.4G) Linux native
/dev/sdb4     Apple_UNIX_SVR2 swap             17626618@959146550 (8.4G) Linux swap

Block size=512, Number of Blocks=976773168
DeviceType=0x0,  DeviceId=0x0

---

### Post by grazie on 2007-02-20
Well you do have bootstrap partition and it's on /dev/sdb It wasn't easy to spot on your earlier post  - did you get those details from gparted?

The next thiing to do is post your /etc/yaboot.conf and /etc/fstab files. Boot the Live CD and in a terminal mount your HD as follows
```
$ sudo mount /dev/sda3 /mnt
```
Then post the output of the following
```
$ sudo cat /mnt/etc/yaboot.conf
$ sudo cat /mnt/etc/fstab
```

Finally
```
$  sudo umount /mnt
```
Depending on how you connect to the internet, you should be able to do this directly from the booted Live CD.

---

### Post by randyjrsteffens on 2007-02-20
The output for sudo cat /etc/yaboot/conf.  is : "no such file or directory"

The output for sudo cat /etc/fstab is:

```
unionfs / unionfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

---

### Post by grazie on 2007-02-20
Sorry, my mistake. I've corrected the cat commands in my previous post. Please try again.

---

### Post by randyjrsteffens on 2007-02-20
The sudo cat /mnt/etc/yaboot.conf yealded the same output as last time.

sudo cat /mnt/etc/fstab yielded:

```
# fs_spec                                                                       fs_file   fs_vfstype    fs_mntops
#
#UUID=DF000C7E-AE0C-3B15-B730-DFD2EF15CB91        /export        ufs         ro
#UUID=FAB060E9-79F7-33FF-BE85-E1D3ABD3EDEA         none           hfs      rw,noauto
#LABEL-This\040Is\040The\040Volume\040Name            none          msdos      ro
```

---

### Post by grazie on 2007-02-20
If that's the contents, then you should have had some errors during the install.

Can you describe exactly which G5 you have, which iso you downloaded and what steps you went through to do the install.

---

### Post by randyjrsteffens on 2007-02-20
I have a Dual 2 GHz PowerPC G5, with 3GB Ram.  I downloaded the file named "ubuntu-6.10-desktop-powerpc.iso".  As far as the installation, I inserted the live CD, held down the "c" key, and pressed "enter" at the prompt.   Once Ubuntu desktop was active, I clicked the "install" icon on the desktop.  I followed the on screen instructions, choosing full disc erase for my second internal hard drive (my primary internal hard drive runs OS 10.4.8).  The installation proceeded apparently normally.  After the installation, the computer prompted me to either restart, or continue using live CD.  After I chose restart, the computer ejected the CD and asked me to retract the tray, and press enter.  Here one odd thing did occur.  The tray wouldn't retract using the retract key (f12), so I manually retracted it, and pressed enter.  Nothing happened, so after I had pressed enter several times, and the same screen continued to display, I just forced the computer off by holding down the power key.  This exact sequence of events occurred both times I tried to install Ubuntu.  Should I try version 6.06?   Or should I perhaps use the install CD rather than the live CD?  

Thanks so much for your input.
Randy

---

### Post by didg on 2007-02-20
Randy 

the tray wouldn't retract using the retract key : it's a known bug with a known cause, it never works and anyway  won't  at this stage when the system is nearly down without userland running. I think you misunderstood what the msg say, on x86 you have to remove the CD otherwise it will boot again from it, not so on a Mac.


pressed enter: again a known bug with a known cause, CTRL+J should reboot/stop though. 

I think your problem is related to sata stuff ie ide drives are shown as scsi drives and it confused the installer.

About 6.06 I don't think it's a good idea, IIRC there's problems with fans.

 grazie made a mistake, it's 
sudo mount /dev/sdb3 /mnt
not sda3 this one is your OSX drive can you retry the the cat /mnt/etc/yaboot.conf with sdb3?

---

### Post by randyjrsteffens on 2007-02-20
Thanks! here is the output of the new code:

```
##  yaboot.conf generated by the Ubuntu installer
##
##run: "man yaboot.conf" for details. Do not make changes until you have!!
##see also : /usr/share/doc/yaboot/examples for example configurations.
##
##For a dual-boot menu, add one or more of:
##bsd=/dev/hdaX,  macos=/dev/hdaY,  macosx=/dev/hdaZ

boot=/dev/sdb2
device=/disc@0:
partition=3
root=/dev/sdb3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

---

### Post by didg on 2007-02-20
Ok, it's bad but not too bad :)

device=/disc@0:
is wrong

last questions before trying a fix:
output of 

cat /proc/scsci/scsi

find /proc/device-tree/ -name "*disk*"

cat /proc/dev-tree/aliases/hd

cat /proc/dev-tree/aliases/cd

cat /proc/dev-tree/aliases/ide0

---

### Post by randyjrsteffens on 2007-02-20
Thanks for your help.  I am getting the message "no such file or directory" for every one of the queries you listed.  Perhaps I am doing something wrong???

Randy

---

### Post by didg on 2007-02-20
Are you doing it from OSX or Linux liveCD? /proc is only in linux

---

### Post by randyjrsteffens on 2007-02-21
I was using the live CD.  

Here is exactly what I entered.

```
sudo mount /dev/sdb3 /mnt
```

Then,

```
sudo cat /proc/scsci/scsi
```

Followed by the other queries in the same manner.  Is that correct?


--Randy

---

### Post by didg on 2007-02-21
Oops, sorry my mistake.

it's 
cat /proc/scsi/scsi 
find /proc/device-tree/ -name "*disk*"
cat /proc/device-tree/aliases/hd

You

---

### Post by randyjrsteffens on 2007-02-21
Ok Great!

Here is what I got:

sudo cat /proc/scsi/scsi:

```
attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
     Vendor: ATA           Model:HDS724040KLSA80    Rev: KFAO
     Type: Direct-Acess                                           ANSI SCSI revision: 05
Host:scsil Channel: 00 Id: 00 Lun: 00
     Vendor: ATA           Model:ST3500641AS            Rev: 3.AA
     Type: Direct-Acess                                           ANSI SCSI revision: 05
```

---

### Post by randyjrsteffens on 2007-02-21
Output for:

sudo find /proc/device-tree/ -name "*disk*"
sudo cat /proc/device-tree/aliases/hd

```
/ht/pci@7/k2-sata-root/k2-sata@0/disk@0ubuntu@ubuntu:~$
```

---

### Post by randyjrsteffens on 2007-02-21
output for :
sudo cat /proc/device-tree/aliases/cd

```
/ht/pci@5/ata-6/disk@0ubuntu@ubuntu:~$
```

---

### Post by randyjrsteffens on 2007-02-21
Output for sudo cat /proc/device-tree/aliases/ide0:

"no such file or directory"

---

### Post by didg on 2007-02-21
Great, but no output for
find /proc/device-tree/ -name "*disk*"
?

---

### Post by randyjrsteffens on 2007-02-21
After I entered: 

```
sudo find /proc/device-tree/ -name "*disk*"

```
I was presented with 

```
ubuntu@ubuntu:~$
```

---

### Post by randyjrsteffens on 2007-02-21
I apologize, but I must have accidentally typed that query wrong!  I am now getting an output.

output for 
```
sudo find /proc/device-tree/ -name "*disk*" 

```
Is:
```
/proc/device-tree/ht@0, f2000000/pci@7/k2-sata-root@c-sata@1/disk@0
/proc/device-tree/ht@0, f2000000/pci@7/k2-sata-root@c-sata@0/disk@0
/proc/device-tree/ht@0, f2000000/pci@5/firewire@e/node@000bc2030003bda5/sbp-2@4008/disk@0
/proc/device-tree/ht@0, f2000000/pci@5/ata-6@d/disk
/proc/device-tree/firewire-disk-mode
/proc/device-tree/packages/sbp2-disk
/proc/device-tree/packages/atapi-disk
/proc/device-tree/packages/ata-disk
/proc/device-tree/packages/disk-label
```

Once again, sorry about that, and thanks for your help!
--Randy

---

### Post by didg on 2007-02-21
Ok I don't know exactly why ofpath fails (I'll try saturday, I can't restart G5s now).

boot the liveCD
Be careful and triple check that you always type sdb never sda it's your
OSX volume, you have a backup of the important stuff on it anyway, right? :)

open a terminal
```

sudo /bin/bash
umount /dev/sdb3
```

umount may return an error*, umount: /dev/sdb3: not mounted*, ignore it

type
```
mount /dev/sdb3 /mnt
mount -o bind /proc/ /mnt/proc
mount -o bind /sys /mnt/sys
mount -o bind /dev /mnt/dev

cd /mnt

chroot . bin/bash
cd /etc
```
edit yaboot.conf and replace the line
**device=/disc@0:**
by
**device=/ht/pci@7/k2-sata-root/k2-sata@1/disk@0:**
and add the following lines:
**ofboot=/ht/pci@7/k2-sata-root/k2-sata@1/disk@0:2**

your yaboot.conf before :

```
boot=/dev/sdb2
device=/disc@0:
partition=3
...
```

now:   
```
boot=/dev/sdb2   
device=/ht/pci@7/k2-sata-root/k2-sata@1/disk@0:
ofboot=/ht/pci@7/k2-sata-root/k2-sata@1/disk@0:2
partition=3
...

```

again type
```

ybin -v --nonvram
exit
umount /mnt

```
reboot

--nonvram doesn't change the default disk in openfirmware so you have to choose linux with the ALT key at power up.

---

### Post by randyjrsteffens on 2007-02-21
After typing 

cd /etc

what do I type to see the contents of, and edit yaboot.conf?

Thanks!

Randy

---

### Post by didg on 2007-02-21
The easiest? If you're using Ubuntu live cd before you type 

```
chroot . /usr/bin
```
type

```
gedit  /mnt/etc/yaboot.conf
```

make changes and quit gedit
and go on with chroot

OT but can you run 
```
sh -x /usr/sbin/ofpath /dev/sdb3 2> /tmp/out
```
and post /tmp/out ? I'd like to understand why ofpath failed.

---

### Post by randyjrsteffens on 2007-02-21
output of:
```
sh -x /usr/sbin/ofpath /dev/sdb3 2> /tmp/out

```
is:

```
/disk@0:3
```

I'll try the new code you gave me.

Thanks,

Randy

---

### Post by randyjrsteffens on 2007-02-21
Ok, did as you said, and edited yaboot.conf

when I come to the ybin -v --nonvram command, I get the output:

Failed to initialize HFS working directories: No such file or directory 
ybin: /dev/sdb2 appears to have never had a bootstrap installed, please run mkof boot

Upon restart, the initial problem still exists.

--Randy

---

### Post by didg on 2007-02-21
Ok, sorry I forgot one thing
before you run ybin -v --novram
type:
export HOME=/tmp

you don't need te redit yaboot.conf

---

### Post by randyjrsteffens on 2007-02-21
Ok, after running 

export HOME=/tmp

and then

ybin -v --nonvram

I get the following message:

hmount: /dev/sdb2: not a Macintosh HFS volume (invalid argument)
ybin: /dev/sdb2 appears to have never had a bootstrap installed, please run mkofboot

Thanks!

Randy

---

### Post by didg on 2007-02-22
And you when you reboot you still have the linux icon and first stage bootloader?
If not you can use mkofboot rather than ybin
If yes I'm not sure, there's something I don't understand.

What's you can do if you have the firt stage boot loader is enter o
and type after the prompt 0 >
boot /ht/pci@7/k2-sata-root/k2-sata@1/disk@0:2,\install\yaboot

---

### Post by didg on 2007-02-22
sorry
boot /ht/pci@7/k2-sata-root/k2-sata@1/disk@0:2,\yaboot

---

### Post by randyjrsteffens on 2007-02-22
Well, I re-installed the Ubuntu OS, and went through the entire procedure you outlined once more, and it WORKED!!

THANKS SO, SO MUCH!!

--Randy

---

### Post by didg on 2007-02-25
Great.
If you have time on your new shinny linux box can you run from a terminal:

sh -x /usr/sbin/ofpath /dev/sdb3 2> /tmp/out

And post the file in tmp folder:
/tmp/out

I'm trying to figure out why it doesn't find the openfirwmare path for your disk.

---

### Post by aboz on 2007-02-27
It's a bug in ofpath.  I had to battle with this one too.  

[http://ubuntuforums.org/showpost.php?p=2116501&postcount=16](http://ubuntuforums.org/showpost.php?p=2116501&postcount=16)

---

### Post by TheCleaner on 2007-03-29
Any chance that didg or the OP is still around?

I'm having the exact same problem only I have a single hard drive.  Almost all of my screen outputs were the exact same as mentioned here.  I erased the drive and have followed the directions given...getting all the way to a terminal screen that said something like "Blessing with Penguin Pee".

Then I reboot and it locks up and I force it off then on, and now I get a white screen saying "Loading second stage bootloader" and then it keeps repeating.

Any help is much appreciated!

---

