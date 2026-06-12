---
title: "how to transfer data to portable hardrive?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by alexjamestodd on 2007-01-07
Hi folks, does anyone know how to transfer a file to a portable hardrive, I could do it in xubuntu but i am now using fluxubuntu and cant find my hardrive when i plug it in to usb, any help greatly appreciated,Alex

---

### Post by ajmorris on 2007-01-07
open a command line and navigate to /media.

do an [PHP]ls[/PHP] and it should show the device. If it does do a [PHP]mount -w "name of device"[/PHP] If it doesn't you will have to find out what the device is called in order to mount it.


if you [PHP]gedit /etc/fstab[/PHP]  it will propably have it in there.

---

### Post by alexjamestodd on 2007-01-07
thanks, im gonna try that and ill let you know if it works.

---

### Post by alexjamestodd on 2007-01-07
unfortunately my lack of knowledge has stumped me , - i opened xterm and typed /media, it replied "media is a directory. is this the correct way to run a command?

---

### Post by ajmorris on 2007-01-07
sorry bad help from me


it should be [PHP]cd /media[/PHP]

---

### Post by alexjamestodd on 2007-01-07
that worked and gave me the answer "cdrom cdrom0"
do i assume that cdrom0 is my hardrive?

---

### Post by ajmorris on 2007-01-07
cdrom0 is the cdrom drive and cdrom is a link to cdrom0. (at least it is for me)

I am not sure why this is but it just is.

Can you see any other usb devices such as a flash disk?

---

### Post by alexjamestodd on 2007-01-07
there were no other devices listed. when i tried the "gedit etc/fstab " command, it said it was a bad command, im gonna try and install gnome as i ccould acsess the drive using other ubuntu versions, do you think this will work? also when gnome is installed , will i be able to run it from the right click menu?

---

### Post by ajmorris on 2007-01-07
sorry it should be gedit /etc/fstab. But if gnome is not installed then gedit probably won't work. You could try nano instead of gedit. It may work having gnome i don't know but it can't hurt to try as you can still keep your current window manager as well.

Gnome does not get run from the right click menu though. ( i assume you mean been able to run applications from right clicking on the desktop)

---

### Post by Frank Golden on 2007-01-07
> **alexjamestodd said:**
> that worked and gave me the answer "cdrom cdrom0"
do i assume that cdrom0 is my hardrive?No that is your optical drive.
In terminal type [COLOR="Red"]sudo fdisk -l[/COLOR] This will show all drives connected to your machine. Your external drive will be a separate drive in the resulting table.
It will have a designation of hdxx or sdxx depending on whether it is ATA or SATA.
A typical entry will be something like /dev/hda1 or something like that.
To mount note whether the drive is Fat32 or whatever filesystem it is. If it NTFS you won't be able to write to it from Ubuntu unless you use an experimental program.

To mount "temporarilly" first create a mount point. In terminal.
[COLOR="red"]sudo mkdir /media/<anyname you want>[/COLOR]
Next if Fat32 type [COLOR="red"]sudo mount -t vfat /dev/hda1 /media/<anyname you want>[/COLOR] Note: the /dev/hda1 should be the actual entry from the fdisk -l table.
Name the mount point something descriptive like /media/external or something like that.
Make sure you use the same name for the mount point in the mount command.
If the drive is NTFS change vfat to ntfs (lowercase) in the mount command.
This should place a icon on your desktop you can drag and drop files to if
it is Fat32. If you get permission error while trying to copy files type [COLOR="red"]gksudo nautilus /media/<anyname you want>[/COLOR] Again use the mount point
name you chose when you created the mount point. This command will open the drive in nautilus (a file browser like Windows Explorer) as root allowing you to copy and remove files from it.

To mount "permanently" on boot up you need to edit fstab.

Please post the result of [COLOR="red"]sudo fdisk -l [/COLOR] with the drive connected so I can tailor these commands for your setup and provide you with a fstab entry
to mount drive at boot up.

If you mount a Fat32 drive at bootup using the fstab entry I will provide you should have read/write access from the desktop icon.

---

### Post by ajmorris on 2007-01-07
I do suggest a mount -w because a normal mount usually mounts it read only. A mount -w forces it to be writable.

---

### Post by alexjamestodd on 2007-01-07
thanks for all your help and advice, i definately learnt a few things

---

