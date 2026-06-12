---
title: "Mounting Windows Partition"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by IDipSkoalMint on 2006-03-27
I've read a few guides on how to mount my Windows partition in Linux (so I can use Linux and listen to my .mp3 and .m4a music files), and I try to enter the following line into Terminal:

"mkdir /mnt/win"

Whenever I do so, I get a error message saying the following:

mkdir: cannot create directory `/mnt/win': Permission denied

I am the only account and I am able to get updates and everything. Can someone point me in the right direction? I even went to File Browser and opened up the "mnt" folder and tried to use the "mkdir /win" command and got the same error message (only without the "/mnt" section). Thanks.


Regards,
Matthew

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]I've read a few guides on how to mount my Windows partition in Linux (so I can use Linux and listen to my .mp3 and .m4a music files), and I try to enter the following line into Terminal:

"mkdir /mnt/win"

Whenever I do so, I get a error message saying the following:

mkdir: cannot create directory `/mnt/win': Permission denied

I am the only account and I am able to get updates and everything. Can someone point me in the right direction? I even went to File Browser and opened up the "mnt" folder and tried to use the "mkdir /win" command and got the same error message (only without the "/mnt" section). Thanks.


Regards,
Matthew[/QUOTE]

You don't have to create a directory under /mnt (it can be anywhere on your file system), also you have to use sudo cmd to create a directory outside your home directory. These set of commands should help you in mounting your Windows partition:
```

$ sudo mkdir /media/windows
(enter your password when it prompts for it)
$ sudo mount /dev/hda1 /media/windows -t nfts -o nls=utf,umask=0222
(assuming the win partition is on dev/hda1

```

S

---

### Post by agyeya on 2006-03-27
The only way you are going to mount it without a read only permission is by logging in as "root". That is my guess. 
And besides to listen to your songs, you would need to install the appropriate plugins as linux does not support mp3 by default. The plugins you can probably find in this forum itself.

Hope this answers your query.

---

### Post by IDipSkoalMint on 2006-03-27
Thank you for your quick reply, it's much appreciated. When I go through that, it tells me that it doesn't recognize the ntfs system:

mount: unknown filesystem type 'nfts'

I went to that directory, and the directory is empty.




I will include my GRUB file in the next part of this post, maybe that'll help you help me. I appreciate your patience, as I am a total newbie ;) ...

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]Thank you for your quick reply, it's much appreciated. When I go through that, it tells me that it doesn't recognize the ntfs system:

mount: unknown filesystem type 'nfts'

I went to that directory, and the directory is empty.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/QUOTE]

sorry my bad, nfts should have read ntfs...here's the updated mount command:
```

$ sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf,umask=0222

```
(you don't have to run the mkdir command again)

S

---

### Post by IDipSkoalMint on 2006-03-27
Now I get the following error message:

mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is mounted on /media/sda1

Believe me, I really do appreciate your patience.

Regards,
Matthew

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]Now I get the following error message:

mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is mounted on /media/sda1

Believe me, I really do appreciate your patience.

Regards,
Matthew[/QUOTE]
looks like Windows partition is auto mounted during boot, could you post the output of this command:
```

$ cat /etc/fstab

```

S

---

### Post by IDipSkoalMint on 2006-03-27
matthew@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks again.

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]matthew@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks again.[/QUOTE]
ok for now execute these two commands in order:
```

$ sudo unmount /media/sda1
$ sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
These set of commands should mount your windows partition and allow you to access it from /media/windows...keep in mind that you'll have to exec these commands every time you boot to access your win partition. To avoid doing it everytime you can modify you fstab file but I would recommend first going with manual mount approach and we can talk abt editing the fstab file sometime later.

S

---

### Post by IDipSkoalMint on 2006-03-27
I feel like a burden with all the help you're giving me, but I get the following error:

matthew@ubuntu:~$ sudo unmount /media/sda1
sudo: unmount: command not found

Thanks again.

---

### Post by aysiu on 2006-03-27
[QUOTE=IDipSkoalMint]I feel like a burden with all the help you're giving me, but I get the following error:

matthew@ubuntu:~$ sudo unmount /media/sda1
sudo: unmount: command not found

Thanks again.[/QUOTE] The command is **umount**, not **unmount**.

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]I feel like a burden with all the help you're giving me, but I get the following error:

matthew@ubuntu:~$ sudo unmount /media/sda1
sudo: unmount: command not found

Thanks again.[/QUOTE]
lol, either it's getting late or I've had way too much wine ;)...sorry once again my bad:
replace unmount with umount and you should be all set (hopefuly)!

S

---

### Post by RRS on 2006-03-27
"sudo umount.........."

No "n" in the spelling, no idea why though.

---

### Post by SkimWear on 2006-03-27
yeah i never got that either. but whatever, its the command. at least it doesnt trick me anymore :\

---

### Post by IDipSkoalMint on 2006-03-27
I would like to thank you for your help. I am now able to view my Windows files. Hopefully, given enough time and practice (I don't really have too much time to experiment), I'll be able to help someone out with their issues. Now those two commands are something I'll need to type each time I want to view my windows files or just the mount command? Also, if you could point me in the right direction to having it automatically mount it properly, that'd be great also. Thanks again for your time.

---

### Post by sn123 on 2006-03-27
[QUOTE=IDipSkoalMint]I would like to thank you for your help. I am now able to view my Windows files. Hopefully, given enough time and practice (I don't really have too much time to experiment), I'll be able to help someone out with their issues. Now those two commands are something I'll need to type each time I want to view my windows files or just the mount command? Also, if you could point me in the right direction to having it automatically mount it properly, that'd be great also. Thanks again for your time.[/QUOTE]
No problem at all we're here to please :). You'll have to manually unmount and mount (i.e both the commands) the partition everytime you boot into linux to access the win partition.

Now about automatically mounting it, you would need to modify the fstab file:
```

