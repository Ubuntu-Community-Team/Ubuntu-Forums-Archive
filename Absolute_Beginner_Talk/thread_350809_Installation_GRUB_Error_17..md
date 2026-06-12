---
title: "Installation GRUB Error 17."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Jnex26 on 2007-02-01
Hi All, 

I'm trying to install Ubuntu on my desktop PC, I have previously experimented with linux (REDHAT) before however I've never received this problem before. 

I can install perfectly I get no errors upon installing. However when I first boot i get the error GRUB error 17. 

I am attempting to dual boot my boot sector resides on hdb this is the NTFS disk with WINXP on it. 

The disk I am installing onto is sda (Note:- This used to be a ICHR5 Raid array but Ubuntu does not see the array it only see's the individual disks, any clues how to get it to see it as a RAID-0 Array.) 

I don't even get a boot list I just get a error stating GRUB Error 17.

Anyone get any Ideas.

---

### Post by Scarlett on 2007-02-01
I was getting that error after trying to install Debian from the Windows executable.  I don't know what it means but I ended up doing a fresh install with an "alternate" cd and it worked fine (after a little fiddling).  I'm certainly not the best person to ask but if you don't want to do a reinstall maybe try using a live Gparted cd first and see if you can mount it somewhere accessible...?

---

### Post by glabouni on 2007-02-01
grub error 17 means:
> 17 : Cannot mount selected partition 

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB

more info about grub : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by jd65pl on 2007-02-01
Try to recover grub using this method, if it doesn't work post back.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Ewat on 2007-02-01
I tried my first install of Ubuntu 6.05 last night and got the Error 17 message, too:

"GRUB Loading Stagel 1.5, please wait...Error 17"

When I reboot (manually turn the machine off), I get "Authentication of system services failed. Press ESC to Resume." Then it gives me the Grub error and freezes.

My status is that of something less than a novice. I unable to recognize half of what you guys are talking, but I am willing to try.

I used the second option to let Ubuntu partition my 40 Gg hard drive, with WinXP, in a IBM T40 notebook, which looks something like this:

hda1        ntfs           34.30 GB        5.76              29.04
unallocated                 6.92 MB
hda2        ext3            2.79 GB        1.77 GB          1.01 GB  boot
hda3        extended   164.73 MB
hda5        extended   164.73 MB

I can't tell you why, but for some reason this set up doesn't seem right to me.  In addition, I don't see the "/" that is mentioned in some of these threads.

Somebody, please help me through this. Given my lack of skill, what is the best thing to do: Should I start over again? Get Grub software?

Somebody have mercy and help this poor novice in a simple way.

---

### Post by dannyboy79 on 2007-02-01
well I don't know what ubuntu did here but something doesn't make sense with what you are telling me. first, do you know how to boot your computer to the live cd? if you do than do that. once you get in you'll need to find out what sudo fdisk -l tells you. it should be something like hda1 is NTFS 34.3GB, hda2 is ext3 and is /, it's 2.79GB in size, blah blah blah. but that wouldn't be possible because ubuntu needs more than 5gb for it's root partition. if you have a 40gb hdd and you want to install ubuntu, you should've really made your ntfs partition smaller and left at least 10gb unalloacated using something like partition magic or whatnot. i don't know if the ubuntu installer can shrink ntfs, I wouldn't count on it. after you know what fdisk -l tells you, you can then double check your /boot/grub/menu.lst file and make sure that the correct partition is being called out for your root partition. it probably would be best if you start over since you even stated yourself that you're a little inexperienced here. when you start over, here is a great tutorial for installing linux after you already have windows nt installed. i know you may not have windows nt installed but the tutorial should be the same for winxp. [http://tldp.org/HOWTO/Linux+WinNT-3.html](http://tldp.org/HOWTO/Linux+WinNT-3.html)

good luck and stick with it, linux is fun!

---

### Post by linux_kid on 2007-02-01
If you are getting that message, chances are you have recently installed Ubuntu.  Just reinstall.  Simple as that.

If you have too much important data, just listen to the smarter people in this forum... :)

---

### Post by Ewat on 2007-02-01
To say that I am a little experienced is a high compliment, compared to what I see on these forums. So, many thanks for dumbing down the information and help, some of which is still Latin to me.

Anyway, thank you for your response and assistance. I will work on righting the partitions and will try to reinstall Ubuntu and follow the tutorial. Is there a recommended partition size for a 40 gb hard drive with WinXP and Ubuntu? 

Is there a specific process for uninstalling Ubuntu? Or should I just overwrite it with the CD?

Again, I appreciate the response and will try to wade through this.

---

### Post by dannyboy79 on 2007-02-01
> **linux_kid said:**
> If you are getting that message, chances are you have recently installed Ubuntu.  Just reinstall.  Simple as that.

If you have too much important data, just listen to the smarter people in this forum... :)


