---
title: "Error 17 after I formatted an extra parition"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by shenanigan on 2007-11-21
Hi I tried to dual boot vista and ubuntu 7.10 in one SATA harddisk. I was planning on having 2 partitions for my vista (for system drive and back-up drive) and 2 partitions for ubuntu (root and swap). 
After the installation of my vista I didn't format my back-up drive and immediately installed ubuntu. After some time I noticed that I still haven't formatted the back-up drive for my vista. Then after formatting it as NTFS........The GRUB error 17 appears and I cannot boot both my vista and my ubuntu. My ubuntu files are crucial especially my evolution files. Help!!! I'm new and I would appreciate your help. Thanks in advance :confused:

______________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/000hwyt9[/IMG]
SAD

---

### Post by bumanie on 2007-11-21
Waht did you use to format your drive? Would you be able to post your drive partitions. It would be helpful to know which partitions have which OS and which partitions are backup etc.
What did you use to partition your disc with. A live cd, gparted or something else?

---

### Post by wolfen69 on 2007-11-22
when you formatted the backup drive you probably overwrote GRUB. just do a quick search on the forums for "repair GRUB"  and you'll have it done in no time.

---

### Post by namanbagga on 2007-11-22
Try [this]("http://www.namanb.com/2007/11/when-computers-dont-boot.html") to reinstall GRUB.I'm sure it will work

---

### Post by Presto123 on 2007-11-22
I would follow the advise posted above. I did a search on Google and everything shows up as a Grub problem.

---

### Post by shenanigan on 2007-11-22
> **bumanie said:**
> Waht did you use to format your drive? Would you be able to post your drive partitions. It would be helpful to know which partitions have which OS and which partitions are backup etc.
What did you use to partition your disc with. A live cd, gparted or something else?

Thanks for the immediate response. Below are my partitions:
sda1 - Windows Vista System Drive (NTFS - 20GB)
sda2 - Back-up (NTFS - 20GB) - The one I forgot to format at the beginning of my installation.
sda3 - Ubuntu 7.10 (ext3 - 39GB)
sda4 - swap (1GB)

