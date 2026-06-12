---
title: "[SOLVED] how to manually mount new SATA drives"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-01-07
#1:  I have successfully installed 7.04 64-bit, dual boot with XP, and am a new user.  I posted earlier about 2 SATA drives that were added after the install.  I can't access them and don't know enough to do it (yet).  I got this response:

> I'm not sure what the actual problem is, you can't access partitions on your local machine? If they were there at install, they should be audio discovered, and seen in 'Computer' (If using gnome). If they are not, you have to find the dev location and mount it manually.

These will generally be in the form of sdaX where x is the partition number, starting at 1, and a is the alphabet corresponding to drive dominance, ie sda sdb.

Then you're looking at some reading:
man mount

You're looking to make a directory, then mount the /dev/sd* as ntfs.

Now, I'm sure that this is useful but it isn't exactly :absolute beginner: speak.  I understand that /hda and /hdb are the IDE drives.  They are OK. I know the command to make a directory, but don't know where to do it.  And where to look to find the dev location?  I'm a beginner.

Can someone please "walk" me through this?  I've done as much homework as I can and am still not comfortable.  I learn quickly but have no one at my shoulder other than the forum.

#2:  Same installation.  Sound does not work.  Can you point me in the right direction to configure (onboard) sound?  It worked in the Live CD but won't after install.  I downloaded 225MB of updates and installed them already today.

Thanks for your patience all.

---

### Post by kpkeerthi on 2008-01-07
To check if they have been detected by ubuntu, open a terminal and post the output of 
```

sudo fdisk -l

```

Are these "new" drives? Have they been formatted? What filesystem?

---

### Post by kpkeerthi on 2008-01-07
> 
#2: Same installation. Sound does not work. Can you point me in the right direction to configure (onboard) sound? It worked in the Live CD but won't after install. I downloaded 225MB of updates and installed them already today.


Open a terminal and type 
```
alsamixer
```
Make sure the sliders are raised enough, especially PCM. Also look for controls marked 'MM'. They may be muted. Press 'm' key to unmute and check if sound works. You should use <tab> key to navigate across the controls. When done press 'Esc'.

---

### Post by ThunderRd on 2008-01-07
> **kpkeerthi said:**
> To check if they have been detected by ubuntu, open a terminal and post the output of 
```

sudo fdisk -l

```

Are these "new" drives? Have they been formatted? What filesystem?

Thanks for answering kp.  Output of  fdisk shows only the IDE drives:

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/hda2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris
```

One SATA is a brand new drive, unpartitioned, and the other is a single NTFS partition with data.

Re sound:
Output of alsamixer says: "function snd_ctl_open failed for default: no such device"

---

### Post by hyper_ch on 2008-01-07
Install gparted

```

sudo apt-get install gparted

```

and run it then. With it you can parttion /dev/hdb then.

Once partitioned (and formated) you can mount it through the shell with the mount command.

(1) create a folder where you want to mount it do e.g.:
```

sudo mkdir /media/new_drive

```

(2) mount the drive:
```

sudo mount /dev/hdb1 /media/new_drive

```
it's hdb1 if you make just one huge ext1 primary partition, otherwise adjust it to hdbX

(3) chown it so you can use it
```

sudo chown USERNAME.USERNAME /media/new_drive

```
USERNAME is your actual username.

---

### Post by ThunderRd on 2008-01-07
I don't know a lot, but I don't think that is correct.  What you are telling me to do is to re-partition hdb.  Why would I do that?  It's my Linux system.

I don't want to do anything to either of the drives in the fdisk output.  They are IDE primary master and slave.  I'm talking about 2 SATA drives, one new, and one with existing data.  Presumably they would be /sda and /sdb, I think.  Please note the title of the thread.  Neither if them show up in fdisk.  Now, if you can tell me why, you'd be helping me.

If I do what you tell me to do I will bork the whole Ubuntu install.

---

### Post by The Cog on 2008-01-07
It's worrying that they don't show up on fdisk. 

Are they motherboard controllers or are they on a separate controller card? 

Do you run Windows and if so, can that see them? 

can you port the out[ut of the command **lspci**

---

### Post by hyper_ch on 2008-01-07
it's not my day today....

hmmm.... yes.... it's not showing...

Upon boot process, does it show the SATA drive?

---

### Post by ThunderRd on 2008-01-07
> **The Cog said:**
> It's worrying that they don't show up on fdisk. 

Are they motherboard controllers or are they on a separate controller card? 

Do you run Windows and if so, can that see them? 

can you port the output of the command **lspci**

Sure:
```
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 3372
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

They are on the VIA SATA motherboard contrroller, ASROCK 4coredual-sata2.  And yes, they show up fine in XP, I use one of them all the time, and the other shows in disk manager as unallocated space.

Please note the last line of the output: I can't get this audio device working either.  No sound, although it worked from the Live CD.

@hyper_ch: If you are talking about the BIOS screen, then, yes, both drives show up when booting.  That is why I can use them in Windows.

---

### Post by The Cog on 2008-01-07
Hmm. I guess Linux is missing the drivers then, but I'm getting out of my depth. That applies to both sound and disks. Maybe something in windows might help to prove that the problems are the two unknown devices in the pci list.

Hopefully someone more hardware savvy will be able to chip in.

---

### Post by ThunderRd on 2008-01-07
This is a long post.  Thanks for your time.