### Post by Frank Golden on 2007-01-07
> **ajmorris said:**
> sorry it should be gedit /etc/fstab. But if gnome is not installed then gedit probably won't work. You could try nano instead of gedit. It may work having gnome i don't know but it can't hurt to try as you can still keep your current window manager as well.

Gnome does not get run from the right click menu though. ( i assume you mean been able to run applications from right clicking on the desktop)to edit fstab you need to be root hence [COLOR="Red"]sudo gedit /etc/fstab [/COLOR]or [COLOR="red"]sudo nano /etc/fstab[/COLOR]. I am experienced with Ubuntu with gnome I have never heard of fluxbuntu.? So some of my advice may need adjusting. Please post the results of [COLOR="red"]sudo fdisk -l[/COLOR] So I can see exactly what your system calls your external drive.

BTW, I just googled fluxbuntu. I guess it is based on Feisty. You sure are pushing the envelope for a new Ubuntu user.
Feisty is still in beta.

---

### Post by alexjamestodd on 2007-01-07
i dont know how to paste the results, i tried the windows way , to no avail,but here is information for you;

fdisk -v             v2.12r
fdisk l, s ,w

hopefully this can be of some use to you.

---

### Post by ajmorris on 2007-01-07
if u wish to paste things from the shell you must right click on the text and click copy and a ctrl+c is a cancel command. Same as pasting to a command line you must either right click and press paste or do shift_ins

---

### Post by ajmorris on 2007-01-07
> **Frank Golden said:**
> to edit fstab you need to be root hence [COLOR="Red"]sudo gedit /etc/fstab [/COLOR]or [COLOR="red"]sudo nano /etc/fstab[/COLOR]. I am experienced with Ubuntu with gnome I have never heard of fluxbuntu.? So some of my advice may need adjusting. Please post the results of [COLOR="red"]sudo fdisk -l[/COLOR] So I can see exactly what your system calls your external drive.

BTW, I just googled fluxbuntu. I guess it is based on Feisty. You sure are pushing the envelope for a new Ubuntu user.
Feisty is still in beta.

I know your very experienced but how will he know what to mount from doing this? i just did this and this happened 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1848    14842880    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1849        3646    14442435    5  Extended
/dev/sda3            3647        3648       16033+   e  W95 FAT16 (LBA)
/dev/sda5            1849        1950      819252   82  Linux swap / Solaris
/dev/sda6            1951        3646    13623088+  83  Linux

but mine are hda1, hda2 and so on.

---

### Post by alexjamestodd on 2007-01-07
i have followed your instructions and did not get an icon on my desktop.
the information is, i believe,   "/dev/sdb6 b w95 fat 32"  this drive had the 30 gig that it is partitioned for so i believe it is the right drive.

---

### Post by ajmorris on 2007-01-07
is it /media?

Did you do a [PHP]sudo mount sdb6 [/PHP] or a [PHP]sudo mount -w sdb6[/PHP]

While in /media?

---

### Post by alexjamestodd on 2007-01-07
i ounted it again using the -w command and it tells me it is already mounted in /media/software       software is the name i gave it, its a shame i cant paste my results as the other user did,
another reply i get is"cant find sdb6 in /etc/fstab or /etc mtab"
Im using fluxbuntu because my laptop is v.old 64 ram pentium 2 and i found xubuntu to slow so im trying a flux window manager, im tempted to try vector linux 4.3 for improved usability .
i only use my laptop for email, surfing , downloading torrents and running my ipod. i ditched windows because i wanted more control over my os, and less reliability on the microsoft way of doing things, i was attracted to ubuntu initially by its humanitarian based philosiphies and people based ideas (which i like)

---

### Post by ajmorris on 2007-01-07
is it in /media/software?

If not try [PHP]sudo mount -w /media/software /dev/sdb6[/PHP]

Then if that doesn't work try everything that you have already tried but replacing sdb6 with hdb6.

so sudo mount-w hdb6 (while in /media) and so on.

Also are you putting sudo infront of your command.

---

### Post by alexjamestodd on 2007-01-07
running that command as sudo with -w , iget, "you must specify the file system type"

---

### Post by alexjamestodd on 2007-01-08
must get some sleep now friends, thanks for help/advice/time, it was informative and appreciated

---

