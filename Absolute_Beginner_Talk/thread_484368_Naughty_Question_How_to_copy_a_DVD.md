---
title: "Naughty Question: How to copy a DVD?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-25
How to stick a DVD in, copy it to your computer, then burn onto a DVD which can be played in a standard DVD player?

---

### Post by raul_ on 2007-06-25
By creating an image (iso) file...?

---

### Post by FleetAdmiral74 on 2007-06-25
There are a few dvd ripping and burning programs in the repositories, I would search there first.

---

### Post by punx45 on 2007-06-25
to make a backup copy so your original disc doesnt get ruined, right? ;)

this looks like it might do the trick.   do check synaptic for it first.
[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

---

### Post by Kobalt on 2007-06-25
K3b or Brasero have 'DVD duplicate' tools, but I don't know how they handle DVD protections...

---

### Post by punx45 on 2007-06-25
yes, in most cases just doing a direct disc copy (e.g. creating an ISO and then burning it) will not work because of protection schemes.  you need to use software that circumvents that, which is, sadly, "illegal," but also readily available.

---

### Post by kevdog on 2007-06-25
Everyone knows that although this could possibly be done in Linux, that DVD Decryptor (now defunct) or AnyDVD are the best tools to accomplish what you want to do.  Unfortunately these are only compatible with windows.  If you can get a hold of a copy of DVD Decryptor (watch out for fakes and viruses), Ive seen forums that suggest it can run under WINE.  I havent tried it.

---

### Post by rharris on 2007-06-25
Have a look here:

[http://www.exit1.org/dvdrip/features.cipp](http://www.exit1.org/dvdrip/features.cipp)

Its in the repos. As well as a few other tools that will help you. Search for "dvd" in synaptic

Rob

---

### Post by mikehvorup on 2007-06-25
K9 has always worked well for me when i backup my DVD, installs with automatix if you unhide KDE apps

---

### Post by alan_daniel on 2007-06-25
> **kevdog said:**
> Everyone knows that although this could possibly be done in Linux, that DVD Decryptor (now defunct) or AnyDVD are the best tools to accomplish what you want to do.  Unfortunately these are only compatible with windows.  If you can get a hold of a copy of DVD Decryptor (watch out for fakes and viruses), Ive seen forums that suggest it can run under WINE.  I havent tried it.

DVD Decryptor works fine under WINE. There's the obvious graphical tiny problems, but it works.

To the original poster: Are you asking how to copy an encrypted DVD (ie a commercially bought DVD) or a homemade DVD? The answer to those questions will yield very different methods.

---

### Post by Ssj3_man on 2007-06-25
[http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html](http://www.fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html) + wine = Ahsome; cause it let yous pick the size and my retarded cousin can do it!    :p

---

### Post by user1397 on 2007-06-25
When you do get the dvd ripped to your computer, you might want to try this guide to burn it to a dvd:  _[Make DVD Videos Using Tovid]("http://ubuntuforums.org/showthread.php?t=183936")_

---

### Post by aberadam on 2007-06-26
> To the original poster: Are you asking how to copy an encrypted DVD (ie a commercially bought DVD) or a homemade DVD?

I want to backup my bought DVDs, I have a unique DVD corrosion problem... 

They're protected I believe... need to get around that.

---

### Post by mastergunner on 2007-06-30
I have tried DVD Decrypter and Shrink and I cant get anything to work. I have Kubuntu 7.04 and I am fed up trying to backup my DVD collection. Yes they are encrypted but mine so how is this done?

---

### Post by Delirious on 2007-06-30
> **mastergunner said:**
> I have tried DVD Decrypter and Shrink and I cant get anything to work. I have Kubuntu 7.04 and I am fed up trying to backup my DVD collection. Yes they are encrypted but mine so how is this done?

Have you tried K9copy, its supposed to be the DVD shrink equivalent in linux.

---

### Post by Drakkor on 2007-06-30
I have DVDShrink 3.2 with wine and it works fine !  ;)

---

### Post by tdwester on 2007-06-30
There is also XDVDShrink. It is in the repos and very easy to uses.

---

### Post by mastergunner on 2007-06-30
TDWester I am a Linux noob so could you tell me how to get XDVDShrink? Thanks.

---

### Post by GeeZor on 2007-06-30
```
sudo apt-get install dvdshrink
sudo apt-cache search shrink
```

---

### Post by mastergunner on 2007-06-30
GeeZor thanks but using that found no dvdshrink so no good for me.

---

### Post by Das Goat on 2007-06-30
From the mouth of a Noob:

There is a two step process to copy DVD's in Ubunutu. I know because I just did it a day or two ago.

First go to this link: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

This will tell you how to turn the codecs on so that FIRST your Unbuntu can play a DVD ( you can't copy until you can play).

If you use 64-bit Ubuntu, like me, then you might want to read my post on this thread:
[http://ubuntuforums.org/showthread.php?t=481074](http://ubuntuforums.org/showthread.php?t=481074)

Basically, you need to load the CORRECT libdvdcss2 for your distro under the synaptic package manager.

Now that you can play a DVD, now you can make PERFECTLY LEGAL BACK UP OF YOUR DVD. 

Note that making BACKUPS of other peoples DVDs is not legal. You be your own copy right police.

After I got Unbuntu playing DVDs, i down loaded ACIDRIP and K9Copy form the Synaptic Package Manager.

ACIDRIP worked, but made a mp3 type video. That might be fine, but not really what I was looking for.

K9copy worked even better, as it BACKED UP the DVD to an *.iso image file. (hint, change the destination path to your desktop so you don't have to go hunting for the file when you are done)

Once the *.iso is created, just close k9copy, then right click on the *.iso file and chose "write to disk". Put in a blank DVD of course. But it burnt to a 4.7G DVD, so I didn't have to buy the expensive 8.4G DVDs. So I think k9copy is doing the compression for you as well.

It is just that simple. It worked with 5 of 6 DVD's I just tried. 

BONUS: if you travel a lot, then this is really the way to go, since you can put several of your movies on your laptop and then play the *.iso files instead of carting around all those disks. DON"T ASK ME HOW TO DO THIS! I am trying to figure that out right now before my next trip. But like most things with Ubuntu, some one knows, and I am sure they will tell you if you ask nice!

:popcorn:

---

### Post by PCFascist on 2007-06-30
Thoggen is a GTK based DVD Backup tool that would be suitable for us Xubuntu folk.

---

### Post by brennydoogles on 2007-06-30
You can also use the dd command from terminal, which will make an exact backup of the disk into an ISO. This can be done like this:```
dd if=[COLOR="Red"]/dev/cdrom[/COLOR] of=[COLOR="Blue"]moviename[/COLOR].iso
```

with the text in red being [COLOR="Red"]the location of the dvd[/COLOR]  and the text in blue being [COLOR="Blue"]the desired name for the iso[/COLOR]. Or you can use this shell script to automatically do it. After you download it, use this command to install it:
```
sudo chmod +x cpdvd.sh
sudo ln -s cpdvd.sh /usr/bin/
```

and this code to run it:
```
cpdvd
```
That's it!!

also, you can play iso images in vlc player just as if you had inserted the DVD!!

---

### Post by brennydoogles on 2007-07-01
> **Das Goat said:**
> From the mouth of a Noob:
. 

BONUS: if you travel a lot, then this is really the way to go, since you can put several of your movies on your laptop and then play the *.iso files instead of carting around all those disks. DON"T ASK ME HOW TO DO THIS! I am trying to figure that out right now before my next trip. But like most things with Ubuntu, some one knows, and I am sure they will tell you if you ask nice!

:popcorn:

Install VLC player
```
sudo aptitude install vlc
```
Open the iso with vlc
```
vlc movie.iso
```

you can also create a script to put in your .gnome2/nautilus-scripts/ folder that will do it for you. an example would be this:
```
#!/bin/bash 
# script for playing iso images as dvd's
for I in "$*" 
do 
vlc "$I"
done
exit0
```
Make sure you set the script as executable, and if you do, you can right click any iso, go to scripts, and then play as dvd (or whatever you named the script. That's it!!

---

### Post by aberadam on 2007-07-01
Thanks a lot!  I'll come back to this thread in the future when I need to backup DVDs.

---

### Post by orb9220 on 2007-07-01
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

I use DVDshrink and DVDecrtpter thru wine. Works great.

---

### Post by deanlinkous on 2007-07-01
[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

I dont use the GUI only the script and it handles everything for me...

---

### Post by RTrev on 2007-07-01
> **brennydoogles said:**
> You can also use the dd command from terminal, which will make an exact backup of the disk into an ISO. This can be done like this:```
dd if=[COLOR="Red"]/dev/cdrom[/COLOR] of=[COLOR="Blue"]moviename[/COLOR].iso
```


I can't get this to work for some reason.

The entry for my CD/DVD drive in fstab looks like this:

```

/dev/hda  /media/cdrom0  udf,iso9660 user,noauto  0 0

```

It's quite weird.  I have Ubuntu Feisty 64-bit set to mount removable media when inserted, and the icon for the CD or DVD will appear on my desktop when I stick one in.  But right clicking on it tells me that it is NOT mounted.  

Programs have no trouble accessing the media, but I can't seem to do anything with it using the dd command.  I've tried /dev/hda and /media/cdrom0 but in all cases it gives me output like this:

```

bob@ub64:~$ dd if=/dev/hda of=test.iso
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.018777 seconds, 0.0 kB/s

```

Got any suggestions?  Thanks...

---

### Post by brennydoogles on 2007-07-01
> **RTrev said:**
> I can't get this to work for some reason.

The entry for my CD/DVD drive in fstab looks like this:

```

/dev/hda  /media/cdrom0  udf,iso9660 user,noauto  0 0

```

It's quite weird.  I have Ubuntu Feisty 64-bit set to mount removable media when inserted, and the icon for the CD or DVD will appear on my desktop when I stick one in.  But right clicking on it tells me that it is NOT mounted.  

Programs have no trouble accessing the media, but I can't seem to do anything with it using the dd command.  I've tried /dev/hda and /media/cdrom0 but in all cases it gives me output like this:

```

bob@ub64:~$ dd if=/dev/hda of=test.iso
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.018777 seconds, 0.0 kB/s

```

Got any suggestions?  Thanks...

That fstab entry looks kinda strange.... next time you put a dvd in right click it and see if you can find which device it actually is... hda is usually a hard drive rather than a disk drive.

---

### Post by RTrev on 2007-07-01
> **brennydoogles said:**
> That fstab entry looks kinda strange.... next time you put a dvd in right click it and see if you can find which device it actually is... hda is usually a hard drive rather than a disk drive.

That's an fstab entry that was created automatically on install.  I think it's probably hda because I have 4 SATA disks, and the CD/DVD player is the only device on IDE.

When I right click the image that appears on the desktop when a CD is inserted, it tells me that it's not mounted.

When I open a DVD to play with VLC, it uses /dev/hda as the device, and works fine.

Boy am I confused!  :confused:

---

### Post by brennydoogles on 2007-07-01
> **RTrev said:**
> That's an fstab entry that was created automatically on install.  I think it's probably hda because I have 4 SATA disks, and the CD/DVD player is the only device on IDE.

When I right click the image that appears on the desktop when a CD is inserted, it tells me that it's not mounted.

When I open a DVD to play with VLC, it uses /dev/hda as the device, and works fine.

Boy am I confused!  :confused:

What I would do if I were in your situation would be to attempt to create a new device (kinda) using a symbolic link (I don't know if this would work, or even if it would be a good idea, but this is what I personally would try if I were in your situation). You could do this by typing 
```
sudo ln -s /dev/hda /dev/cdrom
```

and then I would try the dd command as 
```
dd if=/dev/cdrom of=movie.iso
```

let's see what happens if you try this (unless of course you don't feel like it), and then go from there. The other thing you may try is insert the dvd, do ```
sudo mount -a
``` and try again. I just got to thinking about the noauto in your fstab, and that might prove problematic. Let's see!!

---

### Post by RTrev on 2007-07-01
> **brennydoogles said:**
> What I would do if I were in your situation would be to attempt to create a new device (kinda) using a symbolic link (I don't know if this would work, or even if it would be a good idea, but this is what I personally would try if I were in your situation). You could do this by typing 
```
sudo ln -s /dev/hda /dev/cdrom
```

and then I would try the dd command as 
```
dd if=/dev/cdrom of=movie.iso
```

let's see what happens if you try this (unless of course you don't feel like it), and then go from there. The other thing you may try is insert the dvd, do ```
sudo mount -a
``` and try again. I just got to thinking about the noauto in your fstab, and that might prove problematic. Let's see!!

Okay, here's what we got:

```

bob@ub64:~/Desktop$ sudo ln -s /dev/hda /dev/cdrom
ln: creating symbolic link `/dev/cdrom' to `/dev/hda': File exists
bob@ub64:~/Desktop$ dd if=/dev/cdrom of=movie.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.012907 seconds, 0.0 kB/s

```

And then, trying the mount -a command:

```

bob@ub64:~/Desktop$ sudo mount -a
bob@ub64:~/Desktop$ dd if=/dev/cdrom of=movie.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.007596 seconds, 0.0 kB/s

```

EDIT: Also tried using that actual device name from fstab:

```

bob@ub64:~/Desktop$ sudo mount -a
Password:
bob@ub64:~/Desktop$ dd if=/dev/hda of=test.iso
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00765 seconds, 0.0 kB/s

```

And, finally, while actually listening to a music CD in the drive, so there should be no question but what it is actually mounted:

```

bob@ub64:~/Desktop$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/887603fd-77e9-4cf1-b9d0-9979450a3bff / ext3 rw,noatime,nodiratime,data=ordered 0 0
/dev/disk/by-uuid/887603fd-77e9-4cf1-b9d0-9979450a3bff /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /home/bob/Fastdisk ext3 rw,noatime,nodiratime,data=ordered 0 0
/dev/sdc1 /home/bob/Data1 ext3 rw,noatime,nodiratime,data=ordered 0 0
/dev/sdd1 /home/bob/Data2 ext3 rw,noatime,nodiratime,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

EDIT: Also tried just mount command:

```

bob@ub64:~/Desktop$ mount
/dev/sda1 on / type ext3 (rw,noatime,nodiratime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home/bob/Fastdisk type ext3 (rw,noatime,nodiratime)
/dev/sdc1 on /home/bob/Data1 type ext3 (rw,noatime,nodiratime)
/dev/sdd1 on /home/bob/Data2 type ext3 (rw,noatime,nodiratime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

Appreciate your help.  Maybe we can solve this, but I have no idea what I'm doing.. basic noob, you know?  :)  

I could remove the noauto in fstab if that might help, but wouldn't the system try to mount a non-existent media on every boot? 

Open to suggestions.  I'd really like to be able to make iso files of all of my music and movies, which I could listen to directly with VLC and also be able to burn for further backup.  Seemed like dd is the cleanest approach I've seen.  Thanks for your time!

Bob

---

### Post by pyros on 2007-07-01
...

---

### Post by GeeZor on 2007-07-02
In the /etc/fstab, the line should say autoinstead of noauto  for the media to be mounted automatically when inserted..  (/media/cdrom)
try that.. works like a charm.

---

### Post by RTrev on 2007-07-02
> **GeeZor said:**
> In the /etc/fstab, the line should say autoinstead of noauto  for the media to be mounted automatically when inserted..  (/media/cdrom)
try that.. works like a charm.

Okay, my original fstab looked like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  defaults,noatime,nodiratime,errors=remount-ro  0 1
/dev/sda5  none  swap  sw  0 0
/dev/hda  /media/cdrom0  udf,iso9660  user,noauto  0 0
#
# Add the other three disks, all auto-mounted and ready to use
#
/dev/sdb1  /home/bob/Fastdisk  ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdc1  /home/bob/Data1     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdd1  /home/bob/Data2     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2

```

I changed it to this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  defaults,noatime,nodiratime,errors=remount-ro  0 1
/dev/sda5  none  swap  sw  0 0
/dev/hda  /media/cdrom0  udf,iso9660  user,auto  0 0
#
# Add the other three disks, all auto-mounted and ready to use
#
/dev/sdb1  /home/bob/Fastdisk  ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdc1  /home/bob/Data1     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdd1  /home/bob/Data2     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2

```

Just that one little change resulted in some weirdness on reboot.  I got lucky when rebooting, because one of my 500G drives needed to be checked after 31 mounts, so I had lots of time to write down what was there.  :)

The first difference was that Kinit tried to resume from a different disk prior to realizing there was no image and booting normally.  It used to try /dev/sda8 or something like that, but this time it tried /dev/disk/by-uuid/and the usual bunch of uuid numbers.

The second difference was that right after it said * Reading files needed to boot, it gave me a new error message:

[3687924] usb 1-6: can't set config # 1, error - 62

I may have got those initial numbers wrong.  I wasn't sure how much time I had so was scribbling like mad.  :)  Maybe it's in my kernel log.

Finally the disk check finished (telling me I had 38.6% non-contiguous.. maybe I should use a different file system for large files?)

When I got back to the desktop, I tried all of the copy things with the CD/DVD again, and again they didn't work.  When the icon appears on the desktop, right clicking it still shows that it's NOT mounted.

I'm beginning to wonder if either my file system is all screwed up, or if this could be a bug, because the only thing to change to cause all of these errors was to a device on the IDE bus.. why would that result in usb errors and an attempt to resume from an image on another device (which, thanks to the uuid stuff, I'm not sure what it was?)

I'll change that one value back, and reboot, and see if the new error messages go away again.

Aren't computers fun?  ;-)

---

### Post by brennydoogles on 2007-07-02
> **RTrev said:**
> Okay, my original fstab looked like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  defaults,noatime,nodiratime,errors=remount-ro  0 1
/dev/sda5  none  swap  sw  0 0
/dev/hda  /media/cdrom0  udf,iso9660  user,noauto  0 0
#
# Add the other three disks, all auto-mounted and ready to use
#
/dev/sdb1  /home/bob/Fastdisk  ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdc1  /home/bob/Data1     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdd1  /home/bob/Data2     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2

```

I changed it to this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  defaults,noatime,nodiratime,errors=remount-ro  0 1
/dev/sda5  none  swap  sw  0 0
/dev/hda  /media/cdrom0  udf,iso9660  user,auto  0 0
#
# Add the other three disks, all auto-mounted and ready to use
#
/dev/sdb1  /home/bob/Fastdisk  ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdc1  /home/bob/Data1     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2
/dev/sdd1  /home/bob/Data2     ext3  user,auto,async,noatime,nodiratime,rw,dev,exec,suid  0 2

```

Just that one little change resulted in some weirdness on reboot.  I got lucky when rebooting, because one of my 500G drives needed to be checked after 31 mounts, so I had lots of time to write down what was there.  :)

The first difference was that Kinit tried to resume from a different disk prior to realizing there was no image and booting normally.  It used to try /dev/sda8 or something like that, but this time it tried /dev/disk/by-uuid/and the usual bunch of uuid numbers.

The second difference was that right after it said * Reading files needed to boot, it gave me a new error message:

[3687924] usb 1-6: can't set config # 1, error - 62

I may have got those initial numbers wrong.  I wasn't sure how much time I had so was scribbling like mad.  :)  Maybe it's in my kernel log.

Finally the disk check finished (telling me I had 38.6% non-contiguous.. maybe I should use a different file system for large files?)

When I got back to the desktop, I tried all of the copy things with the CD/DVD again, and again they didn't work.  When the icon appears on the desktop, right clicking it still shows that it's NOT mounted.

I'm beginning to wonder if either my file system is all screwed up, or if this could be a bug, because the only thing to change to cause all of these errors was to a device on the IDE bus.. why would that result in usb errors and an attempt to resume from an image on another device (which, thanks to the uuid stuff, I'm not sure what it was?)

I'll change that one value back, and reboot, and see if the new error messages go away again.

Aren't computers fun?  ;-)

I'm afraid this is beyond my experience to fix :0/ . Maybe I can help track down someone with more experience to help us out. Let's see what we can make happen!!

---

### Post by RTrev on 2007-07-02
> **brennydoogles said:**
> I'm afraid this is beyond my experience to fix :0/ . Maybe I can help track down someone with more experience to help us out. Let's see what we can make happen!!

Understood, and thanks for trying!  And if you find someone, I'm all ears as Ross Perot used to say.  :-)

Thanks again,
Bob

---

### Post by mastergunner on 2007-07-02
How do you exactly change fstab? I looked at mine and my cdrom said noauto. I am a noob so step by step would help. Thanks.

---

### Post by RTrev on 2007-07-02
> **mastergunner said:**
> How do you exactly change fstab? I looked at mine and my cdrom said noauto. I am a noob so step by step would help. Thanks.

Assuming your using Ubuntu (the Gnome version), you'd issue a command like this:

```

sudo gedit /etc/fstab

```

That just means run as root, use your editor, and edit the file /etc/fstab

If you have a different text editor you prefer, just subsitute it for gedit.

HTH?

Bob

---

### Post by mastergunner on 2007-07-02
What would it be in Kubuntu cause gedit doesnt work.

---

### Post by RTrev on 2007-07-02
> **mastergunner said:**
> What would it be in Kubuntu cause gedit doesnt work.

Try kate or kedit I think.  I'm not a KDE guy.  You might also have nano, which is a non-gui editor but easy to use. 

Bob

---

### Post by rickycodie on 2007-07-02
kde? good get mandvd. it's friggin' awesome!!!

in the applications menu go to add/remove programs, then  in the search coulmn, type mandvd click the mark and hit apply then it's done.

have fun!

---

### Post by Pathfinder_ on 2007-07-02
I use K9copy and it has never failed me.

---

### Post by RTrev on 2007-07-02
> **rickycodie said:**
> kde? good get mandvd. it's friggin' awesome!!!

in the applications menu go to add/remove programs, then  in the search coulmn, type mandvd click the mark and hit apply then it's done.

have fun!

Hi ricky,

I'm on Gnome.  It  was mastergunner asking about how to do it in KDE.

I can use k3b to get iso files from my DVDs, although it meant loading a lot of kde libraries and whatnot.  But I can't find any way to get an iso file from a CD, whether it's music, data, or whatever.  That's the part that's missing for me.  I can rip the CDs to a folder full of FLAC or OGG files, but I can't just get a nice clean iso file.

The dd command is so appealing because it's simple and clean and doesn't require a ton of code on my system which I otherwise try to keep pristine.  :-)

Bob

---

### Post by brennydoogles on 2007-07-02
> **RTrev said:**
> Hi ricky,

I'm on Gnome.  It  was mastergunner asking about how to do it in KDE.

I can use k3b to get iso files from my DVDs, although it meant loading a lot of kde libraries and whatnot.  But I can't find any way to get an iso file from a CD, whether it's music, data, or whatever.  That's the part that's missing for me.  I can rip the CDs to a folder full of FLAC or OGG files, but I can't just get a nice clean iso file.

The dd command is so appealing because it's simple and clean and doesn't require a ton of code on my system which I otherwise try to keep pristine.  :-)

Bob

I may have just emulated your issue. Do you have everything installed that you would need to play all types of dvd's??? Try this:
```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

sudo apt-get install w32codecs

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

sudo apt-get install libdvdcss2

```
Tell me what happens after yo do this, and let's see if we can get this working.

---

### Post by RTrev on 2007-07-02
Okay, I think we've spotted some problems if all of those things are needed.  :)

I'll just list the ones which generated something besides a message to the effect that it was already installed and the latest version.

```

bob@ub64:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll
bob@ub64:~$ 

```

```

bob@ub64:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
bob@ub64:~$ 

```

```

bob@ub64:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

Install debhelper and fakeroot, then run this script again
bob@ub64:~$ 

```

All of the rest worked fine, but said I already had the latest version.

Now I'll go back through and see about getting those packages that were missing, or that couldn't install for some reason.  Once I get it all installed, I'll reboot and then try it all again from the beginning.  Thanks much!

BTW, here is my /etc/apt/sources.list just in case there is something critical missing:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

Really appreciate you hanging in there with me!  :-)

Bob

---

### Post by 3rdalbum on 2007-07-02
If the disc is a DVD-5 (that is, its contents fit onto a single-sided, single-layer DVD), you can do a straight DVD copy with K3B, as long as you have libdvdcss.

---

### Post by brennydoogles on 2007-07-02
> **RTrev said:**
> Okay, I think we've spotted some problems if all of those things are needed.  :)

I'll just list the ones which generated something besides a message to the effect that it was already installed and the latest version.

```

bob@ub64:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll
bob@ub64:~$ 

```

```

bob@ub64:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
bob@ub64:~$ 

```

```

bob@ub64:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

Install debhelper and fakeroot, then run this script again
bob@ub64:~$ 

```

All of the rest worked fine, but said I already had the latest version.

Now I'll go back through and see about getting those packages that were missing, or that couldn't install for some reason.  Once I get it all installed, I'll reboot and then try it all again from the beginning.  Thanks much!

BTW, here is my /etc/apt/sources.list just in case there is something critical missing:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

Really appreciate you hanging in there with me!  :-)

Bob

Looks great!! Let's see if this can get us taken care of!!

---

### Post by RTrev on 2007-07-02
Okay, I installed everything I could find, but the error on that one command continues.  I reinstalled gcc, and cannot find the config.log file it says to look at.

```

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

```

I see that I have the w64codecs installed, but not the w32codecs.  Is the problem that I'm running 64-bit?  If I did a clean install of 32-bit, would all of this be taken care of automatically?

I also cannot find anything even remotely resembling *pitfdll*:

```

bob@ub64:~$ sudo apt-get install gstreamer0.10-pitfdll
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
bob@ub64:~$ 

```

I think we're close... very, very close... :-)

---

### Post by RTrev on 2007-07-03
Lordy, what a night I've had.

First, decided that probably things would work better if I were running 32-bit, at least as far as the audio/video stuff goes.

Decided to dual-boot my Feisty-64 with an install of Feisty-32.

Downloaded the alternate CD for Feisty-32, and burned it with Gnomebaker as I always do.  No matter what I tried, it wouldn't boot.

Burned it again.  Still wouldn't boot.

Decided I must have somehow gotten a bad download, so downloaded the regular CD.  Same deal, wouldn't boot at all.

Wondered if I'd somehow hosed my hardware.. but a test of another bootable CD booted fine.  Decided I must have somehow screwed up my system so that Gnomebaker could no longer burn CDs correctly.

Found an old copy of Feisty-32 that I gotten when Feisty was first released.  It booted fine.

Installed that, went through all of the updates, configured Twinview, set up my other disks, basically got everything tweaked the way I like it.

Then, while doing something else, noticed that Feisty-32 could only see 2G of my 4G of RAM.  Not pleased, but figured I could just use the 32-bit version for doing the copying of CDs and DVDs.

Installed all of the stuff you'd listed, and it all came down fine this time, except that it told me I had just reverted to an older version of libdvdcss2.  Up pops an update notice, telling me that there's a newer version of this file.  Figure I'll try it with the old version just in case the newer one was hosed somehow.

Went through the whole routine of testing again, and got the same results.  Couldn't read the CD with the dd command.

Okay, just for the heck of it, I put in a DVD.. and it worked!  Or so I thought.  After about 15 minutes, it was done, and looking at the iso image I'd created I found that it was only 8 K.  Of course nothing would read it.

So, after all of this, I have a 32-bit system that can't see half of my RAM, and a 64-bit system that can't read or write CDs or DVDs anymore.

The sun is coming up, and my eyelids are drooping, and I think I'm too tired to try anything more without a bit of sleep.  :-)

I've got a tentative plan, though.  I initially set this system up with two 74G 10,000 RPM Raptors, with the idea of running the OS as RAID-0 for speed.  I figure my bottleneck is the disk, as I don't know of any disk that can fill the pipe on a SATA connection.  But two Raptors might come close on a SATA-1 connection like I have.  So, given my current state, I think it's time to try the mdadm software RAID approach again.  I never got it working before, but since I'm pretty well hosed at the moment it's a good excuse to try it again.

Maybe a 2G boot partition on one of the disks, and a 2G swap on the other, and then the rest of each disk left for the RAID-0?  And once I'm up and running again, then figure out the iso issue.  So first thing to do is download and burn an alternate CD of Feisty-64, I guess.  I'll start that running (slow DSL) and then get some sleep.  And then tackle this fresh.

It gives me a good excuse to do what I've been wanting to do for a long time, but screwed it up a few times and decided to bag it for a while.  Time to try it again.

Thanks for all the help.. I learned a lot during this and I truly appreciate it.  There's something weird with my drive or the way it's hooked up, apparently.. because this seems to work for everybody else.  I'll figure that out once I have a solid 64-bit system.. hopefully running like lightning!  :-)

Really appreciate all the time and effort you put into this for me.. and I won't forget it.

Warm regards,
Bob (who may be off-line for a while)  :-)

---

### Post by tregeagle on 2007-07-03
The **dd** command is a basically a straight forward copy command - **it won't get past any copy protection** or it will most likely produce a broken ISO (playing with the fstab won't fix it if this is the case!)

So **dd** is fine to copy your own home DVD or an unprotected volume - but for anything else you might want to look at getting one of the other suggestions:
[LIST=1]
[*][dvd:rip]("http://www.exit1.org/dvdrip/") 

[*][k9copy]("http://k9copy.sourceforge.net/")

[*][dvdshrink on wine]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

[*][XDVDshrink]("http://dvdshrink.sourceforge.net/")
[/LIST]

Good luck :)

---

### Post by Hallvor on 2007-07-03
And if none of those above work (because of e.g. Macromedia copy protection), you can make a backup using VLC media player, as long as you are able to play the movie with it. It is the only application I have found for linux that is able to deal with advanced copy protection.

---

### Post by RTrev on 2007-07-03
> **tregeagle said:**
> The **dd** command is a basically a straight forward copy command - **it won't get past any copy protection** or it will most likely produce a broken ISO (playing with the fstab won't fix it if this is the case!)

So **dd** is fine to copy your own home DVD or an unprotected volume - but for anything else you might want to look at getting one of the other suggestions:
[LIST=1]
[*][dvd:rip]("http://www.exit1.org/dvdrip/") 

[*][k9copy]("http://k9copy.sourceforge.net/")

[*][dvdshrink on wine]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

[*][XDVDshrink]("http://dvdshrink.sourceforge.net/")
[/LIST]

Good luck :)

Hmm... I thought dd was a byte for byte copy routine, and I didn't expect it to change anything about the copy protection.  I just wanted an exact duplicate of the media as an iso file.  The copy protection is the css scrambling, and is dealt with at playback time.  I'm not trying to remove copy protection.  I can play the copy protected CDs and DVDs, and I've successfully created iso files of my DVDs and VLC plays them fine.  I thought the same would be the case for CDs, but have yet to get that to work.  Nautilus will create an iso file of a CD for me, but it also creates a .toc (table of contents) file, and neither one will play.  I may be misunderstanding all of this, but I was under the impression that an iso could be created for *any* CD/DVD media.  A single iso file which is an exact duplicate of the contents, and can be burned back if needed to the same type of media.  Or played directly on the hard drive.

I couldn't get any routine to copy a CD, although k3b did a nice job of copying the DVDs.  I don't want to shrink the stuff, but keep it exactly as I purchased it.  There seems to be nothing in Gnome that I've found that works, which means a lot of KDE stuff on the disk.  That's why dd looked really appealing.  Clean and simple, and already installed.

Am I completely off-base here?  It wouldn't be the first time!  :)

Bob

---

### Post by RTrev on 2007-07-03
> **Hallvor said:**
> And if none of those above work (because of e.g. Macromedia copy protection), you can make a backup using VLC media player, as long as you are able to play the movie with it. It is the only application I have found for linux that is able to deal with advanced copy protection.

Oh really!  VLC has more tricks up its sleeve than I realized.  I'll have to look at that.  I simply never occurred to me that VLC was anything but a playback system.  Thanks, this sounds promising.. everything I have I can play with VLC.

Bob

---

### Post by hyper_ch on 2007-07-03
Some people have issued their opinions on whether something is legal or not. What they all keep forgetting is, that each country has a different set of legal rules regarding that issue. What in one country may be illegal could be legal in another one.

---

### Post by RTrev on 2007-07-03
> **hyper_ch said:**
> Some people have issued their opinions on whether something is legal or not. What they all keep forgetting is, that each country has a different set of legal rules regarding that issue. What in one country may be illegal could be legal in another one.

I tend to look at things like this more from the perspective of if it's morally correct.  I don't see anything morally objectionable to making a backup of something I paid for, and that only I will ever watch.  But I recognize that the issue exists.  It's kind of a gray area for me.  If we wanted to be completely within the law in all respects, I think we'd be required to drive at night only if somebody was walking ahead of us holding a lantern.  I've been told that law never got taken off the books.  ;)

---

### Post by Hallvor on 2007-07-03
> **RTrev said:**
> Oh really!  VLC has more tricks up its sleeve than I realized.  I'll have to look at that.  I simply never occurred to me that VLC was anything but a playback system.  Thanks, this sounds promising.. everything I have I can play with VLC.

Bob

Try this for DVD backups:
[http://software.newsforge.com/article.pl?sid=06/04/19/1711245&from=rss](http://software.newsforge.com/article.pl?sid=06/04/19/1711245&from=rss)

This may also be useful. Streaming with VLC:
[http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

---

### Post by GeeZor on 2007-07-03
.

---

### Post by RTrev on 2007-07-03
> **Hallvor said:**
> Try this for DVD backups:
[http://software.newsforge.com/article.pl?sid=06/04/19/1711245&from=rss](http://software.newsforge.com/article.pl?sid=06/04/19/1711245&from=rss)

This may also be useful. Streaming with VLC:
[http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

Bookmarked..  thank you very much!

---

### Post by mastergunner on 2007-07-03
I still dont get it. How do you modify the fstab so I can get my DVD drives to mount automatically?in kubuntu. Again I am a noob so a step by step explanation will help. Thanks.

> **RTrev said:**
> Try kate or kedit I think.  I'm not a KDE guy.  You might also have nano, which is a non-gui editor but easy to use. 

Bob

---

### Post by mastergunner on 2007-07-03
Rickie did that and it came back with no program found. Any ideas?

> **rickycodie said:**
> kde? good get mandvd. it's friggin' awesome!!!

in the applications menu go to add/remove programs, then  in the search coulmn, type mandvd click the mark and hit apply then it's done.

have fun!

---

### Post by RTrev on 2007-07-03
> **mastergunner said:**
> I still dont get it. How do you modify the fstab so I can get my DVD drives to mount automatically?in kubuntu. Again I am a noob so a step by step explanation will help. Thanks.

I think one of these other folks could help more.. I'm the guy who's having all the trouble with this stuff.  :-)

I'm sorry I didn't give you more elaborate instructuions before.. I thought you were simply asking where the file was and how to edit it.  I'm a bit confused myself about auto versus noauto when it comes to removable media.  I've told the system to mount CDs and DVDs automatically, but I see the icon on the desktop and look at it and it says it's not mounted.  Sorry I can't help with this.

Bob

---

### Post by mastergunner on 2007-07-03
Hey Bob we are both in the same boat so maybe someone will come on and help us out.

---

### Post by catnappist on 2007-07-03
Frankly, this is the main reason I've kept Windows XP (as a dual boot). When I can't copy... I mean... back up a commercial DVD with DVD Decryptor, DVDShrink, and Ripit4me, I use MagicDVDCopier.  I haven't had any luck with WINE, K9Copy, or dvdrip. I also can't seem to play videos with Ubuntu, but that's another issue...

---

### Post by hyper_ch on 2007-07-03
dvddecrypter runs fine in wine... what I needed to do is set the environment to WinNT in wine for dvddecrypter...

---

### Post by mastergunner on 2007-07-03
Well I cant get dvd decrypter or shrink to work well in Wine.

---

### Post by hyper_ch on 2007-07-03
have you tried changing the environment for dvddecrypter to winnt?

---

### Post by mastergunner on 2007-07-03
I did and it still works like garbage.

---

### Post by coolen on 2007-07-04
> **Das Goat said:**
> BONUS: if you travel a lot, then this is really the way to go, since you can put several of your movies on your laptop and then play the *.iso files instead of carting around all those disks. DON"T ASK ME HOW TO DO THIS! I am trying to figure that out right now before my next trip. But like most things with Ubuntu, some one knows, and I am sure they will tell you if you ask nice!

:popcorn:

Totem -> Movie -> Open Location
Point it to the iso, and enjoy.

---

### Post by Hallvor on 2007-07-04
> **mastergunner said:**
> I did and it still works like garbage.

I think it is better to use a native client for backups, like K9copy. Works the same way as dvdshrink in Windows.

If you want to make an xvid, use Acidrip or dvd::rip.

---

### Post by brennydoogles on 2007-07-04
> **RTrev said:**
> Okay, I installed everything I could find, but the error on that one command continues.  I reinstalled gcc, and cannot find the config.log file it says to look at.

```

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

```

I see that I have the w64codecs installed, but not the w32codecs.  Is the problem that I'm running 64-bit?  If I did a clean install of 32-bit, would all of this be taken care of automatically?

I also cannot find anything even remotely resembling *pitfdll*:

```

bob@ub64:~$ sudo apt-get install gstreamer0.10-pitfdll
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
bob@ub64:~$ 

```

I think we're close... very, very close... :-)

Do you know what your default shell is?? If it is not BASH, maybe try and make it so like this:
```
sudo rm /bin/dash
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/dash
sudo ln -s /bin/bash /bin/sh
```

---

### Post by RTrev on 2007-07-04
> **brennydoogles said:**
> Do you know what your default shell is?? If it is not BASH, maybe try and make it so like this:
```
sudo rm /bin/dash
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/dash
sudo ln -s /bin/bash /bin/sh
```

GNU bash, version 3.2.13(1)-release (x86_64-pc-linux-gnu)

It called GNOME Terminal 2.18.0 on this system.

I'm back up and running in 64-bit, and installed LVM this time.  Now I'm looking for how I can use it, among other things, to mimic a RAID-0 setup for two Raptor system disks.

Still haven't figured out the dd thing.  I hear lots of people rave about how cool it is, for example using it to copy an old hard drive contents to a new drive.. and the drive is bootable when done.  Sounds like a great tool.  I'm wondering if my problem isn't my actual drive.  Here is what hal says about it.  Maybe there is a clue here somewhere:

```

udi = '/org/freedesktop/Hal/devices/storage_model_MAD_DOG_LS_DVDRW_TSH652M'
  storage.partitioning_scheme = ''  (string)
  storage.removable.media_size = 481341440  (0x1cb0b000)  (uint64)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage'} (string list)
  info.addons = {'hald-addon-storage'} (string list)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_MAD_DOG_LS_DVDRW_TSH652M'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_MAD_DOG_LS_DVDRW_TSH652M'  (string)
  linux.fstab.options = 'user,noauto'  (string)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  storage.cdrom.write_speed = 8468  (0x2114)  (int)
  storage.cdrom.read_speed = 8468  (0x2114)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'MAD DOG LS-DVDRW TSH652M'  (string)
  storage.size = 0  (0x0)  (uint64)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_10de_53_ide_0_0'  (string)
  storage.firmware_version = 'MD00'  (string)
  storage.vendor = ''  (string)
  storage.model = 'MAD DOG LS-DVDRW TSH652M'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = true  (bool)
  storage.bus = 'ide'  (string)
  block.is_volume = false  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 3  (0x3)  (int)
  block.device = '/dev/hda'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_53_ide_0_0'  (string)
  linux.sysfs_path_device = '/sys/block/hda'  (string)
  linux.sysfs_path = '/sys/block/hda'  (string)

```

Bob

---

### Post by RTrev on 2007-07-04
Hey, I think maybe I have a lead on what the problem is:

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

I was told that we could use any convention in fstab, but this article seems to suggest otherwise.

Bob

---

### Post by RTrev on 2007-07-04
Sigh, no.. the /media/cdrom0 is the mount point, and even using their commands, which shouldn't have been needed since I did a fresh install of Feisty instead of an upgrade, left the /dev/hda in the fstab.  Back to square zero.  :)

---