I found Linux drivers on the Realtek site for codec ALC888 which is the one I have.  I read with interest this thread in which a user was trying to install the same driver set:
[http://ohioloco.ubuntuforums.org/showthread.php?t=652054](http://ohioloco.ubuntuforums.org/showthread.php?t=652054)

Here is some terminal output when an application is launched with an associated sound file:
```
~~~~~~~@Q6600:~$ sudo gedit
Password:
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

```

I am not sure if this helps anyone, but sure ain't working.

I have unpacked the driver.  Here is the readme:```
Installation:
This Source Code is from www.alsa-project.org.
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
```

Here is the install file:```
#!/bin/sh

######## VERSION 1.0 ########

KERNEL_VER=`uname -r`

. ./version

echo ".....Decompress Driver source v1.0.15rc3-$ver"
tar xvpfj alsa-driver-rt20071002.tar.bz2 > /dev/null 2>&1
echo ".....Decompress ALSA Library source v1.0.14"
tar xvpfj alsa-lib-1.0.14.tar.bz2 > /dev/null 2>&1
echo ".....Decompress ALSA Utility v1.0.14"
tar xvpfj alsa-utils-1.0.14.tar.bz2 >/dev/null 2>&1
#echo ".....Decompress XRealMixer v0.5"
#tar xvpfj xrmix-0.5.tar.bz2 > /dev/null 2>&1
sync

echo "Remove old sound driver"
if [ -d /lib/modules/$KERNEL_VER/kernel/sound ]; then
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/pci > /dev/null 2>&1
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/acore > /dev/null 2>&1
fi

## remove driver modules
if [ -f /etc/rc.d/init.d/alsasound ]; then
   /etc/init.d/alsasound stop
   rmmod snd-page-alloc > /dev/null 2>&1 
   rmmod soundcore > /dev/null 2>&1
fi

sleep 2

echo "Compile Driver........"
cd alsa-driver-rt20071002
./configure --with-cards=hda-intel 
make
make install
./snddevices
cd ..

## for x86
echo "Remove old alsa library"
rm -rf /lib/libasound.* > /dev/null 2>&1 
rm -rf /lib64/libasound.* > /dev/null 2>&1 
rm -rf /usr/lib/libasound.* > /dev/null 2>&1 
rm -rf /usr/lib64/libasound.* > /dev/null 2>&1

echo "Compile ALSA Library....."
cd alsa-lib-1.0.14
./configure
make
make install
cd ..

echo "Compile ALSA Utility......"
cd alsa-utils-1.0.14
./configure
make
make install
cd ..

#echo "Comiple XrealMixer......"
#cd ./

## for x86_64
if [ -d /usr/lib64 ]; then
  cp -lf /usr/lib/libasound.* /usr/lib64
  cp -lf /usr/lib/pkgconfig/alsa.pc /usr/lib64/pkgconfig
  ldconfig -n /usr/lib64
fi

sleep 1

## del audio stat file
if [ -f /etc/asound.state ]; then
   rm -rf /etc/asound.state > /dev/null 2>&1
fi

## alsa driver sndstat file relink
rm -rf /dev/sndstat > /dev/null 2>&1
ln -s /proc/asound/oss/sndstat /dev/sndstat

## sample wave
if [ -d /usr/share/sounds/alsa ]; then
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav
else
     mkdir /usr/share/sounds/alsa
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav
fi

echo "Remove Folder....."
rm -rf alsa-driver-rt20071002 > /dev/null
rm -rf alsa-lib-1.0.14 > /dev/null
rm -rf alsa-utils-1.0.14 > /dev/null
alsaconf
```

I tried the "automatic" installation from the directory with: sudo ./install
This produced an error:```
.: 7: Can't open ./version
```

Here are the contents of /version:
```
#!/bin/sh
ver=4.07a
```

If there is someone who can interpret this info please let me know.  Perhaps it will give a clue as to the disk problem as well.

EDIT:
After removing this line of code from the install file-```
 . ./version 
``` it produced this output:
```

thunderrd@Q6600:~$ '/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install' 
.....Decompress Driver source v1.0.15rc3-
.....Decompress ALSA Library source v1.0.14
.....Decompress ALSA Utility v1.0.14
Remove old sound driver
Compile Driver........
cd: 35: can't cd to alsa-driver-rt20071002
/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install: 36: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install: 39: ./snddevices: not found
Remove old alsa library
Compile ALSA Library.....
cd: 50: can't cd to alsa-lib-1.0.14
/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install: 51: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
cd: 57: can't cd to alsa-utils-1.0.14
/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install: 58: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
cp: cannot stat `/usr/lib/pkgconfig/alsa.pc': No such file or directory
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
bzip2: Can't open input file test.wav: No such file or directory.
Remove Folder.....
/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a/install: 100: alsaconf: not found

```

---

### Post by rkd on 2008-01-07
I just started looking at this thread. A couple of things occur to me right away:

The problems you have trying to run the install for the alsa driver might be caused because you did not change to the directory of the alsa driver install files before trying to run them. That's the usual way to do it. The code assumes it and can often not work in strange ways if you don't do it.  So I think it would be worthwhile trying that again after using 
```
cd '/home/thunderrd/Desktop/_linux drivers and stuff/realtek-linux-audiopack-4.07a'
```
to set the directory there.

A second thing about that is that I've sometimes seen warnings not to use spaces in directory names, because sometimes programmers forget to use quotes around file names in their scripts. So if you would rename that '_linux drivers and stuff' directory to something without any spaces, it might help, too.

You mentioned that the sound worked when you booted from the live CD, but doesn't work now after installing to the hard disk and doing all the updates. Did you check the sound after installing to the hard disk but before doing any updates? It might help us focus on the problem if we knew whether the problem was caused by one of the updates or not.

Were the SATA disks recognized when you had booted from the live CD? If you did not try that, I think it would be helpful to boot from the live CD now and check that. Same point as in my previous paragraph -- it would help me to know whether the updates caused the problem.  If they are recognized when running from the live CD, it might be helpful to see the lspci output and the fdisk -l output at that time. Come to think of it, the lspci output when running from the live CD would be interesting to see what it says about the sound controller, too.

I'll try to study this thread some more later and see whether I can spot any clues I didn't see at first glance.

---

### Post by ThunderRd on 2008-01-07
> ...you did not change to the directory of the alsa driver install files...rename that '_linux drivers and stuff' directory to something without any spaces...

Thanks, rkd, I'll try that.  Of course I thought that /install would run as long as I used the correct path to it; I will keep in mind in the future to actually be in the directory before running it.  Actually, the way I did it was to open terminal and drag the install file into it.  I'll also rename that directory.

> Did you check the sound after installing to the hard disk but before doing any updates?
Frankly, I can't remember but I don't think it worked then either.  Not sure, TBH.

> Were the SATA disks recognized when you had booted from the live CD?
At that time they weren't in the machine as yet; I will boot from the cd and check.

> it might be helpful to see the lspci output and the fdisk -l output at that time.
Will do.  Incidentally, there's no problem if you want me to reinstall; as long as it's on a seperate drive from windows I have no objection.

I won't be able to do any of this until later; please keep an eye out for my posting, and thank you.

---

### Post by rkd on 2008-01-07
You are completely correct that the command runs when you type the full path to it. The problem is that most people write their install script assuming that the working directory has been set to the directory into which you unpacked all the files. Typing the full path name doesn't change the working directory. So the command runs, but can't find the other files it is looking for. (Just thought you'd like to understand that nuance.)

We don't need to think about a reinstall just yet. Maybe later if nothing else works.

---

### Post by ThunderRd on 2008-01-08
Well, I'm not sure about this.  I booted from the Live cd and the audio didn't work.  I'm absolutely sure that it did before; I remember playing around with the sound when I first tried the CD.

I went back to windows to check the hardware and it runs fine.  All audio devices are working.

I know I'm not crazy, but something is different.

The SATA drives do not show up on the Live CD, output from fdisk is same as before.  Here is lspci:```
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge

00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge

00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge

00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge

00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller

00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge

00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller

00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)