if you're going to try to help than it would be good for all if you provide help instead of just random comments. He is dual booting so your idea isn't really applicable.

---

### Post by linux_kid on 2007-02-01
dannyboy79: If you are dual booting and come with that error, the simplist way is to reinstall ubuntu.  I had to do it about 4 months ago with the same error and I dual-boot.

And, Ewat, I have a 40GB HDD an my partition table is similar to this

Windows: 21GB
Linux: 6GB
Swap: 800MB
Restore: 8GB

---

### Post by dannyboy79 on 2007-02-01
> **Ewat said:**
> To say that I am a little experienced is a high compliment, compared to what I see on these forums. So, many thanks for dumbing down the information and help, some of which is still Latin to me.

Anyway, thank you for your response and assistance. I will work on righting the partitions and will try to reinstall Ubuntu and follow the tutorial. Is there a recommended partition size for a 40 gb hard drive with WinXP and Ubuntu? 

Is there a specific process for uninstalling Ubuntu? Or should I just overwrite it with the CD?

Again, I appreciate the response and will try to wade through this.


well, like I said, just forget about booting to a live cd and trying to figure out your partition scheme. if I were you I would just follow that tutorial except now you can simply delete all the parititon that "AREN'T" NTFS because those were created by ubuntu install and it doesn't appear that it went well. so when you use the floppy to resize your 40 gb partition you should allow at least 10gb for your ubuntu install. you'll want to create a / partition as well as a swap partition. are you aware of how much disk space your hard drive has left CURRENTLY right now. (that's speaking if you didn't just try to install ubuntu a little but ago) so for example: if your computer has a 40gb hard drive and after it's formatted ntfs, it really is only 36gb for example, then after you installled winxp and some of your apps you when you look at the properties under windows explorer it states that you have 20 gb left, than what you should do is shrink your ntfs partition down so that you leave a little breathing room on ntfs and have about 10 to 15gb for your ubuntu partition. it's going to be up to you but you could create a / parititon, a /home partition and a swap partition and still have them all be primary partitions. i think you can create 4 primaries. otherwise you might have to create an extended partition and put your /home on it if you chose to create a seperate partition for your /home. if you do chose to have a /home parititon, then make it be whatever is left over after you make your / parititon be min 8 gig. this will leave space for installing apps, for aptitude cache, your /var and /tmp get filled up with crap. so it sounds like it would be 26gb for winxp, 8-10gb for /, 1-1.5gb for swap, remaining is /home. that should do it. good luck

---

### Post by glabouni on 2007-02-01
linux_kid, seems to me you're confusing simple and easy.
easiest way is to reinstall (assuming if it fixes anything at all), simpliest is to fix grub.

---

### Post by dannyboy79 on 2007-02-01
> **linux_kid said:**
> dannyboy79: If you are dual booting and come with that error, the simplist way is to reinstall ubuntu.  I had to do it about 4 months ago with the same error and I dual-boot.

And, Ewat, I have a 40GB HDD an my partition table is similar to this

Windows: 21GB
Linux: 6GB
Swap: 800MB
Restore: 8GB


sorry, I was unaware that the installer was smart enough to shrink a ntfs partition that contained windows and then create the partition scheme one would want and then install ubuntu. i don't dual boot so I was unaware of that.

---

### Post by linux_kid on 2007-02-01
You don't need to repartiton to reinstall.

Sorry Ewat, I did confuse simple and easy :oops:

---

### Post by Jnex26 on 2007-02-01
Hi again. 

Well I've tried everything i can think of and I'm still stuck. Although I've got a little further now. 

I've reinstalled about 9 times now. pointless same error everytime. 

The stage I'm at now... instead of Immediately getting error 17 I get a menu, 

I did this by removing the boot flag from my NTFS partition then setting in bios the DISK sda as the primary boot disk which also happens to be my Linux disk. then running the fix as descibed earlier by mounting the sda1 to /mnt/root. 

Now I've got the menu I feel i'm getting a little somewhere however trying to boot into Ubuntu gives me error 17 and booting into windows just gives me a screen telling me i'm getting a grub error 18. although I can do a fix MBR on that disk without messing up the sda1 mbr as windows can't see that disk in setup, BTW I'm not the type of guy that gives up easily on these type of things I'll get this working. 

many way to help you understand my disk configuration here is a screen grab of a fdisk -l 

```

root@ubuntu:~# fdisk -l

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       36481   293033601    7  HPFS/NTFS

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4314    34652173+  83  Linux
/dev/sda2            4315        4500     1494045    5  Extended
/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/hdf: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       19929   160079661    7  HPFS/NTFS

```

