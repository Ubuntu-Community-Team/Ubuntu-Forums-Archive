---
title: "After intall doesn't boot ubuntu"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by vlomasb on 2008-05-19
Hi.

I have installed 8.04 Hardy Heron in PowerPC G5. The partition table is:

/dev/sda1                    
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda8             
/dev/sda9             HFS+                    Macintosh  HD
/dev/sda10            Swap
/dev/sda11            Ext3                    / 
/dev/sda12            HFS                     NewWorldBoot

But when I reboot the Mac after the installation success only OSX  
start. I've tried a lot of thinks. For example, press the Command key and then show 2 icons, the first one is a HD from OSX and the second is the penguin (ubuntu) I click in the linux button ant then show a black screen with a menu:
l for linux
x for osx
c for cdrom

if I press l then the before screen shows.

I've read if I press command control o and f the shows Openfirmware. And then I write

> boot:hd,12

and then yaboot start. But I write device=/dev/disk@0 partition=11

And it says Unable to find........

I don't know what to do.

Thank you for your help

---

### Post by frog_pilot on 2008-05-19
It would be helpful, if you show your yaboot.conf

and the output of ```
ofpath /dev/sda12
```

(btw the shown device in your of menu isnt your root-volume. it is your newworld bootblock (sda12))

---

### Post by vlomasb on 2008-05-20
This I've get

sudo ofpath /dev/sda12
```

/disk@0:12

```

fdisk sda1  p
```
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sda9               Apple_HFS NotQuiteMaxDisk    156248177 @ 1824      ( 74.5G)  HFS
/dev/sda10        Apple_UNIX_SVR2 swap                 6151084 @ 156250001 (  2.9G)  Linux swap
/dev/sda11        Apple_UNIX_SVR2 untitled            61432560 @ 162401085 ( 29.3G)  Linux native
/dev/sda12        Apple_Bootstrap untitled                1954 @ 223833645 (977.0k)  NewWorld bootblock

```


Yaboot.conf
```
boot=/dev/sda12
device=/disk@0:
partition=13
root=/dev/sda13
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

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

Thank you.

---

### Post by frog_pilot on 2008-05-21
You don't need root privileges to print out an of path. But you get the same results as root and as user.

First of all your ofpath seems very short. Mine is like ```
/pci@f4000000/ata-6@d/disk@1:2
``` and I've seen only very similar ofpaths in the past. But let's proceed with your result...

> **vlomasb said:**
> Yaboot.conf
```
boot=/dev/sda12
device=/disk@0:
[COLOR="Red"]partition=13
root=/dev/sda13[/COLOR]
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

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

The red marked lines seem to be the problem. They have to point to the root volume - sda11 on your machine. Change the lines to ```
partition=11
root=/dev/sda11
```

You could also add the lines ```
enablecdboot
macosx=/dev/sda9
``` above the image-section to choose in the first stage yaboot menu (the one you mentioned in your first post) between cdboot, osx and linux.

The only thing which confused me about your partition scheme is that yaboot is on the last partition. I've ever had yaboot as the first partition for the linux section, in front of root, swap and anything else. Maybe thats why your yaboot autoconfig went wrong. And maybe this will be the main problem in case you cant fix the misbehavior of your machine...

To load your yaboot.conf into the boot device you have to execute ```
sudo ybin
``` from inside your running ubuntu system. I'm quite sure its only possible from within your system. As your system isnt bootable yet you have to chroot inside it from a live-cd-session.

If this isnt necessary, I hope someone will correct my posting. But dont mind, you wont harm your system, if you follow these steps.

Chroot into your installed system from a live-cd-session:

1. Start the machine from a desktop cd

2. Mount your root volume to /mnt ```
sudo mount /dev/sda11 /mnt
```

3. Mount the actual device-files to the target system ```
sudo mount -o bind /dev /mnt/dev
```

4. Mount the interface filesystem to the target system ```
sudo mount -t proc /proc /mnt/proc
```

5. Step into the target system (your actual installed system) ```
sudo chroot /mnt
```

6. Install yaboot to your bootloader volume sda12 ```
sudo ybin -v
``` the v Parameter means verbose. You will get an output from ybin which will show you hopefully success.

7. leave the target system ```
exit
```

8. reboot. Your system should come up with a working yaboot menu...

---