$ sudo cp /etc/fstab /etc/fstab.bak
(make a backup in case something blows up)
$ sudo gedit /etc/fstab
In the text editor, scroll down to the entry for **/dev/sda1**, find **defaults**
on the same line and replace defaults with **nls=utf8,umask=0222**
Save the file and reboot and you should be good to go (keep in mind that the windows partition in this case would be accessible at /media/sda1).

```

Cheers,
S

---

### Post by IDipSkoalMint on 2006-03-27
Thank you again. I seemed to successfully edit the file, so I'll find out on my next reboot. On a side note: in other forums I'm a member of (the other ones I tend to be much more on the "giving" side of things, so hopefully soon, I will be here as well), there's a way to give "rep points" to the members who have been extremely helpful. Is there any way I would be able to do that for you, since you've given me so much of your time? I'd buy you a beer or something, but I think "rep points" is all I really can do for now haha ;)

Regards,
Matthew

UPDATE: I restarted my computer and as you said, "sda1" shows my Windows files as I had hoped. One thing I noticed when it was running through the startup though, was that the "mounting local filesystems" step failed. Is that a bad thing or is it just due to the fact that I edited the FSTAB file?

---

### Post by sn123 on 2006-03-28
[QUOTE=IDipSkoalMint]Thank you again. I seemed to successfully edit the file, so I'll find out on my next reboot. On a side note: in other forums I'm a member of (the other ones I tend to be much more on the "giving" side of things, so hopefully soon, I will be here as well), there's a way to give "rep points" to the members who have been extremely helpful. Is there any way I would be able to do that for you, since you've given me so much of your time? I'd buy you a beer or something, but I think "rep points" is all I really can do for now haha ;)

Regards,
Matthew

UPDATE: I restarted my computer and as you said, "sda1" shows my Windows files as I had hoped. One thing I noticed when it was running through the startup though, was that the "mounting local filesystems" step failed. Is that a bad thing or is it just due to the fact that I edited the FSTAB file?[/QUOTE]

Not too sure about the both i.e. the rep points and the mounting filesystem failing. Try rebooting once again to see whether it was something temporary or you get the error every time. You can also try to revert back to the original fstab file and reboot again just to see how that goes or  wait till someone else can throw some more light on it...I am sorry I can only help this much tonight/morning cause it's getting late in my part of the world.

S

---

### Post by IDipSkoalMint on 2006-03-28
I rebooted and still got the same "failed" message. There doesn't seem to be any issues with my O/S, and I can view my Windows files (which was the reason for this post in the first place), so unless someone knows of an issue that can be caused by this step failing, I don't see how it would really hurt. Thanks again for all your help.

Regards,
Matthew

---

### Post by confused57 on 2006-03-28
You've received some excellent advice, but this link may help(if you're not
already aware of it):

[http://ubuntuguide.squarecows.com/doku.php#windows](http://ubuntuguide.squarecows.com/doku.php#windows)

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=confused57]You've received some excellent advice, but this link may help(if you're not
already aware of it):

[http://ubuntuguide.squarecows.com/doku.php#windows](http://ubuntuguide.squarecows.com/doku.php#windows)[/QUOTE]

Thank you very much. I wasn't aware of that. I don't have time to read it now, but I'm sure when I get some free time I'll take a look at that. I really do appreciate everyone's help and patience.

UPDATE: For anyone who's interested in playing their iTunes music in Linux, once you've got your Windows partition mounted, I installed a program called "Quod Libet" and imported my files easily. I've got them playing as we speak. Anyway, just thought I'd share that little bit of information.

---

### Post by adnaann on 2006-04-25
well mate 

 i guess u shud use 
 umount instead of unomunt...

---