00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 3372

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

I did what you said with the driver installation.  It did run, but it appears there were still errors.  
```
thunderrd@Q6600:~$ cd /home/thunderrd/Desktop/_linux_drivers/realtek-linux-audiopack-4.07a
thunderrd@Q6600:~/Desktop/_linux_drivers/realtek-linux-audiopack

-4.07a$ ./install

.....Decompress Driver source v1.0.15rc3-4.07a

.....Decompress ALSA Library source v1.0.14

.....Decompress ALSA Utility v1.0.14

Remove old sound driver

Compile Driver........

checking for gcc... gcc

checking for C compiler default output file name... 

configure: error: C compiler cannot create executables

See `config.log' for more details.

make all-deps

make[1]: Entering directory `/home/thunderrd/Desktop/_linux_drivers/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002'

make[1]: Nothing to be done for `all-deps'.

make[1]: Leaving directory `/home/thunderrd/Desktop/_linux_drivers/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002'


Please, run the configure script as first...


if [ -L /include/sound ]; then \

                rm -f /include/sound; \

                ln -sf /home/thunderrd/Desktop/_linux_drivers/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002/include/sound /include/sound; \

        else \

                rm -rf /include/sound; \

                install -d -m 755 -g root -o root /include/sound; \

                for f in include/sound/*.h; do \

                        install -m 644 -g root -o root $f /include/sound; \

                done \

        fi

install: cannot create directory `/include': Permission denied

install: cannot stat `include/sound/*.h': No such file or directory

make: *** [install-headers] Error 1

./install: 39: ./snddevices: not found

Remove old alsa library

Compile ALSA Library.....

checking build system type... x86_64-unknown-linux-gnu

checking host system type... x86_64-unknown-linux-gnu

checking target system type... x86_64-unknown-linux-gnu

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for gawk... no

checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking for gcc... gcc

checking for C compiler default output file name... configure: error: C compiler cannot create executables

See `config.log' for more details.

make: *** No targets specified and no makefile found.  Stop.

make: *** No rule to make target `install'.  Stop.

Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for gawk... no
checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking whether NLS is requested... yes

checking for msgfmt... no

checking for gmsgfmt... :

checking for xgettext... no

checking for msgmerge... no

checking for style of include used by make... GNU

checking for gcc... gcc

checking for C compiler default output file name... configure: error: C compiler cannot create executables

See `config.log' for more details.

make: *** No targets specified and no makefile found.  Stop.

make: *** No rule to make target `install'.  Stop.

cp: cannot stat `/usr/lib/pkgconfig/alsa.pc': No such file or directory

ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists

bzip2: Output file test.wav already exists.

cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied

bzip2: Output file test.wav.bz2 already exists.

Remove Folder.....

./install: 100: alsaconf: not found

```

---

### Post by rkd on 2008-01-08
Actually, it makes more sense that the sound doesn't work from the live CD, either. It is the same Ubuntu OS, so it should work the same whether from the live CD or from the hard disk after installing from the live CD. I can't explain why you believe you had the sound working when running the live CD, though.

Buried in the output from the install of the ALSA software is a report of something about the C compiler not working:
```
configure: error: C compiler cannot create executables
See `config.log' for more details.
```
If you look in /home/thunderrd/Desktop/_linux_drivers/realtek-linux-audiopack-4.07a (the directory where you were doing the build), I think you'll find the file named config.log. Post the contents of that file. If it is extremely long, attach the file to the post rather than pasting its contents into the body of the post. It ought to tell us more about what went wrong. I hope from that it will be clear what needs to be done to fix the install problem.

I think the problem with the SATA disks is that the SATA controller on your motherboard isn't yet supported in the stock Ubuntu (not even in 7.10, apparently). But VIA has the module file needed for 7.04 available on their web site. I downloaded it and looked at the installation instructions, and they seem pretty simple. Part of the instructions are to mount a disk image file with loopback and run a script from it. I wanted to look at the script, but mount complains about the attempt to mount the disk image file. I'll have to figure out what is wrong with that. I'll post again when I've got that solved and am sure I understand how the installation is supposed to work. Then you can try it. 

