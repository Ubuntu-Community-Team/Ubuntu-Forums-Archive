---
title: "startup fails g4 PM Yikes! 6.06"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by krucz36 on 2010-01-24
I'm sorry if this has been posted before, a couple searches didn't reveal a topic that matched. 

I grabbed the dapper drake "alternate" install ISO and burned it from my Macbook Pro to a boot disk, and went through the entire install process on my Power Mac G4 400mhz "Yikes!". After install it starts right up to the boot prompt (is that what its called?), and i generally just hit "enter". after a flash to a white screen, it comes back to a black screen and gives me a few lines of errors, the first of which reads: 
"
Can't open device </pci@80000000/pci-bridge@d/pci-ata@1/@d/disk@1:0>
/pci@80000000/pci-bridge@d/pci-ata@1/@d/disk@1:0/disk@1:3,/boot/initrd.img:unknown or corrupt filesystem
"
Sorry if it's not character for character accurate, i had to write it down. Now the drive that linux is installed on was literally formatted right then by the installer, so i'm not sure what the issue may be. I have another drive on the disk with Mac OS 9 installed that is set as the master drive, but it seemed to find the linux drive no problem. during install i was informed it would write partions #3 and #4 to the drive. 

any info or hints or castigation appreciated.

---

### Post by krucz36 on 2010-01-24
i tried an xubuntu live CD, and when I click the "install" icon, i get this: 

> Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 54, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 171, in __init__
    self.customize_installer()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 300, in customize_installer
    self.tzmap = TimezoneMap(self)
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1615, in __init__
    self.tzdb = ubiquity.tz.Database()
  File "/usr/lib/python2.4/site-packages/ubiquity/tz.py", line 182, in __init__
    self.locations.append(Location(line, iso3166))
  File "/usr/lib/python2.4/site-packages/ubiquity/tz.py", line 168, in __init__
    today = datetime.datetime.today()
ValueError: microsecond must be in 0..999999

any thoughts?

---

### Post by linuxopjemac on 2010-01-25
with your first installation it looks like you are almost there. I guess it's just a matter of manually adapting yaboot.conf to your needs. After installation take the liveCD and boot into it. Chroot into the system and give us the output ofpath /dev/yourdevice  and /etc/yaboot.cfg

to chroot into your system from the liveCD:
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash

```

Then go into the config folder of your system and show the contents of yaboot:

```
sudo cat /etc/yaboot.conf
```

and then tell me the output of the following

```
mac-fdisk /dev/hda
```

or 

```
mac-fdisk /dev/sda (this is the drive where Linux resides)
```

then I need to know the ofpath to that device where Linux is on, so e.g.:

```
sudo ofpath /dev/sda

```
or 

```
sudo ofpath /dev/hda
```

---

### Post by krucz36 on 2010-01-27
Thanks for the info linuxopjemac. 

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
```
Sadly, I got that far and it said "mount: unknown filesystem type 'ext4'

any more info much appreciated!

---

### Post by linuxopjemac on 2010-01-27
Probably sda4 is not the partition you installed Linux on. Try to first find out where you installed Linux on (the root partition , "/"). You can see it when you boot in the liveCD and go to gparted. You need to first know this before we can proceed.

---

### Post by krucz36 on 2010-02-06
Hi: In a demonstration of my n00bness, I took a while to figure out what gparted was, and it lists four drives
/dev/hdc
/dev/hdd
/dev/sda
/dev/hda

/dev/hdd is the 30GB drive I chose to install linux on with the debian installer, and would have been what I'd use for the xubuntu installer, had it not failed

that drive lists 4 partitions, "unknown", hfs, ext3, and a locked partition called linux-swap. the dev/hdd3 is 27GB, everything else is small. 

does that answer anything? Sorry about my delayed responses, I'm doing this as a side project. Thanks so much for your help!

---

### Post by linuxopjemac on 2010-02-08
the ext3 partition on that drive is Linux, if you tell me that that is the third partition, then it would be /dev/hdd3

then you have to put that info in yaboot.conf, see my posts how to chroot into your system from the liveCD, to be able to edit the yaboot.conf file.

---

### Post by krucz36 on 2010-02-09
eureka! i changed the /dev/sda4 to /dev/hdd3 and everything went as outlined. 

yaboot.conf looks like this: 
```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hdd2
device=/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@1:
partition=3
root=/dev/hdd3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash video=ofonly"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash video=ofonly"

```

I then did a few variations on the mac-fdisk command you mentioned... mac-fdisk /dev/sda hda hdd3 etc. I got a "Command" command line, and typed ? then p and they all gave me "No partition map exists" as a result

finally "sudo ofpath /dev/sda" gave me 
```
/pci@80000000/pci-bridge@d/pci9004,7850@3/@6:
```

that's what i managed to do. thanks for bearing with me. i haven't felt this newblike since 94

---

### Post by krucz36 on 2010-02-09
I must have had some kind of typo on the mac-fdisk command, because I went back and tried it again and it worked: 
```
root@ubuntu:/# mac-fdisk /dev/hda
/dev/hda
Command (? for help): p
/dev/hda
        #                    type name                length   base    ( size )  system
/dev/hda1     Apple_partition_map Apple                    2 @ 1       (  1.0k)  Partition map
/dev/hda2               Apple_HFS Xubuntu 6.06 ppc   1420304 @ 16      (693.5M)  HFS

Block size=512, Number of Blocks=1420320
DeviceType=0x1, DeviceId=0x1

```

