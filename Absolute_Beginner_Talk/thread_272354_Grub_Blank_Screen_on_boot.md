---
title: "Grub Blank Screen on boot"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ,gds on 2006-10-06
Hi

I recently installed Ubuntu on to my PC which already had WinXP pro on it.

All went well.

As I use Windows XP mostly (for now until I learn Ubuntu) I wanted to make it the default OS on the Grub boot sequence.  So on these forums I found a useful tool called GrubEd which allows you to edit Grub.

I changed the default to Windows XP, and all worked. I then changed other settings to see, such as splash screen etc.  Didn't like that so undid it with GrubEd.  Now when I boot my PC no grub menu of OS choices comes up (though time countdown was set to 5), just a blank GNU Grub screen.  I have no idea what to do! How can I boot up in to Ubuntu to try and fix this?

Please help!

I am now using the Ubuntu CD to type this message.

Thanks

---

### Post by Kateikyoushi on 2006-10-06
You can restore grub by following [this guide.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by ,gds on 2006-10-06
Thanks

I had actually just found this post and tried this up until "quit" command (just after this: finally exit the grub shell).

All these commands worked.

But when I restarted from the LiveCD the same blank GRUB screen (GRUB Shell) came up.

---

### Post by ,gds on 2006-10-06
See:
Copy from grub shell:
grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by ,gds on 2006-10-06
btw just noticed - you are in Tokyo - me too! :)

---

### Post by Kateikyoushi on 2006-10-06
Did you create a backup of your grub menu.lst before you edited it ?
You could rename it to grub.lst and it would work like before.

---

### Post by ,gds on 2006-10-06
How would I do that/find a backup and make it live? I am using the Live CD.

I believe GrubEd makes a backup - that is what I used to edit grub.  Didn't do it manually.

---

### Post by Kateikyoushi on 2006-10-06
Then I hope it created a backup in the /boot/grub folder.
You could check it from live cd.

---

### Post by ,gds on 2006-10-06
Sorry Kateikyoushi - how would I find teh backup if there is one)? I am a 1 day old UNIX user, so don't know the required commands - but I am good at copying and pasting. :)

Thansk for your help BTW.
btw. I am fairly sure it does create a backup - because it has a restore backup 
option (i'm fairly sure) in GrubEd - but as I can't boot up in to Ubunto - I can't use GrubEd restore :)

---

### Post by Kateikyoushi on 2006-10-06
Boot from live cd and from places check your hard drives.
There is a /boot/grub folder on your ubuntu partition, menu.lst file should be in it.

---

### Post by ,gds on 2006-10-06
I am in the Live CD...It can't seem to mount to the drive "Unable to mount the selected volume"

---

### Post by ,gds on 2006-10-06
The strange thing, in the Grub Shell - I do
grub> find /boot/grub/stage1
(hd0,1)

And it seems to find it.

But in places - it doesn't mount

---

### Post by Kateikyoushi on 2006-10-06
Copy this to a terminal.

```
fdisk -l
```

---

### Post by ,gds on 2006-10-06
Ok, done
> ubuntu@ubuntu:/$ fdisk -l
ubuntu@ubuntu:/$


---

### Post by Kateikyoushi on 2006-10-06
Sorry -_-;;

```
sudo fdisk -l
```

---

### Post by ,gds on 2006-10-06
the first thing I did - fdisk - didn't jsut format my HD did it? just looks like formatdisk :)

---

### Post by ,gds on 2006-10-06
Ok, see here:
>  sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81923436    7  HPFS/NTFS
/dev/sda2   *       10200       11851    13269690   83  Linux
/dev/sda3           11852       12161     2490075   82  Linux swap / Solaris
ubuntu@ubuntu:/$


---

### Post by Kateikyoushi on 2006-10-06
No the -l lists your partition table, so we can mount your hard drive.

---

### Post by Kateikyoushi on 2006-10-06
Okay lets try to mount it.

```
sudo mount -t ext3 /dev/sda2 /mnt
```

---

### Post by Tomosaur on 2006-10-06
Hi there, tricky problem you've got. I wrote GrubEd so obviously if it's causing you problems I'd be concerned. This is the first problem of this type  I know about. Please could you post the output of:

```

ls /boot/grub/

```

and also the contents of the following file:
/boot/grub/menu.lst

If you're using the liveCD you should be able to open that file in a text editor and paste the contents here.

---

### Post by ,gds on 2006-10-06
> **Kateikyoushi said:**
> Okay lets try to mount it.

```
sudo mount -t ext3 /dev/sda2 /mnt
```
That worked!
Now?
:)

---

### Post by ,gds on 2006-10-06
> **Tomosaur said:**
> Hi there, tricky problem you've got. I wrote GrubEd so obviously if it's causing you problems I'd be concerned. This is the first problem of this type  I know about. Please could you post the output of:

```

ls /boot/grub/

```

and also the contents of the following file:
/boot/grub/menu.lst

If you're using the liveCD you should be able to open that file in a text editor and paste the contents here.
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda2 /mnt
ubuntu@ubuntu:/$ ls /boot/grub/
ls: /boot/grub/: No such file or directory
ubuntu@ubuntu:/$

---

### Post by Kateikyoushi on 2006-10-06
Now do what the Tomosaur wrote.
We need to see the files in your /boot/grub folder

```
ls /mnt/boot/grub
```

---

### Post by ,gds on 2006-10-06
ubuntu@ubuntu:/$ ls /mnt/boot/grub
default        fat_stage1_5  menu.lst        reiserfs_stage1_5  xfs_stage1_5
device.map     images        menu.lst~       stage1
e2fs_stage1_5  jfs_stage1_5  minix_stage1_5  stage2
ubuntu@ubuntu:/$

