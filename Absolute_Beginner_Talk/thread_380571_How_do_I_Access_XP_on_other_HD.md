---
title: "How do I Access XP on other HD?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by pedegalinha on 2007-03-09
Hello

How do I access XP on the other harddrive?  How do I find the other HD?

all the best

Pedegalinha

---

### Post by taurus on 2007-03-09
Here you go.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by pedegalinha on 2007-03-10
> **taurus said:**
> Here you go.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Thanks for the reply however I cant even get past the first step in the link.  I am very new to linux and will not give up.  I refuse to be a slave to Micro$oft.  I just need some help and none of my friends use linux.

"Mounting Windows Partitions in Ubuntu
If you already have your Windows partitions mounted (but with the wrong permissions), unmount them before beginning these instructions. For example, if your Windows partition is mounted as /media/hda1, then open up a terminal and type:

sudo umount /media/hda1"

I dont even understand what what this means.  If windows partition is mounted as /media/hda1.  I dont know what "Mounted as" means.  When I type the command in the Terminal it cant find it so obviously it is not "Mounted" anywhere in or under media/hda1.

All I know is that when I go into disk manager I can see both HD's and the XP one gives 2 tabs that say properties and Partitions.  Properties says /dev/hda.  Partition 1 says Device: /devhda1 
Filesystem: windows virtual fat (Vfat)
Access Path: none
Size: 5.27 gib (free space not available)
Status: Inaccessible

Partition 2...

Device: /dev/hda2
filesystem: windows ntfs
Access Path: /tmp/disks-conf-hda2
Size 181.04 gib (151.03 gib free)
Status: accessible

When I click browse it gives the error:

The Folder contents could not be displayed.  You do not have the permission necessary to view the contents of "Disks-conf-hda2".

Please, if thre is somebody out there that has patience and will help out a new person step by step please reply if you can.

Best Regards

Pedegalinha

---