### Post by Frank Golden on 2007-01-08
> **alexjamestodd said:**
> running that command as sudo with -w , iget, "you must specify the file system type"Try [COLOR="Red"]sudo mount -t vfat /dev/sdb6 /media/software[/COLOR] or as ajmorris said change the -t to a -w to mount writable.
It seems that nano is the default text editor in Fluxbuntu. I think ctrl+x is the save command in nano followed by a confirming y. If you need to edit fstab remember this.

---

### Post by Frank Golden on 2007-01-08
> **ajmorris said:**
> I know your very experienced but how will he know what to mount from doing this? i just did this and this happened 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1848    14842880    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1849        3646    14442435    5  Extended
/dev/sda3            3647        3648       16033+   e  W95 FAT16 (LBA)
/dev/sda5            1849        1950      819252   82  Linux swap / Solaris
/dev/sda6            1951        3646    13623088+  83  Linux

but mine are hda1, hda2 and so on.
I wanted this info so I could tailor the terminal commands for his setup.
Less confusion?

---

### Post by Frank Golden on 2007-01-08
> **ajmorris said:**
> is it in /media/software?

If not try [PHP]sudo mount -w /media/software /dev/sdb6[/PHP]

Then if that doesn't work try everything that you have already tried but replacing sdb6 with hdb6.

so sudo mount-w hdb6 (while in /media) and so on.

Also are you putting sudo infront of your command. The command should be
[COLOR="Red"]sudo mount -w vfat /dev/sdb6 /media/software[/COLOR] The command is saying super user mount -w vfat volume /dev/sdb6 to mount point /media/software.
The other way says to mount the mount point to the device.

Edit: xfe is the default file browser in fluxbuntu so commands using nautilus may not work. Try substituting xfe for nautilus in command.
Also since Fluxbuntu doesn't use gnome the commabd gksudo may not work either. gksudo is the prefered method of opening a GUI app. I don't know if there is a Flux substitute or if it is really needed. Sudo may work ok. I just don't know.
The -w flag doesn't appear to exist in the mount command use the -t flag.
As a last note fluxbuntu is so new you may get more help from their forum. Keep at it and keep us posted.

---

### Post by 3rdalbum on 2007-01-08
Fluxbuntu isn't really recommended for people who haven't used the command-line before.

Don't worry, manually mounting is something that I found difficult for a long while, until finally I "got it".

I suggest downloading "ivman" from the repositories:

```
sudo apt-get install ivman
```

Then start ivman (by typing its name on the command-line) before you plug in your hard drive. It will mount the hard drive into the /media directory, but you'll still need to learn how to do "sudo umount /media/mountpoint" where the word "mountpoint" is the name of the directory that takes you to the drive.

---

### Post by Nim on 2007-01-25
> **Frank Golden said:**
> No that is your optical drive.
In terminal type [COLOR="Red"]sudo fdisk -l[/COLOR] This will show all drives connected to your machine. Your external drive will be a separate drive in the resulting table.
It will have a designation of hdxx or sdxx depending on whether it is ATA or SATA.
A typical entry will be something like /dev/hda1 or something like that.
To mount note whether the drive is Fat32 or whatever filesystem it is. If it NTFS you won't be able to write to it from Ubuntu unless you use an experimental program.

To mount "temporarilly" first create a mount point. In terminal.
[COLOR="red"]sudo mkdir /media/<anyname you want>[/COLOR]
Next if Fat32 type [COLOR="red"]sudo mount -t vfat /dev/hda1 /media/<anyname you want>[/COLOR] Note: the /dev/hda1 should be the actual entry from the fdisk -l table.
Name the mount point something descriptive like /media/external or something like that.
Make sure you use the same name for the mount point in the mount command.
If the drive is NTFS change vfat to ntfs (lowercase) in the mount command.
This should place a icon on your desktop you can drag and drop files to if
it is Fat32. If you get permission error while trying to copy files type [COLOR="red"]gksudo nautilus /media/<anyname you want>[/COLOR] Again use the mount point
name you chose when you created the mount point. This command will open the drive in nautilus (a file browser like Windows Explorer) as root allowing you to copy and remove files from it.

To mount "permanently" on boot up you need to edit fstab.

Please post the result of [COLOR="red"]sudo fdisk -l [/COLOR] with the drive connected so I can tailor these commands for your setup and provide you with a fstab entry
to mount drive at boot up.

If you mount a Fat32 drive at bootup using the fstab entry I will provide you should have read/write access from the desktop icon.

My external hardrive is HPFS/NTFS - at present it doesn't let me write to it, is there any way around this at all??

---