---

### Post by Tomosaur on 2006-10-06
Alright, looks like you have a save of menu.lst. Try this:
```

sudo cp /mnt/boot/grub/menu.lst~ /mnt/boot/grub/menu.lst

```

But before you reboot,let us see the contents of the file.

---

### Post by ,gds on 2006-10-06
How would I view it?

---

### Post by Tomosaur on 2006-10-06
In the terminal, type:
```

gedit /mnt/boot/grub/menu.lst

```

---

### Post by ,gds on 2006-10-06
This is it:
> gedit /mnt/boot/grub/menu.lst
#splashimage /boot/grub/images/GrEdSplash.xpm.gz

Strange, I know it used to have a lot more!

and menu.lst~ is
> 
gedit /mnt/boot/grub/menu.lst~

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
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

### Post by Tomosaur on 2006-10-06
Very strange. It looks like renaming menu.lst~ to menu.lst will fix your problem, but now I'm worried there's a big bug with GrubEd. Try overwriting menu.lst with menu.lst~ and see if the problem is fixed. Don't delete menu.lst~, just make a copy of it and rename it to remove the ~.

---

### Post by ,gds on 2006-10-06
The main reason I started on this venture was to make windows XP the default OS.

Can I modify the restored menu.lst to do this?

And how?

 
:)

---

### Post by ,gds on 2006-10-06
> **Tomosaur said:**
> Very strange. It looks like renaming menu.lst~ to menu.lst will fix your problem, but now I'm worried there's a big bug with GrubEd. Try overwriting menu.lst with menu.lst~ and see if the problem is fixed. Don't delete menu.lst~, just make a copy of it and rename it to remove the ~.
Done!

---

### Post by Tomosaur on 2006-10-06
Did it work? If it did, could you please try and remember exactly what operations you used in GrubEd?

---

### Post by ,gds on 2006-10-06
before I reboot can I edit the file and change default boot to Windows?

seeing I have terminal open etc.

---

### Post by Kateikyoushi on 2006-10-06
> **,gds said:**
> The main reason I started on this venture was to make windows XP the default OS.

Can I modify the restored menu.lst to do this?

And how?

 
:)

Yes you can make xp the default.

sudo gedit /mnt/boot/grub/menu.lst

change the

dafault 0

to default 3

---

### Post by ,gds on 2006-10-06
thanks will try now

---

### Post by ,gds on 2006-10-06
That worked thanks, but looks like I need to change it to 4 not 3 - 3 is the line "other operatirn systems" or whatever.

---

### Post by Kateikyoushi on 2006-10-06
Yes, you are right I did not notice that line.

You can change it by booting ubuntu and tying in terminal.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by ,gds on 2006-10-06
All works fine now! changing to 4 fixed it :)
Thanks much Keteikyoushi - thanks so much! btw the weather in Tokyo sucks today doesn't it! :) too much rain.

---

### Post by Tomosaur on 2006-10-06
If you intend to use GrubEd again, remember to make a proper backup next time :P The backup you had was just a 'feature' of many text editing programs, which is easily turned off.

---

### Post by ,gds on 2006-10-06
> **Tomosaur said:**
> Did it work? If it did, could you please try and remember exactly what operations you used in GrubEd?
Hi, thank you so much too Tomosaur! much appreciated.

I was playing around in GumpEd to see what was changeable.  I didn't change much though.  I changed the default, time count to 5, also tried the splash.  

That all worked.

But when I went to undo splash change, and change the time again, I noticed it saying things like ": seconds", when it displayed current settings at the top of the dialog (ie: 5 seconds).  This worried me..and later when I rebooted that is when I went in to gump shell and not the gump menu.

---

### Post by Tomosaur on 2006-10-06
Hmm, I can't seem to duplicate this problem at all. If it happens again, please let me know via the GrubEd thread (check the link in my sig), or through a private message.

---

### Post by ,gds on 2006-10-06
Oh oh, new problem - may as well keep it in same thread as it is related.

Now, when I leave it on default and it times out to 0 it just reloads the grub menu choice. 

Also when I press enter on the Windows default option in Grub menum, when the timer ticks down that also just reloads the Grub menu.. ie. Windows isn't loading.

This problem doesn't happen for option 0 - Ubunto.  Not sure about the other options - memory test etc.

Ubuntu doesn't want me to go back to Windows :)

---

### Post by ,gds on 2006-10-06
This is the content of menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
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

### Post by Tomosaur on 2006-10-06
Nope, that's an ordinary line which Windows installations require, since Windows has its own bootloader.

---

### Post by ,gds on 2006-10-06
Ok,that's not the problem then :)

Any idea what is?

---

### Post by ,gds on 2006-10-06
Any ideas why Windows doesn't load when it is selected in the the Grub menu? Just the Grub menu re-loads when windows is selected.

See menu.lst code posted earlier.

---

### Post by ,gds on 2006-10-06
I've just noticed the following text comes up when selecting the "Windows" option on Grub.

Booting 'Microsoft Windows XP Professional'

root (hd0,0)
filesystem type unkown, partition type 0x7
savedefault
makeactive
chainloader +1

Grub loading Stage2

Then nothing further seems to happen, and it comes back to the Grub boot selection menu.

Hope this helps with identifying and resolving the problem.

---

### Post by IoCaster on 2006-10-06
You could try:

```
title Microsoft Windows XP Professional
root (hd0,0)----->change to rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

See if that helps.

---