### Post by taurus on 2007-03-10
Okay, will walk you through this whole thing then.  Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by mikewhatever on 2007-03-10
A little something on mount points [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

---

### Post by pedegalinha on 2007-03-10
> **taurus said:**
> Okay, will walk you through this whole thing then.  Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         731     5526328+   b  W95 FAT32
/dev/hda2   *         732       25841   189831600    7  HPFS/NTFS

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       38725   311058531   83  Linux
/dev/hdb2           38726       38913     1510110    5  Extended
/dev/hdb5           38726       38913     1510078+  82  Linux swap / Solaris



And:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Thanks for the help!

next step?

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> A little something on mount points [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

Awsome!  Thanks!!!

---

### Post by taurus on 2007-03-10
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following two lines to the end of it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hda2
sudo mount -a
df -h
```

---

### Post by pedegalinha on 2007-03-10
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following two lines to the end of it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hda2
sudo mount -a
df -h
```

This is what happens after I type the edit /etc/fstab command:

Warning: unknown mime-type for "/etc/fstab" -- using "application/*"
Error: no write permission for file "/etc/fstab"


Going out on a limb...would this make sence?  "mount /dev/hda/ mnt/hda"  or am I getting way to ahead of myself and should just stick to your next step which is more than likely correct.  Sorry, the wheels are turning but the tires are flat.

---

### Post by mikewhatever on 2007-03-10
The commands Taurus posted are in the boxes, not above. Edit /etc/fstab is what the command in the box below do, opens fstab file for editing.

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> The commands Taurus posted are in the boxes, not above. Edit /etc/fstab is what the command in the box below do, opens fstab file for editing.


Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             292G  2.4G  275G   1% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  164K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-28-386/volatile
/dev/hda2             182G   31G  152G  17% /tmp/disks-conf-hda2
/dev/hda1             5.3G  4.5G  795M  86% /media/hda1


Got up to this point...fingers crossed...now?

---

### Post by mikewhatever on 2007-03-10
Now the two partitions are mounted in /media/hda1 and /media/hda2. Adding the lines to fstab makes sure they will be mounted there on every boot. You should also get the shortcuts on the desktop.

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> Now the two partitions are mounted in /media/hda1 and /media/hda2. Adding the lines to fstab makes sure they will be mounted there on every boot. You should also get the shortcuts on the desktop.

Ummmm

I know have access to that HD but I cant find anything on it.  No "My documents" or anything to where my MP3's are stored in windows.  There also was no shortcut on the desktop.  What else do I need to do so I can access all my music?

Thanks agian

---

### Post by mikewhatever on 2007-03-10
I would cross fingers and reboot.

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> I would cross fingers and reboot.

ahahahhahahhahahahhahahhah

Let the games begin!

BRB

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> I would cross fingers and reboot.

OK!  

Shortcut on desktop!

Access to pics
Access to music
access to videos!

I can see pics...
MUSIC WONT PLAY!
Videos wont play!


AHhhhhhhhhhhhh so close but so far away!  MUSIC IS MY LIFE!!!  Please somebody help me!

try to open them and it says "Could not connect to sound server".  

Cd Player: Drive Error
XMMS: Please check that: Your soundcard is configured properly, You have the correct Output plugin selected, No other program is blocking the soundcard.

New thread?  Can somebody continue to guide me?

---

### Post by taurus on 2007-03-10
Is your soundcard working at all?  When you log in, do you hear any music playing?  What kind of soundcard do you have?

```
lspci
```

---

### Post by pedegalinha on 2007-03-10
> **taurus said:**
> Is your soundcard working at all?  When you log in, do you hear any music playing?  What kind of soundcard do you have?

```
lspci
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host B ridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Modem: Motorola: Unknown device 3052 (rev 04)
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controll er (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500 ] (rev a1)


My sound is not working at all.  I have been having this problem on and off for 2 days now.  I though it was with skype.  I cant use skype half the time because it says I have a problem.  Sometimes streetfire.net has no sound and myspace also.  after a reboot it works some times though.  Until now I though skype was causing this because when I de-installed skype stuff worked however something must be off somewhere.

---

### Post by pedegalinha on 2007-03-10
> **pedegalinha said:**
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host B ridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Modem: Motorola: Unknown device 3052 (rev 04)
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controll er (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500 ] (rev a1)


My sound is not working at all.  I have been having this problem on and off for 2 days now.  I though it was with skype.  I cant use skype half the time because it says I have a problem.  Sometimes streetfire.net has no sound and myspace also.  after a reboot it works some times though.  Until now I though skype was causing this because when I de-installed skype stuff worked however something must be off somewhere.

Rebooted and still streetfire.net does not have sound but myspace does.  No way to play mp3's from other HD and whey I try by double clicking it brings up this error also with the program that tries to open it:

Totem could not play 'file:///media/hda2/Documents and Settings/Compaq_Owner/My Documents/music/Metal/Amon Amarth/With Oden On Our Side/Amon Amarth - With Oden On Our Side - 06 - With Oden On Our Side.mp3'.

You do not have a dcoder installed to handle this file.
You might need to install the necessary plugins.

This still dont explain streetfire.net...gotta be something with the configuation right?

---

### Post by taurus on 2007-03-10
You need to install codecs first before you can play your music or video.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mikewhatever on 2007-03-10
In order to play MP3s, restricted formats codecs must be installed
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> In order to play MP3s, restricted formats codecs must be installed
[https://help.ubuntu.com/community/IndonesianRestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/IndonesianRestrictedFormats?highlight=%28restricted%29)

That was the indonesian link...but I got the point...I will read on.

Thanks!

---

### Post by mikewhatever on 2007-03-10
Changed it to the right one, sorry.

---

### Post by pedegalinha on 2007-03-10
> **mikewhatever said:**
> Changed it to the right one, sorry.

Already done brother!

Thanks again for the help now I can listen to music!!!  Thanks to everybody who helped!

\m/

---