You are still using 7.04, right? Those updates you mentioned doing in the first post weren't to upgrade to 7.10, were they?

---

### Post by ThunderRd on 2008-01-08
```
...you'll find the file named config.log. Post the contents of that file.
```
The file's not there.  Am trying to find it elsewhere.  Any suggestions?

```

I'll post again when I've got that solved [the SATA install routine] and am sure I understand how the installation is supposed to work. Then you can try it.
```
OK, I'll be here when you know what to do.  My chipset is PT880 Ultra, southbridge is VT8237S.  I believe this is the file for my chipset: via_ubuntu7.04(x86&x86_64)_sata&ahci_patch_kernel_2-6-x_v1.30_appnote_ver0.8.tar.gz
If that is the one you're talking about, I have it downloaded already but will do nothing with it until you say so.

```

You are still using 7.04, right? Those updates you mentioned doing in the first post weren't to upgrade to 7.10, were they?
```
I think so.  After I installed, a notification appeared in the tray telling me to get the latest versions of some software.  I downloaded it overnight and in the morning I had a message that all had been installed correctly.  I believe it was simply updates to 7.04.  What can I check to make sure?

Thanks so much for your attention.  I'll learn how to do this stuff myself eventually...but I have to start somewhere, ;)

-TR

---

### Post by rkd on 2008-01-08
A way to look for files is with the find command. Try this:
```
sudo find /home -name config.log
```
That will look in /home and all directories under /home for a file matching "config.log" and print the full pathname. I suggest using sudo so that it is not blocked from looking in some directories due to the permissions. If you don't find config.log under /home, you could try looking everywhere  by changing /home to just / -- that will run longer, though.

One way to find the version of your system is to go to the System menu, choose About Ubuntu, then on the page that displays, the second paragraph mentions the version. Upgrading to a new version is a big deal and you wouldn't have done it by accident. I just didn't know whether you did it intentionally.

You're welcome -- learning by doing works well for many people, and I like to teach informally.

---

### Post by ThunderRd on 2008-01-08
Both searches yielded nothing.  They were finished almost instantaneously.  There's next to nothing in the /home subdirectories anyhow.  I'm pretty sure that it's cleaning up a temp directory after itself...what if I comment out all the rm commands in the install file?  Maybe the directories would remain after the failed install, like this:
```

echo "Remove Folder....."
## rm -rf alsa-driver-rt20071002 > /dev/null
## rm -rf alsa-lib-1.0.14 > /dev/null
## rm -rf alsa-utils-1.0.14 > /dev/null
alsaconf
```

Please note the edit to my previous post re: the SATA drivers from VIA

Still v7.04, as I thought.

---

### Post by ThunderRd on 2008-01-08
OK, done.  I commented out the final cleanup commands and have 3 config.log files attached here.  Note the pathnames for the locations of the files.

Hmm.  I have the files but the forum won't allow me to attach them, says they are invalid.  I can email them if you PM me.  They are fairly long to post.

---

### Post by ThunderRd on 2008-01-08
Never mind, I just had to convert them to another format.  Here they are:

I'll save the rest of the contents of those 3 directories in case you have to see something else.

---

### Post by rkd on 2008-01-09
That's a pretty dumb install script that purges the files that contain the error report, isn't it? Well, you were on top of things and figured it out. Good work!

The log files actually don't tell much more about the error (all three report the same thing). The first part of most installations is the configure part, that checks the environment, which versions of programs are available, and other things. This installation's configure test compiles a simple C program and checks to see whether it produced an object file. It didn't -- a serious problem when you are about to compile a bunch of code! 

The log file does have one bit of additional information: It lists what it claims is the test program, and it is, indeed, very simple. Just a main function with a return statment. You can see it in the log file if you want to look for it.

But it doesn't tell us why the C compiler didn't create an object file.  Maybe the compiler didn't get installed correctly or was mangled by those updates, or something else.

So one thing I'd like you to do is copy the following lines into a text file, call it main.c:
```
int main() {
;
return 0;}
```
Then enter the command:
```
gcc main.c
```
Look to see whether it displays any error messages, and do ls to see whether in created a file a.out.

I tried to look into the .configure script to see exactly how it runs the compiler, especially what options it sends, because that could make the difference, but the script is too complicated for me to figure out very quickly.

The only thing I can think of to do to try to fix the problem is to remove and reinstall stuff connected with building software. The problem with that is that I don't know very much about managing packages beyond apt-get install, so I'm treading on somewhat dangerous ground. I believe what I suggest won't destroy your system, but I don't know for sure. I don't know what things building the sound driver requires, so I'm guessing at that, too. If you had some instructions about what packages to install before trying to build the driver, maybe we can adjust the set of packages we fiddle with here.

When you do these commands, do them one at a time and copy and paste the command and its output into an editor window as you go (save the file after each addition to it). That way we'll be able to go back and look at everything if we need to study it afterward.

```
sudo apt-get autoremove build-essential
sudo apt-get autoremove gcc
sudo apt-get autoremove linux-headers-`uname -r`
sudo apt-get autoclean

sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get linux-headers-`uname -r`

```
Assuming you get through all of this, try building the sound driver again. I remember at one point, you removed a command ./version because it couldn't find the file. If you haven't put that command back in, please do so. It could be important.

Okay, now to the SATA driver. This looks much simpler. You already downloaded the file. First thing to do is expand it:
```
tar xvzf via_ubuntu7.04(x86&x86_64)_sata&ahci_patch_kernel_ 2-6-x_v1.30_appnote_ver0.8.tar.gz
```
The readme.pdf has the installation instructions I've copied here. Then we make a directory and mount the disk image on it:
```
mkdir x
sudo mount -o loop ubuntu7.04_DD.img x
```
Then we switch into that disk image and run the install:
```
cd x
sudo ./sata_ahci_ubuntu7.04_install

```
If everything went right, the SATA disks should be working at this point. I don't believe you need to boot.