Ok disk hdb1 is pata (why i don't have a hda :- because the previous hda disk died and i was already booting off the d drive in windows)

Disk's sda and sdb will be my linux disks, I used to have them in a RAID-0 Configuration but ubuntu did not see them as a raid array rather just a individual configuration any ideas how to fix it will be appreciated. I have sda set as my master boot disk in bios atm.

Disk hde and hdf are connected to a Highpint intergrated raid controller with no raid defined. 

Here is my grub device.map 

```

(hd0)   /dev/hdb
(hd1)   /dev/hde
(hd2)   /dev/hdf
(hd3)   /dev/sda
(hd4)   /dev/sdb

```

And finally here is my menu.lst 

```

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=41710711-c493-4e28-b4b8-9944c75d9f40 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd3,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd3,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd3,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Can anyone give me a clue as to why linux won't boot.

---

### Post by Ewat on 2007-02-01
Guys,

Is there are specific process to uninstall Ubuntu?

Should I use Gparted to delete the program in each partition before I re-partition. Or am I making much-ado-about nothing, just run the CD again?

I am getting a little frustrated at this point, and I haven't even installed the software. Please help. Remember, I have no experience.

Thank you.

---

### Post by confused57 on 2007-02-01
I'm not sure I understand your setup, but do you get a grub menu(and can boot Windows) when you set your hdb(hd0) as the first boot hard drive?  If I understand correctly, that's your Window's hard drive.

---

### Post by Jnex26 on 2007-02-02
> **confused57 said:**
> I'm not sure I understand your setup, but do you get a grub menu(and can boot Windows) when you set your hdb(hd0) as the first boot hard drive?  If I understand correctly, that's your Window's hard drive.

hdb(hd0) is my windows drive. 

if i boot from sda I get a grub menu, selecting windows gives me a grub error 18


if a boot from hdb I get into windows.

---

### Post by confused57 on 2007-02-02
> **Jnex26 said:**
> hdb(hd0) is my windows drive. 

if i boot from sda I get a grub menu, selecting windows gives me a grub error 18


if a boot from hdb I get into windows.
Just logged in to the forums and saw your reply, I may be able to give you some suggestions to try.
I assume you're not able to boot Ubuntu or Windows from your grub menu when you boot first to sda(Ubuntu) drive.  If that is the case, then at the grub menu, make sure that your Ubuntu entry is highlighted, press "e" to edit, then change root (hd3,0) to root (hd0,0) & try to boot with this change.  If this works, the change is only temporary, you need to make it permanent in your /boot/grub/menu.lst.  If you are able to boot Ubuntu with your current setup of root (hd3,0), with your sda set as your first hard drive to boot to, then you obviously wouldn't need to do what I suggested.

If my assumptions are correct and you needed to change root to (hd0,0) in order to boot Ubuntu, you can add an entry to boot Windows.  Set your Windows drive as the second hard drive boot device, then add an entry similar to this:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I'm not going to be able to help anymore tonight, have to "hit the hay"(go to bed)...but maybe this will give you some things to try.

---

### Post by Jnex26 on 2007-02-02
> **confused57 said:**
> Just logged in to the forums and saw your reply, I may be able to give you some suggestions to try.
I assume you're not able to boot Ubuntu or Windows from your grub menu when you boot first to sda(Ubuntu) drive.  If that is the case, then at the grub menu, make sure that your Ubuntu entry is highlighted, press "e" to edit, then change root (hd3,0) to root (hd0,0) & try to boot with this change.  If this works, the change is only temporary, you need to make it permanent in your /boot/grub/menu.lst.  If you are able to boot Ubuntu with your current setup of root (hd3,0), with your sda set as your first hard drive to boot to, then you obviously wouldn't need to do what I suggested.

If my assumptions are correct and you needed to change root to (hd0,0) in order to boot Ubuntu, you can add an entry to boot Windows.  Set your Windows drive as the second hard drive boot device, then add an entry similar to this:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I'm not going to be able to help anymore tonight, have to "hit the hay"(go to bed)...but maybe this will give you some things to try.


Thanks for that it worked I can now dual boot yay.... 

Thanks again your help is much appreciated.

---

### Post by dannyboy79 on 2007-02-02
> **Jnex26 said:**
> Thanks for that it worked I can now dual boot yay.... 

Thanks again your help is much appreciated.


can you please be specific as to what you did to solve this? what hard drive is listed as boot drive in bios, which one is second. then please list what you did with grub. please post your applicable menu.lst lines like the #kopt and #groot lines as well as the actual grub entry lines for booting the different os's. thank you. is would be good in the future to put the solution instead of just say, "yeah, I got it". i can kind of understand why you put this because the previous thread lists a possible solution but it has more than one and some assumptions so I can't really figure out how to solve my issue unless you're specific as to how you solved this. thank you.

---

### Post by confused57 on 2007-02-02
> **Jnex26 said:**
> Thanks for that it worked I can now dual boot yay.... 

Thanks again your help is much appreciated.

Glad to have helped...I didn't want to keep asking you questions about your setup & waiting for a reply, thus I had to make some assumptions(based on what I'd read in your previous posts), & if they were true, then offer a solution based on them.

---