After using this for quite some time I formatted the sda2 using Vista in Computer Management. M format might have caused an error in my GRUB. :(

_________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/000cfbp7[/IMG]
SHOCKED

---

### Post by Presto123 on 2007-11-22
Also, I'm confused. Are you trying to run Ubuntu off of your NTFS format?

Another link for you:

[http://forums.techguy.org/unix-linux/579008-solved-grub-error-17-after.html](http://forums.techguy.org/unix-linux/579008-solved-grub-error-17-after.html)

*EDIT* Never mind the question above.

---

### Post by bumanie on 2007-11-22
I gather you used vista to do the format. I am assuming that this has overwritten your grub. what you need to do is boot into your gutsy live cd and bring up terminal  ----- Applications --> TerminalIn terminal type 
sudo grub --> enter  This gets you into the grub shell. Then type 
grub> find /boot/grub/stage1    This will give an output of (hd?,?) where the 1st ? is your hdd as seen by grub and the 2nd ? is the partition grub is installed on. Then type
grub> root (hd?,?)   replacing the ? with the numbers from your output. From the list you provided, it should be (hd0,2).  then type 
grub> setup (hd?)  The 1st number from your output (in your case it should be 0) then type
grub> quit
all going well, grub should be restored.

---

### Post by namanbagga on 2007-11-22
Everything is explained in the above link.You should use something like gparted to format any partition be it NTFS of ext3 or any other because Microsoft can't tolerate the presence of another OS on a computer

---

### Post by shenanigan on 2007-11-22
Thanks a bunch **bumanie, Presto123 and namanbagga**. I tried to install GRUB to my (hd0,2) and I am now able to boot from my Windows Vista. Sadly a new problem arised, "Error 17 : Cannot mount selected partition" When I select the Ubuntu 7.10 Generic in the boot selection menu and I still can't boot my Ubuntu OS. :(
___________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001z65kp[/IMG]
DISMAYED AND ANNOYED

---

### Post by bumanie on 2007-11-22
Are you sure you have not inadvertently removed your gutsy install?
Could you please boot with live cd again and in terminal type sudo fdisk -lu and post the result. I am not an expert, but if I cannot make sense of things, someone else on this forum probably can.
It also may be useful to also do a sudo gedit /boot/grub/menu.lst and post its results also.
Be aptient, someone will work things out.

---

### Post by shenanigan on 2007-11-22
> **namanbagga said:**
> Everything is explained in the above link.You should use something like gparted to format any partition be it NTFS of ext3 or any other because Microsoft can't tolerate the presence of another OS on a computer
Thanks namanbagga I'll keep that in mind :D
___________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001ys76x[/IMG]
OPTIMISTIC

---

### Post by Presto123 on 2007-11-22
> **namanbagga said:**
> Everything is explained in the above link.You should use something like gparted to format any partition be it NTFS of ext3 or any other because Microsoft can't tolerate the presence of another OS on a computer

Yeah...if it were psychology, I would say that Microsoft has an inferiority complex. 

If it were a guy it would be the first person in line for the new biggest truck...if you get what I'm saying ;)

---

### Post by Presto123 on 2007-11-22
On that link I posted, take a look at comments 10 through 13 and see if that makes sense.

I am going to go into my grub file and see how it looks before I move on. I only have Ubuntu on this computer, but I might be able to figure something out.

On that page it talks about having an "unknown" partition. I get that on my system, but it is my swap file, so, I wouldn't try formatting them.

Since you have it working on one part, use this command:

```
sudo grub
```

Then:

```
geometry (hd0)
```

Post that, maybe someone can help with it further. JUST DON'T MESS WITH IT yet.

---

### Post by bumanie on 2007-11-22
Shenanigan, I have to go now, but please post those things I suggested. If your thread is not marked solved when I return, I will have a look at your output and see if I can help. I have to go out for 2-3 hours, hopefully someone can help you before then. Good luck.

---

### Post by shenanigan on 2007-11-22
> **bumanie said:**
> Are you sure you have not inadvertently removed your gutsy install?
Could you please boot with live cd again and in terminal type sudo fdisk -lu and post the result. I am not an expert, but if I cannot make sense of things, someone else on this forum probably can.
It also may be useful to also do a sudo gedit /boot/grub/menu.lst and post its results also.
Be aptient, someone will work things out.
Bumanie here is what I got from **sudo fdisk -lu**:
__________________________________________________
Disk /dev/sda: 81.9 GB, 81964302336 bytes

255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors

Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *        2048    40962047    20480000    7  HPFS/NTFS

/dev/sda2        40962048    79953919    19495936    f  W95 Ext'd (LBA)

/dev/sda3        79955505   158079599    39062047+  83  Linux

/dev/sda4       158079600   160071659      996030   82  Linux swap / Solaris

/dev/sda5        40964096    79953919    19494912    7  HPFS/NTFS
____________________________________________________

And here is what I got from my **/boot/grub/menu.lst**:
____________________________________________________
# menu.lst - See: grub(8), info grub, update-grub(8)

#            grub-install(8), grub-floppy(8),

#            grub-md5-crypt, /usr/share/doc/grub

#            and /usr/share/doc/grub-doc/.



## default num

# Set the default entry to the entry number NUM. Numbering starts from 0, and

# the entry number 0 is the default if the command is not used.

#

# You can specify 'saved' instead of a number. In this case, the default
entry

# is the entry saved with the command 'savedefault'.

# WARNING: If you are using dmraid do not use 'savedefault' or your

# array will desync and will not let you boot your system.

default                0



## timeout sec

# Set a timeout, in SEC seconds, before automatically booting the default
entry

# (normally the first entry defined).

timeout                10



## hiddenmenu

# Hides the menu by default (press ESC to see the menu)

#hiddenmenu



# Pretty colours

#color cyan/blue white/blue



## password ['--md5'] passwd

# If used in the first section of a menu file, disable all interactive
editing

# control (menu entry editor and command-line)  and entries protected by the

# command 'lock'

# e.g. password topsecret

#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/

# password topsecret



#

# examples

#

# title                Windows 95/98/NT/2000

# root                (hd0,0)

# makeactive

# chainloader        +1

#

# title                Linux

# root                (hd0,1)

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

# kopt=root=UUID=5fff869b-9879-4040-b075-2c459fbfa19a ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



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



## should update-grub lock old automagic boot options

## e.g. lockold=false

##      lockold=true

# lockold=false



## Xen hypervisor options to use with the default Xen boot option

# xenhopt=



## Xen Linux kernel options to use with the default Xen boot option

# xenkopt=console=tty0



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



## should update-grub add savedefault to the default options

## can be true or false

# savedefault=false



## ## End Default Options ##



title                Ubuntu 7.10, kernel 2.6.22-14-generic

root                (hd0,1)

kernel                /boot/vmlinuz-2.6.22-14-generic
root=UUID=5fff869b-9879-4040-b075-2c459fbfa19a ro quiet splash

initrd                /boot/initrd.img-2.6.22-14-generic

quiet



title                Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root                (hd0,1)

kernel                /boot/vmlinuz-2.6.22-14-generic
root=UUID=5fff869b-9879-4040-b075-2c459fbfa19a ro single

initrd                /boot/initrd.img-2.6.22-14-generic



title                Ubuntu 7.10, memtest86+

root                (hd0,1)

kernel                /boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title                Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title                Windows Vista/Longhorn (loader)

root                (hd0,0)

savedefault

makeactive

chainloader        +1
___________________________________________________________________
Sorry if it was too long.....:biggrin: I'll be patient, coz I need my files in Ubuntu so much.
________________________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001z7p7a[/IMG]
RELAXED

---

### Post by shenanigan on 2007-11-22
I understand **bumanie**, I hope I resolve this too, thanks for the help.
________________________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001zqgkk[/IMG]
THANKFUL

---

### Post by bitterbug on 2007-11-22
I think, from looking at your partitions, that you just need to change the root in this section: ```
title Ubuntu 7.10, kernel 2.6.22-14-generic

root (hd0,1)

kernel /boot/vmlinuz-2.6.22-14-generic
root=UUID=5fff869b-9879-4040-b075-2c459fbfa19a ro quiet splash

initrd /boot/initrd.img-2.6.22-14-generic

quiet
```

Try making it ```
root (hd0,2)
```

If I understand the way grub works, 0,0 will be the first partition (vista), 0,1 is your second, and 0,2 will be the third (ubuntu).

I've only needed to edit my grub config when making bootable USB drives, so I might be off, but give it a try :)

At your boot menu just type E to edit the select and you can test the change in grub on the fly.

---

### Post by shenanigan on 2007-11-22
I have observed in my menu.lst that the root of my ubuntu system is (hd0,1). It is supposed to be (hd0,2) right? I tried to edit and save my menu.lst in my live CD but it states that it is only read-ony, thus I cannot change it :(.
______________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001zk4tc[/IMG]
STRESSED

---

### Post by bumanie on 2007-11-22
Hi shenanigan, 
I am back for a couple of minutes. As you cannot boot into ubuntu, I would suggest you download super grub disk, it may do either of two things.
1) If you are lucky it might restore grub for you or
2) It may allow to 'force' boot into ubuntu
I agree with bitterbug, your grub menu.lst looks wrong according to the way your partitions are set out. Before you alter anything, you should backup your present grub menu.lst. In terminal type
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
I will check some more things out and get back to you when I am able to, just make sure you backup before doing anything.

---

### Post by shenanigan on 2007-11-22
Thanks for the advice **bitterbug** You guys certainly know how to make a noob feel welcomed. I can boot to my ubuntu now, but is there a way to save the current settings I made (hd0,2)? Coz everytime I boot I still need to press E, change the boot partition and press B to boot to my ubuntu.
___________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001xppfk[/IMG]
HAPPY

---

### Post by bumanie on 2007-11-22
Now that you can get into ubuntu, you should be able edit menu.lst via terminal and save it. As I said before, do back it up before you do that just in case something goes wrong and it becomes worse. Also even if this is sorted out, it is still a good idea to have a live cd of gparted, which at this point doesn't work well on vista, but works well on most other OS's. Super grub disk is also another live cd that often comes in handy. If you find things still don't work, let me know - I have one idea left.

---

### Post by shenanigan on 2007-11-22
> **bumanie said:**
> Now that you can get into ubuntu, you should be able edit menu.lst via terminal and save it. As I said before, do back it up before you do that just in case something goes wrong and it becomes worse. Also even if this is sorted out, it is still a good idea to have a live cd of gparted, which at this point doesn't work well on vista, but works well on most other OS's. Super grub disk is also another live cd that often comes in handy. If you find things still don't work, let me know - I have one idea left.
You solved my 2nd problem **bumanie**. I just backed up my menu.lst and edited it. I now have my old system back. Thanks a bunch!!! I´ll keep on exploring, Ubuntu is one of the best customizable OS I´ve even seen. 
________________________________________
Current Mood:
[IMG]http://pics.livejournal.com/black_beast/pic/001h6ex8[/IMG]
CELEBRATION

---