---

### Post by ThunderRd on 2008-01-09
OK, I made the text file and ran the command from the same directory:
```
thunderrd@Q6600:~$ dir
Desktop  Documents  Examples  main.c  Music  Pictures  wallpapers
thunderrd@Q6600:~$ gcc main.c
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
```

I don't know if that is what you're looking for, but that's what I got.

Next:  I followed your instructions for the SATA drives, and bingo:
```

thunderrd@Q6600:~/Desktop/_linux_drivers/sata_drivers/sata$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/hda2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      310096   156288352+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```


As you can see, one drive is partitioned and the other one isn't.  So we made some progress.  Now I'll wait until you tell me what to do about the other thing.

Good job and thanks.  You are very succinct and explain things well and in an organized fashion. :)  Remember that if this sound thing gets too complex it may be easier to install again, if you think it's the right thing to do.  Then I'd leave the drives in the machine to auto-detect; so I wouldn't have the SATA problem again.

---

### Post by rkd on 2008-01-09
Okay, it looks like the SATA drives are recognized okay now. Is there more you want to do with them that you need help with?

The compiler error you saw looks the same as what the installation log file showed. Something definitely is wrong with the compiler or something it depends on. I think you should try the remove and install steps I listed, unless you think the set of packages should be modified in any way, perhaps based on what you may have installed prior to trying to install the sound driver the first time.

---

### Post by ThunderRd on 2008-01-09
OK, will try later when I have time.  Will post back.  I did some reading on "gcc"; I see what you had me do.  You wrote some code and gcc was to compile it to an executable. It didn't compile, so the compiler is broken.  Build-essential and Linux-header contain the components needed to assemble and install the compiler, so you want me to remove the broken one and try to reinstall it.  Is that correct?

I don't need to do anything with the drives anymore.  As long as I can see them I'm ok.

EDIT:
Ok, I have completed your instructions.  All of the commands worked properly except for the last one, sudo apt-get linu-headers-`uname -r`, which produced an error.

In spite of the error I tried the routine you asked me to do and a.out was compiled.  I have attached a zip file with the log of the apt-get commands, a copy of a.out, and output of the attempted audio driver installation which I tried afterwards.  There were some errors there as well, but it looked promising.

---

### Post by rkd on 2008-01-11
Sorry, I made a mistake in the last command for reinstalling the packages that might be needed for the build. I left out the word "install" from that command. Oops.

I don't understand why it couldn't get several packages during the install of build-essential, saying it could not resolve 'th.archive.ubuntu.com'. I just tried it and it went without problems on my system, though I notice my system is using us.archive.ubuntu.com rather than th.archive.ubuntu.com. Could there be a difference between those two locations? I hope it was just a temporary problem and when you run it again, it will work okay.

I see that after those errors, one of the messages suggests that apt-get update might be advisable. Oops again. I should have included that.

The build of the ALSA stuff seems to have gone much better than before, though still not perfect. One error is that it couldn't find version.h and suggests installing the full kernel sources. I think that was caused by the failure to install linux-headers-`uname -r`, so I'm not going to install the full kernel sources unless we still get that error on the next build.

I'm concerned that "make all-deps" said there was nothing to do. Maybe the problem is that there was stuff left over from the previous build attempt (because we removed the rm commands so we could look at the log files). I think you should remove the directory you created by running tar to extract from the file you downloaded, do the extraction again, move into that directory, and run the install.

Some of the errors the install got indicate that it needs to be run as root. I think you can do that by the command "sudo ./install" (without the quotes, of course) instead of just ./install. I think a lot of build and install instructions have not been updated to take into account distributions such as Ubuntu that strongly recommend never logging in as root  -- the instructions expect that when someone is installing software, they naturally will be logged in as root and so they don't mention it.

Okay, here are my revised recommendations. 

Delete the directory you made using tar from the downloaded file. Do the tar again. Then:
```
sudo apt-get update
sudo apt-get autoremove build-essential gcc linux-headers-`uname -r`
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install linux-headers-`uname -r`

cd to the directory you made from the ALSA tar file

sudo ./install
```
It probably isn't necessary to do the apt-get update twice, but I'm not very clear on these things, and I'm sure it can't hurt.

I hope I didn't mess up any of the commands this time.

---

### Post by ThunderRd on 2008-01-12
OK, I went ahead and followed your plan to reinstall gcc and linux-headers; I saved the output.  I could not find any obvious errors.

Then I ran ./install;  this was interesting.  It certainly got farther than it had before, but it wasn't perfect yet.  I studied the output and I saw the same permissions errors that you were talking about before.  Also, at the end of the routine it complained about a missing lcurse package.  In spite of this, I was able to get the mp3 player to work; it seemed ok.  However, the system sounds did not work.

I thought that was strange.

 I reached out to the repos and installed ncurse-dev, which went ok.  After that, I ran sudo ./install again.  The errors at the end went away, but the permissions errors remained even though I used sudo...and the system sounds still didn't work.  Interestingly enough, in system-prefs-sound, the test sounds work on the devices page, but on the sounds page nothing will play.  

I thought about the permissions errors.  They remained even after using sudo- to install, so I tried the ./install from a root terminal.  This eliminated all of the errors, afaik, but the system sounds still don't function.  It's not particularly important to me but it does show that something isn't quite right yet.

I have attached the output of the first instructions you gave me along with a file that is the output of the driver install from root terminal.  Things are looking up; thanks.

---

### Post by rkd on 2008-01-12
You are right that the build looks pretty good. The fact that some sound is being generated is very encouraging. 

I don't understand your experience with getting permission errors during the driver install until you did it when logged in as root rather than with sudo. Trying it as root was a good idea. I just don't know why that was necessary to eliminate the permission errors. There is a lot I don't know yet.