when i pay attention things work...

---

### Post by krucz36 on 2010-02-12
well i tried editing yaboot.conf last night to no avail...couldn't get it to boot from the HDD, just the live CD again

---

### Post by krucz36 on 2010-02-14
another day of fidgeting with yaboot.conf, another day of linux hating me.
some day i will win!

---

### Post by linuxopjemac on 2010-02-14
> boot=/dev/hdd2
device=/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@1:
partition=3
root=/dev/hdd3

then you did

> finally "sudo ofpath /dev/sda" gave me
Code:

/pci@80000000/pci-bridge@d/pci9004,7850@3/@6:


If you tell me that the bootstrap partition is /dev/hdd2 then you issue:

```
ofpath /dev/hdd
```

to find the correct device and put that as "device" in the yaboot.conf
then 

```
sudo ybin -v
``` 

and reboot

Tell me if you end up in yaboot at all if things don't work out.

---

### Post by linuxopjemac on 2010-02-14
I give you my setup, it will help you understand...
```

sudo mac-fdisk /dev/hda
```

```
Command (? for help): p   
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           37345704 @ 2018     ( 17.8G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1722358 @ 37347722 (841.0M)  Linux swap

Block size=512, Number of Blocks=39070080
DeviceType=0x0, DeviceId=0x0

```

```
khanitta@debian:~$ cat /etc/yaboot.conf 
## yaboot.conf generated by debian-installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img

image=/boot/vmlinux-2.6.18
	label=linux-2.6.18
	initrd=/boot/initrd.img-2.6.18

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
khanitta@debian:~$ 

```

```
khanitta@debian:~$ sudo ofpath /dev/hda
/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
```

---

### Post by krucz36 on 2010-02-15
after going through everything, running ```
sudo ybin -v
```
gives me the message
```
ybin: Finding OpenFirmware device path to '/dev/hdd2'...
Failed to initialize HFS working directories: No such file or directory
ybin: /dev/hdd2 appears to have never had a bootstrap installed, please run mkofboot
```
But I ran the debian installer. 

thanks for all the help so far, it's been illuminating.

---

### Post by krucz36 on 2010-02-15
comparing the mac-fdisk results they're basically identical, except my computer is /dev/hdd instead of dev/hda

---

### Post by linuxopjemac on 2010-02-16
can you give me the output of mac-fdisk please ? I don't think you have a HFS partition there as bootstrap...

mine looks like this

```
   Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           37345704 @ 2018     ( 17.8G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1722358 @ 37347722 (841.0M)  Linux swap
```

where /dev/hda2 is the bootstrap partition

---

### Post by linuxopjemac on 2010-02-16
I think, that if you have a HFS partition there, you can simply do

```
sudo mkofboot -v
```

followed by

```
sudo ybin -v
```

for detailed information:
[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml)

---

### Post by krucz36 on 2010-02-16
this is what i get with ```
mac-fdisk /dev/hdd
```

```
        #                    type name                 length   base     ( size )  system
/dev/hdd1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hdd2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hdd3         Apple_UNIX_SVR2 untitled           57521485 @ 2018     ( 27.4G)  Linux native
/dev/hdd4         Apple_UNIX_SVR2 swap                2506929 @ 57523503 (  1.2G)  Linux swap

Block size=512, Number of Blocks=60030432
DeviceType=0x0, DeviceId=0x0


```

when i ran mkofboot -v it returned 
```
Failed to initialize HFS working directories: No such file or directory
mkofboot: HFS filesystem creation failed!
```

---

### Post by krucz36 on 2010-02-16
by the way: THANK YOU FOR ALL YOUR HELP!

---

### Post by linuxopjemac on 2010-02-17
This is really strange. Since ybin is a shell script, you can 
try to run it with "sudo sh -x ybin" to see where the error occurs.

Do you have hfsutils in the live environent ?

If I were you, I would try to do the same things with a Debian Lenny live CD, instead of a 6.06 Ubuntu CD. I am pretty sure that the problem lies in some missing proram (hfsutils) on the Ubuntu installer.

---

### Post by krucz36 on 2010-02-18
thanks, i'll get that downloading.

---

### Post by Ken147 on 2010-02-18
Strangely I had the same problem when i was going to install Ubuntu 6.10 onto my power mac G3, but I had no problem installing it on to my G4 Sawtooth (next one up from the Yikes!)

---

### Post by krucz36 on 2010-02-20
hey all: i finally got it working. i used the net install version of debian 5.0.4, and after a failed install that hung up while retrieving files, then another that would boot to the mac os system folder icon and just stop, i took a close look at the HD. it was set up with jumpers set in "slave" mode. i switched it over to "master" (after launching the little jumper thing across the room and having to search for it) and it installed and worked like a charm. i'm posting this message on it now. 
it's not ubuntu, but it's linux. i'm going to go back and try the ubuntu install as well. THANK YOU for all the help so far. this is a great forum.

---

### Post by linuxopjemac on 2010-02-21
I am very happy for you :)

---