### Post by frog_pilot on 2008-05-21
You dont need to chroot into your System to install yaboot to your boot volume. On the [ybin manpage]("http://hermes.ppckernel.org/cgi-bin/man/man2html?8+ybin") you can find option ```
-C
``` for specifying the configuration file > -C, --config: config-file
Use config-file as the ybin/yaboot ( 8 ) configuration file instead of the default   /etc/yaboot.conf.

Simply start from the desktop cd. Create a folder to mpunt your root volume ```
sudo mkdir /media/root
``` mount your root partition to it ```
sudo mount /dev/hda11 /media/root
``` and execute ```
sudo ybin -v -C /media/root/etc/yaboot.conf
```

---

### Post by vlomasb on 2008-05-21
It doesn't happen nothing.

I made the chroot and ybin. Reboot and the same thing. Then I tried reinstall ubuntu, such as you said. First the Newworld partition, then "/".

The new structure is:

```

/dev/sda9               Apple_HFS NotQuiteMaxDisk    156248177 @ 1824
   ( 74.5G)  HFS
/dev/sda10        Apple_UNIX_SVR2 swap                 6151084 @
156250001 (  2.9G)  Linux swap
/dev/sda12        Apple_Bootstrap untitled                1954 @
213600240 (977.0k)  NewWorld bootblock
/dev/sda13        Apple_UNIX_SVR2 untitled            93224610 @
213602194 ( 44.5G)  Linux native
/dev/sda14        Apple_UNIX_SVR2 swap                 2877068 @
309704740 (  1.4G)  Linux swap

```

I have two swaps, because I can delete the first one, since LiveCD.