I did notice a few things to wonder about in looking through the two files you sent.  

In the output from both apt-get update commands, there is an error about how it failed to fetch packages.gz from the feisty-updates/universe repository. That seems like something to be concerned about, but I don't know enough to say for sure that it is a problem.

I notice that you used us.archive.ubuntu.com this time rather than th.archive.ubuntu.com, as you did earlier. Did you make that change deliberately, or did it happen on its own?

In the driver install, I notice three errors in the last 40 or so lines: two complaints that t-ja.gmo doesn't exists, and at the very end, that alsaconf was not found. I don't know how serious those are.

Also, I saw more than 50 messages from make saying "Nothing to be done for xxxxx". Many of the xxxxxx names were "install-xxxxxx", and not doing installs seems worrisome. Perhaps those messages are normal. Maybe in your configuration, there really was nothing that should have been done for those steps. I just don't know.

One thing that can cause make to decide that there is nothing to be done is if you do a build in a directory that has results left over from a previous build. You ran the driver install several times. Did you make sure that nothing was left over in the realtek-linux-audiopack-4.07a directory from the prior attempts?

One of the things I've seen suggested in other threads about sound problems it to check the mixer to be sure all relevant channels are not muted and have the levels set appropriately. And I've seen advice to check OSS, too, whatever that is. If you've already looked at those things, good. If not, perhaps you should do that. If you don't know how to do it or what it means, I'll try to help you (but I don't completely understand it myself). I also notice that on my computer, most of the system sounds are, by default, set to "no sound". Did you check that on your computer? 

I probably should have asked this question long before now: In threads where people are asking about how to build some program from the source distribution, frequently someone will tell them they should install the already-built package from the repositories. Have you already tried that? I don't remember that being asked in this thread.  There are times when it is necessary to build from source -- usually when the version in the repository is not as new as it needs to be to support your hardware, or there is no such package in the repository. Are either of those situations the case here?

---

### Post by ThunderRd on 2008-01-12
> **rkd said:**
> 
I don't understand your experience with getting permission errors during the driver install until you did it when logged in as root rather than with sudo.
Heh, me neither.  It just seemed like a good idea at the time.  Is it possible that some functions can't be executed with sudo?  I was thinking about your prior comment regarding devs and how they sometimes assume things.

> 
In the output from both apt-get update commands, there is an error about how it failed to fetch packages.gz from the feisty-updates/universe repository.
Don't know about this.

> 
I notice that you used us.archive.ubuntu.com this time rather than th.archive.ubuntu.com, as you did earlier. Did you make that change deliberately, or did it happen on its own?
I think what happened here is this:  the first time I ran commands you gave me I wasn't aware that I had to have an active connection.  So when it attempted to reach th.archive.ubuntu (the Thailand archive, where I live, made the default at install when I chose my region) it failed until I got the connection running.  Now, I believe that it went to the next choice in the file that contains the source addresses.

> 
In the driver install, I notice three errors in the last 40 or so lines: two complaints that t-ja.gmo doesn't exists, and at the very end, that alsaconf was not found. I don't know how serious those are.
Can't say anything here either.

> Also, I saw more than 50 messages from make saying "Nothing to be done for xxxxx"...
One thing that can cause make to decide that there is nothing to be done is if you do a build in a directory that has results left over from a previous build.
I think this is exactly what happened.  I don't believe there is any reason to delete the directory I un-tarred the package to.  I checked; the installation didn't put anything there.  It seems to have put everything in other locations, so I assumed that by running the install again it would overwrite previous attempts.  It seems that linux is smart enough to know that something has already been done, and so it tells you.

> 
One of the things I've seen suggested in other threads about sound problems it to check the mixer to be sure all relevant channels are not muted and have the levels set appropriately. And I've seen advice to check OSS, too, whatever that is. If you've already looked at those things, good. If not, perhaps you should do that. If you don't know how to do it or what it means, I'll try to help you (but I don't completely understand it myself). I also notice that on my computer, most of the system sounds are, by default, set to "no sound". Did you check that on your computer? 
I have checked the obvious things.  OSS I don't know about.  Will RTM. Yes, all sounds except login and out are set to no sound.  But when I set one of them, it won't play.

> 
I probably should have asked this question long before now: In threads where people are asking about how to build some program from the source distribution, frequently someone will tell them they should install the already-built package from the repositories. Have you already tried that? I don't remember that being asked in this thread.  There are times when it is necessary to build from source -- usually when the version in the repository is not as new as it needs to be to support your hardware, or there is no such package in the repository. Are either of those situations the case here?
Can you explain this a bit?  I'm not fully understanding you.  Are you saying that there are already prepared files that don't require all of this work?  How would one know if these are available?

---

### Post by rkd on 2008-01-12
Sorry for being slow to respond - I was busy all day.

> [QUOTE]Also, I saw more than 50 messages from make saying "Nothing to be done for xxxxx"...
One thing that can cause make to decide that there is nothing to be done is if you do a build in a directory that has results left over from a previous build.
I think this is exactly what happened.  I don't believe there is any reason to delete the directory I un-tarred the package to.  I checked; the installation didn't put anything there.  It seems to have put everything in other locations, so I assumed that by running the install again it would overwrite previous attempts.  It seems that linux is smart enough to know that something has already been done, and so it tells you.[/QUOTE]
You are right that install scripts put the things they build into other locations in the system -- the places where they are ultimately needed. The way I believe install scripts using make know when to put something into those other places is that they compare the timestamp on the destination file with the timestamp of the one in the build location. The possibility I'm thinking of is that the earlier build, because it didn't work quite right, may have built something incorrectly and installed it, then on the subsequent build, it saw that there is something there and accepted it, not knowing that it was built incorrectly the first time and should have been rebuilt. If you wipe out the contents of the directory in which the build was done, an incorrectly-built file can't be left sitting around to cause that kind of mistake. When make is told to build something and it decides that something is already up to date, it displays that "Nothing to be done" message. That might not be the only explanation for that message, but it is one thing that can cause it. So I'm not sure that the scenario I am thinking about actually happened, but I think it might have. So it might be worthwhile to delete everything from the directory and run that install script again in a fresh environment. It's possible that you already did this the way I am suggesting and I just am misinterpreting your reply. If so, sorry and you can ignore this point.

> [QUOTE]I probably should have asked this question long before now: In threads where people are asking about how to build some program from the source distribution, frequently someone will tell them they should install the already-built package from the repositories. Have you already tried that? I don't remember that being asked in this thread. There are times when it is necessary to build from source -- usually when the version in the repository is not as new as it needs to be to support your hardware, or there is no such package in the repository. Are either of those situations the case here?
Can you explain this a bit?  I'm not fully understanding you.  Are you saying that there are already prepared files that don't require all of this work?  How would one know if these are available?[/QUOTE]
Yes, there are already-prepared files for tons of devices. The trick is finding them. Or at least it is still a trick to me because the explanations always seem to leave out that essential information. 

Ubuntu is supposed to find the right driver for you automatically, and when it does, life is good. But, as Frank Capra said, "Automatic just means that you can't fix it yourself." When the automatic driver selection doesn't work, I gather sometimes you can find the right driver in a repository somewhere and install it using apt-get. When the right driver isn't in a repository, or it is there but you don't know what it is called or don't know where the repository is, you end up trying to build it from source, as you are doing.

There are also the restricted drivers. They are drivers that Ubuntu found for you, but won't install unless you tell it to. I don't know what all is in there. If you go to the System menu, open Administration, then open Restricted Drivers Manager, you will see a list of any restricted drivers that Ubuntu will install for you if you just check the "enabled" box. If your sound driver is there, getting it running should be that simple.

As I said, I don't understand it fully, but I have the feeling that the sound driver you need is not likely to be in Restricted Drivers (but take a look, anyway). The sound driver you need could be in some repository somewhere. I don't know what the package would be called and I don't know where to look for repositories that aren't built-in. 

Something else I wonder about is whether building from source will cause any difficulties for you when you want to upgrade to the next version of Ubuntu. I imagine that things you build from source are invisible to the apt-get package management, so it seems to me there is potential for problems when upgrading. Maybe not; I just don't know. Perhaps you need only rebuild the driver from source again. I hope that since you've done that this time, it won't be so hard to do it again, since you know all the right steps. But f that is a problem, it is one you'll hit in the future, not now.

Somewhere, there probably is an explanation of all of this that I just haven't found yet.

You got pointed to this source package in another Ubuntu thread, right? So there is some chance that building from the source is the right way to proceed because that thread was a chance for someone to chime in with the suggestion to get the driver from the xxxxx repository. Since no one did that, perhaps there is no repository for it.

So what is the next step? 

One is that I think you should run the install from source steps again, after removing everything from the directory you did it in. Start with doing the tar command to extract the stuff from the file you downloaded.

Another is to look at the OSS documentation and see whether there are some settings you need to adjust with it.

I'm still concerned about that packages.gz file the apt-get update was unable to fetch from the repository. I don't know whether that is a problem or not. Perhaps we should create a thread asking just that.

If none of those get the sound working properly, we could try to find a pre-built driver. I'm not really sure what to look for, but I'll help you as much as I can with that.

It might be helpful to try a few other programs that produce sound -- try to get a music application to play some .mp3 files (or files with other encodings). Try to play an audio CD from your CD drive. Try to listen to an internet radio station feed. If some of those work and others don't, maybe we can search for tips about the programs that don't work and find the clue we need.

You sure are close to being done with this. I'm sure we'll get there, but it is a bit discouraging that so much work is needed when the pre-built driver isn't available.

---

### Post by ThunderRd on 2008-01-13
> **rkd said:**
> So it might be worthwhile to delete everything from the directory and run that install script again in a fresh environment.
Which directory should I delete?  Do you mean the directory *into which* I untarred the file? Or something else?


> 
 When the automatic driver selection doesn't work, I gather sometimes you can find the right driver in a repository somewhere and install it using apt-get. When the right driver isn't in a repository, or it is there but you don't know what it is called or don't know where the repository is, you end up trying to build it from source, as you are doing.
I am having difficulty getting my head around what to search for, and how.  How does one search unless he knows the name of the file?  I have found a couple of tidbits only because I saw that someone else had them, and posted the filenames.  But I'm a bit lost when I need to find something but I don't know what to instruct apt-get to look for.

> 
As I said, I don't understand it fully, but I have the feeling that the sound driver you need is not likely to be in Restricted Drivers (but take a look, anyway).
You're right.

> 
The sound driver you need could be in some repository somewhere. I don't know what the package would be called and I don't know where to look for repositories that aren't built-in. 
Heh, see above ;)  BTW, are the repositories mirrors?  Or is it necessary to go to different ones for different things?

> 
Something else I wonder about is whether building from source will cause any difficulties for you when you want to upgrade to the next version of Ubuntu. I imagine that things you build from source are invisible to the apt-get package management, so it seems to me there is potential for problems when upgrading. Maybe not; I just don't know.
With any luck the correct stuff will be there by default by that time.

> One is that I think you should run the install from source steps again, after removing everything from the directory you did it in. Start with doing the tar command to extract the stuff from the file you downloaded.
As soon as I'm sure which directory you're referring to.

> 
Another is to look at the OSS documentation and see whether there are some settings you need to adjust with it.
I'm still in the dark on this one.  Is this something I'm supposed to have already?  I find no evidence of it in the system and I'm trying to find some install information on it.

> 
I'm still concerned about that packages.gz file the apt-get update was unable to fetch from the repository. I don't know whether that is a problem or not. Perhaps we should create a thread asking just that.
Let me know when you are out of ideas. :)