Then when I reboot the computer, the same thing. Reboot with LiveCD, at same time I read you second post (Don't necessary chroot). I checked the yaboot.conf and this is the new:

```
boot=/dev/sda12
device=/disk@0:
partition=13
root=/dev/sda13
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda9

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

I think this time is correct, but I tried with:

```
sudo ybin -v -C /media/root/etc/yaboot.conf
```

and got this:

```
ybin: Finding OpenFirmware device path to `/dev/sda12'...
ybin: Finding OpenFirmware device path to `/dev/sda9'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda12...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda12...
ybin: Installing /media/root/etc/yaboot.conf onto /dev/sda12...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda12 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
```

I reboot the MAC and the same thing.
Then I tried with OpenFirmware:
```
>0 boot hd:12,yaboot
```
Then Yaboot prompt show. And I typed:
```
/disk@0:13,/boot/vmlinux

```
```
Please Wait, loading kernel...
/disk@0:13,/boot/vmlinux: Unable to open file, Invalid device.

```

If I press only key enter, the same message:
```
Please Wait, loading kernel...
/disk@0:13,/boot/vmlinux: Unable to open file, Invalid device.

```

I don't know what to do.

Thank you for your help

---

### Post by frog_pilot on 2008-05-22
uhhrrrmmmm, sounds strange.

I dont know if the swap space in front of your linux volumes is the problem...

What exactly is happening during boot up. Will you see yaboot stage 1 (the one with the options l, c and x)? Will you see yaboot stage 2 (where you could choose a kernel)?

The output of ybin looks fine.

1. The only thing, I find is in your yaboot.conf. Change the lines 
```
append="quiet splash"
``` to ```
append="nosplash"
``` as suggested in [this thread]("http://ubuntuforums.org/showpost.php?p=5012076&postcount=2") for a G5. And then self evidently execute ybin.

2. You can try to hold the ALT-key during startup. Then a graphical of boot menu is coming up. There has to be a boot device with a penguin. Choose this.

3. If you want to reinstall - the live cd uses any existing swap space by default - but you can unmount the swap via gparted. Then you can erase your whole linux installation (2 SWAPs, bootblock, root). Leave the space free, let the installer "use biggest existing free space" to execute a default partition process.

//edit: 
4. If you get to yaboot stage 2 dont type the /boot/vmlinux stuff! The options available are:
```
Linux
``` for latest kernel


```
Linux old
``` for previous kernel


```
Linux single
``` for single user mode


or press TAB and choose one of the provided options

---

### Post by vlomasb on 2008-05-23
> Will you see yaboot stage 1 (the one with the options l, c and x)?
Yes, only if I press alt and then press Linux Icon. If I press l or x a graphical of boot menu is coming up.

> Will you see yaboot stage 2 (where you could choose a kernel)?
No, I can not see.

I could delete swap partitions, such as you told me. And then I could reinstall Linux. This time I choose all free space in HD such Linux. But the problem still go on.

This is the new table of partition:

```
/dev/sda1     Apple_partition_map Apple                     63 @ 1
   ( 31.5k)  Partition map
/dev/sda2          Apple_Driver43 Macintosh                 56 @ 64
   ( 28.0k)  Driver 4.3
/dev/sda3          Apple_Driver43 Macintosh                 56 @ 120
   ( 28.0k)  Driver 4.3
/dev/sda4        Apple_Driver_ATA Macintosh                 56 @ 176
   ( 28.0k)  Unknown
/dev/sda5        Apple_Driver_ATA Macintosh                 56 @ 232
   ( 28.0k)  Unknown
/dev/sda6          Apple_FWDriver Macintosh                512 @ 288
   (256.0k)  Unknown
/dev/sda7      Apple_Driver_IOKit Macintosh                512 @ 800
   (256.0k)  Unknown
/dev/sda8           Apple_Patches Patch Partition          512 @ 1312
   (256.0k)  Unknown
/dev/sda9               Apple_HFS NotQuiteMaxDisk    156248177 @ 1824
   ( 74.5G)  HFS
/dev/sda10        Apple_Bootstrap untitled                1954 @
156250001 (977.0k)  NewWorld bootblock
/dev/sda11        Apple_UNIX_SVR2 untitled           153451172 @
156251955 ( 73.2G)  Linux native
/dev/sda12        Apple_UNIX_SVR2 swap                 2878681 @
309703127 (  1.4G)  Linux swap
``` 

This is the new yaboot.conf:

```
boot=/dev/sda10
device=/disk@0:
partition=11
root=/dev/sda11
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda9

image=/boot/vmlinux
       label=Linux
       read-only
       initrd=/boot/initrd.img
       append="nosplash"

image=/boot/vmlinux.old
       label=old
       read-only
       initrd=/boot/initrd.img.old
       append="nosplash"
```

And this is the ybin -v -C /media/root/etc/yaboot.conf output:

```

ybin: Finding OpenFirmware device path to `/dev/sda10'...
ybin: Finding OpenFirmware device path to `/dev/sda9'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda10...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda10...
ybin: Installing /media/root/etc/yaboot.conf onto /dev/sda10...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda10 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
```

> . You can try to hold the ALT-key during startup. Then a graphical of boot menu is coming up. There has to be a boot device with a penguin. Choose this.


Yes, I've tried all this time. Because If I didn't hold ALT-key just MacOs start. 
Just when I choose penguin-boot show the yaboot stage 1. And then if I press l just the graphical menu show, and again.

Thnak you for your help

---

### Post by frog_pilot on 2008-05-23
So far, so good. But

> **vlomasb said:**
> Yes, I've tried all this time. Because If I didn't hold ALT-key just MacOs start. 
Just when I choose penguin-boot show the yaboot stage 1. And then if I press l just the graphical menu show, and again.
Thnak you for your help

what do you mean by [COLOR="Green"]"If I press l or x a graphical of boot menu is coming up." and "And then if I press l just the graphical menu show, and again."[/COLOR]?

After yaboot stage 1, there has to come up a second ascii-only menu, similar to stage 1.
a) a text about loading kernel (I dont remember the text right now)
b) this prompt ```
boot:
```

If you would press ENTER here, the  default kernel would load usually. Or you could use a option from my last post.

good luck...

---

### Post by vlomasb on 2008-06-05
Hi, Iam so sorry for answer to late. But I have had some problems.

Here we are. 

If I press alt key I get a graphical menu. The first one is Mac and the second button is Linux. If I press this button then a text menu appears. l for linux, x for mac and c for cd rom if I choose l then the graphical menu appears again and over and over.

Then I installed OpenSuse 10.3 for PPC. And I get success. The dual boot allow me choose mac or opensuse and the last one works fine. But I don't like OpenSuse. 

In another partition I have installed ubuntu. 

Is almost the same partition table the difference is:

/dev/sda10   hfs    boot
/dev/sda11   ext3   /  ubuntu
/dev/sda13   ext3   /  opensuse
/dev/sda12   swap

Some extrange because I couldn't find /etc/yaboot.conf on OpenSuse but I found /etc/lilo.conf Searching in google I read that OpenSuse use lilo mix with yaboot. But I couldn't understand. Any way, I added the option with yast bootloader for ubuntu. This is the /etc/lilo.conf on opensuse:

```

activate
timeout = 80
default = linux
boot = /dev/sda10

image = /boot/vmlinux-2.6.22.5-31-ppc64
###Don't change this comment - YaST2 identifier: Original name: linux###
    label = opensuse
    append = " quiet sysrq=1 insmod=sym53c8xx insmod=ipr"
    initrd = /boot/initrd-2.6.22.5-31-ppc64
    root = /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS167W4-part13

other = /dev/sda9
    label = Macc

image = /boot/vmlinux
    label = ubuntu
    initrd = /boot/initrd.img
    root = /dev/sda11
    append = nosplash

```

And this is the yaboot.conf that was generated by ubuntu installation on ubuntu's partitions:

```

boot=/dev/sda10
device=/disk@0:
partition=11
root=/dev/sda11
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda9

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"


``` 

But when I reboot opensuse and the computer ask me what OS I want  If I chose "ubuntu" the same error Invalid....

Then I changed this lines 

```
root=/dev/sda11
```

for this in /etc/lilo.conf
```
root = /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS167W4-part11
```

But the same

I don't kwon what is wrong.

Thank you for your help

---

### Post by frog_pilot on 2008-06-07
> **vlomasb said:**
> ```
activate
timeout = 80
default = linux
boot = /dev/sda10

image = /boot/vmlinux-2.6.22.5-31-ppc64
###Don't change this comment - YaST2 identifier: Original name: linux###
    label = opensuse
    append = " quiet sysrq=1 insmod=sym53c8xx insmod=ipr"
    initrd = /boot/initrd-2.6.22.5-31-ppc64
    root = /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS167W4-part13

other = /dev/sda9
    label = Macc

image = /boot/vmlinux
    label = ubuntu
    initrd = /boot/initrd.img
    root = /dev/sda11
    append = nosplash
```

And this is the yaboot.conf that was generated by ubuntu installation on ubuntu's partitions:

```
boot=/dev/sda10
[COLOR="Red"]device=/disk@0:
partition=11[/COLOR]
root=/dev/sda11
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda9

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"
```

IMHO your yaboot.conf looks fine. Maybe your ubuntu-root is broken. But if installation went fine on this without errors and you couldnt change anything yet because you wasnt able to boot into ubuntu then I have no idea wtf avoids ubuntu from starting up.

For the problem with your lilo.conf look at the marked lines. It is obvious that ubuntu wont start without these parameters. The ubuntu section in your lilo.conf should look like this
```

        image=/boot/vmlinux
        label=ubuntu
        read-only
        device=/disk@0:
        partition=11
        root = /dev/sda11
        initrd=/boot/initrd.img
        append="nosplash"
```

I suggest to verify your of-path (/disk@0:11) once again. Yours is very unusual. Start into opensuse, open a terminal and execute
# ofpath /dev/sda11
once again.

To check the filesystem on sda11 (for eliminating the possibility of a corrupt filesystem). Start into opensuse, open a terminal, unmount /dev/sda11
# sudo umount /dev/sda11
(if its mounted) and then execute
# e2fsck -v -p -f /dev/sda11
this will force a check of the filesystem in verbose mode, you will be asked for every change that has to be executed.

Report about your progress. Maybe there is a way to eliminate your problems by using opensuse to repair your ubuntu system :)

---

### Post by vlomasb on 2008-06-07
I was doing some test but I don't have success.

1) I installed Ubuntu 7.04 in /dev/sda11, because I thought Ubuntu 8.04 had a bug. When I reboot I got the image (1) I chose letter l for linux and I got the error.

2) Using OpenFirmware (key alt + command + o +f) and then 

```
>0 hda:10,yaboot 
```

I got the image (2). You can see the errors.

3) I booted the Live CD Ubuntu 7.04 again and I could make a chroot to opensuse system. Then I executed 

```
#lilo
```

And when I reboot the previous version of lilo bootloader appeard. I ran opensuse, And I got this

```
# ofpathname /dev/sda11
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:11
```

and this

```
# e2fsck -v -p -f /dev/sda11

 100834 inodes used (1.97%)
     95 non-contiguous inodes (0.1%)
        # of inodes with ind/dind/tind blocks: 4552/34/0
 689158 blocks used (6.73%)
      0 bad blocks
      1 large file

  76572 regular files
  10979 directories
    134 character device files
     26 block device files
      2 fifos
      0 links
  13112 symbolic links (12038 fast symbolic links)
      0 sockets
--------
 100825 files
```

such as you told me. It seems to be no problem with anything. I corrected lilo.conf version

```
image=/boot/vmlinux
        label=ubuntu
#        read-only
#        device=/disk@0:
#        partition=11
#        root = /dev/sda11
        root = /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS167W4-part11
        initrd=/boot/initrd.img
        append="nosplash"
```

I had to comment the line read-only, device and partition because I received this error when I executed # lilo on opensuse

```
# lilo
ERROR: !!!!!!!!!! unkown option read-only !!!!!!!!!!!!!
```

```
# lilo
ERROR: !!!!!!!!!! unkown option device !!!!!!!!!!!!!
```

Once I could run lilo successfully and I rebooted I got the image (3)

Well I am such as the beginning, with nothing; well I now know how to install opensuse in PPC how the hell opensuse for PPC use lilo and don't yaboot :)

Thank you again

---

### Post by frog_pilot on 2008-06-08
> **vlomasb said:**
> ofpathname /dev/sda11
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:11

This looks like an ofpath I like :)

This you have to add to your ubuntu yaboot.conf as
```
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
```

The mistaakes with lilo.conf came frome false syntax. I thaght it has to be thw same as for yaboot, as I thought it will also use yaboot. My fault :(


Try this first please...

//edit: the first of your attached shots suggests that your ofpath entry isnt valid...

---

### Post by vlomasb on 2008-06-08
Hi

There are excellent news but also bad news.

The excellent new is at least I could run ubuntu, since now I am writing this post with ubuntu. I did exactly that you told me. Add the line 

```
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
```

to yaboot.conf and I executed ybin -V and I got this:

```
ybin: Finding OpenFirmware device path to `/dev/sda10'...
ybin: Finding OpenFirmware device path to `/dev/sda9'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda10...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda10...
ybin: Installing /etc/yaboot.conf onto /dev/sda10...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda10 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
```

I rebooted the PPC and just MacOS boot suddenly without my decision.

Then I pressed alt key, and then in the graphical menu I clicked on Linux button and just the same graphical menu appeared. I was disappointed but I remembered the famous OpenFirmware MAC, then alt + command + o + f I typed

```
0>boot hd:10,yaboot
```

and then yaboot appeared I pressed tab key, show me Linux, old and Opensuse, I typed Linux and voila! Ubuntu ran.

Then the bad news I have to follow the previous procedure to initialize ubuntu. 

My last questions is, what have I to do for Ubuntu on PPC system works normally? 

Once again, thank you.

---

### Post by vlomasb on 2008-06-08
I forgot to say:

By the way I am too happy!

---

### Post by frog_pilot on 2008-06-10
> **vlomasb said:**
> I rebooted the PPC and just MacOS boot suddenly without my decision.

Then I pressed alt key, and then in the graphical menu I clicked on Linux button and just the same graphical menu appeared. I was disappointed but I remembered the famous OpenFirmware MAC, then alt + command + o + f I typed

```
0>boot hd:10,yaboot
```

and then yaboot appeared I pressed tab key, show me Linux, old and Opensuse, I typed Linux and voila! Ubuntu ran.

Then the bad news I have to follow the previous procedure to initialize ubuntu. 

My last questions is, what have I to do for Ubuntu on PPC system works normally? 

Once again, thank you.

Do you mean that after the graphical openfirmware menu (the one with the buttons), if you press the linux(penguin)-button there appears exactly the same graphical openfirmware menu?

There should appear the

# l - Linux
# x - OSX
# c - cdrom

menu. And the yaboot stage 2

# boot:

where you hit tab and then enter your wanted option (ubuntu).

Now, having the right openfirmware-path for your startup-disk, step back to the first attempt to fix ubuntu...

Change your ubuntu yaboot.conf with the now known device-entry. Make these changes permanent with 
# ybin
and try starting again, ignoring your new opensuse install...



> **vlomasb said:**
> My last questions is, what have I to do for Ubuntu on PPC system works normally?

Usually it works normally :lolflag: on most ppc macs the efault yaboot.conf works fine and has detected the right openfirmware path. Sometimes you have to add a kernel parameter. What went wrong on your machine is a mystery...

---