> 
It might be helpful to try a few other programs that produce sound...
Everything else I can think of works.  There are some formats like ogg which don't yet but it's clear that software is needed, so I know what to do if I ever need the ability to play those[not likely].

> 
You sure are close to being done with this. I'm sure we'll get there, but it is a bit discouraging that so much work is needed when the pre-built driver isn't available.
I've been working around various boxen too long to be discouraged.  It's just like anything else; it's a learning curve, and it's just a bit different from windows.  I used to work on the command line a lot in the old days in DOS and a little UNIX so it's not entirely foreign to me.  It's more a hobby for me now (and I try to understand as much as I can- the why questions are the toughest); and after working for years in corporate I'm taking it easier these days.

I have done some digging in the forums, and have seen these; see if there is anything there that helps you to help me ;)
[http://www.uluga.ubuntuforums.org/showthread.php?t=649209](http://www.uluga.ubuntuforums.org/showthread.php?t=649209)
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/145866](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/145866)
These users have a similar or identical problem to me; no system sound even thought the test sounds work, the login bongos work, etc.  Other sound devices work.

I'm learning a lot from you.  Thanks for hanging in there.

---

### Post by rkd on 2008-01-13
> Which directory should I delete? Do you mean the directory into which I untarred the file? Or something else?
Yes, the directory into which you untarred the file that you downloaded.

> I am having difficulty getting my head around what to search for, and how. How does one search unless he knows the name of the file? I have found a couple of tidbits only because I saw that someone else had them, and posted the filenames. But I'm a bit lost when I need to find something but I don't know what to instruct apt-get to look for.
This frustrates me, too. I know there are repositories besides the ones Ubuntu has built in because I have seen posts in other threads that give URLs that you can add to your apt-get sources file. I don't know how you learn about these other repositories.

> BTW, are the repositories mirrors? Or is it necessary to go to different ones for different things?
I think there are different repositories for different things, but as I feel I don't really understand the whole picture, I might be mistaken.


> [QUOTE]Another is to look at the OSS documentation and see whether there are some settings you need to adjust with it.
I'm still in the dark on this one. Is this something I'm supposed to have already? I find no evidence of it in the system and I'm trying to find some install information on it.[/QUOTE]
I don't know anything about it, either. I just remember seeing it mentioned in another thread about problems getting sound to work. I poked around in my system a little, and the only place I see it mentioned is System -> Preferences -> Sound. In that window, on the Devices tab, all of the selection boxes have a choice that includes OSS in the name. It sort of looks like you choose among a number of systems for managing your audio devices -- OSS is one, ALSA is another, ESD is another. But I might be misunderstanding. I don't know why you would choose one of those for Sound Events and another for the Mixer, but apparently you can do that. I just don't know how these things are supposed to fit together.

I just spent a couple of minutes web searching. Apparently, the home for OSS is [www.opensound.com](www.opensound.com). I didn't find much documentation there. If you click on "API Specs", then "What is OSS" you can see a few paragraphs of general information, but no details. There might be something more around there somewhere, but I didn't find it. "man oss" had nothing on my system. I don't know where else to look. Maybe some more web searching for Open Source Sound would turn up something.

> I'm learning a lot from you. Thanks for hanging in there.
You're welcome. I'm glad I can help. I just hope I'm not teaching you things that are incorrect. I try to be careful to make it clear when I'm not sure about something that I suggest vs. when I'm pretty confident about it. I've only been reading the Ubuntu forums a few weeks, so there is a lot of stuff I simply don't know. I find I that for me, working on specific projects helps me learn, so helping you on your problems helps me, too. A good arrangement, isn't it?

---

### Post by ThunderRd on 2008-01-13
I'll do the reinstall  and delete the untar directories.  I most likely won't have time to get on it tomorrow so it may be another day.  I'll post back when I do.

Maybe this OSS is a library or package.  I will do some more research.

I am pleased that we have gotten this far.  The rest is not so important, but it is always nice to have things the way they should be.

---

### Post by ThunderRd on 2008-01-16
I tried installing the audio package again after cleaning out the directory- when reviewing the install output I found another reference to an ncurses package; I searched using 'apt-cache search lib ncurse dev' and installed ALL of the resulting packages.  The error went away  after that, but didn't produce any system sounds as yet.

I did some more thinking and thought that all of this installing and re-installing would be enough to confuse any OS, so I started over, deleted the partitions, and re-installed Ubuntu.  The story line is about the same; there were no sounds of any sort after the install.  This time I tried to do things in a more orderly fashion; I installed the SATA drivers first; then installed build-essential, gcc and linux-headers, and then installed the ncurses packages.

After that, I tried building the audio driver.

At first, it didn't seem right; there wasn't any sound still, but there were no errors that I could find in the output.  But I remembered that sometimes, even in Linux, a reboot can give things a kick, so I rebooted.  After the restart...everything worked.

All sound devices that I need are working, as well as the system sounds.  Mission accomplished.

I'm going to mark this thread solved, thanks to you.  But be on the lookout for more new user problems from me!

Thanks again.

EDIT:
Incidentally, I remembered why there was some confusion as to the sound working from the Live disk- it wasn't that at all.  Originally, when I was trying out Ubuntu, I set it up in VMware in XP as a virtual machine.  For some reason, the sound did work then.

---

### Post by rkd on 2008-01-17
Good! I'm glad to hear you finally got everything working.

The explanation for why the sound worked in VMware is that a VMware virtual machine doesn't pass through the actual sound hardware you have -- it emulates some old, standard sound hardware, which Ubuntu clearly had no problem supporting. (As far as I know, it is the same story with all of the hardware in the virtual machine, which is why you can move virtual machines from computer to computer without concerning yourself about installing new drivers or anything.)

I might not notice new threads you open, but if you post and aren't getting answers, go to my profile and send me a private message and I'll go look at the post.

---

