---
title: "using live CD to fix partition mess"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-02
You know when you boot up and text starts running by and then something called "grub" get mentioned? Anyway, from there you can choose which OS you want to boot into. Well for me I now have three options when I only want two. A while ago I re-installed Ubuntu because I had screwed too many things up and I now have almost everything working great (thanks to this forum) but one nagging problem is that I have my partitions screwed up. I don't know how much HDD space I have dedicated to Windows and I have two iterations of Ubuntu installed when I only want or need one. I need to delete one Ubuntu partition and make sure that the Windows and Ubuntu portions are the right sizes. I was told on another thread that the best way to do this is using the Live CD but If I knew how to do that I wouldn't have screwed things up in the first place.

---

### Post by forestpixie on 2008-01-02
can you do these in terminal and post the outputs

```
df-h
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by stump138 on 2008-01-02
Most often, especially after a patch or upgrade that changes your kernel, the GRUB list gets updated. It will simply prepend the list instead of change it. I would approach it this way to start.

Since you only want the latest version of Ubuntu showing up in the menu you can edit the display menu. The menu display can be changed by editing the file /boot/grub/menu.lst

If you want to look at and possibly change your partitions.  I would try gparted as it has a nice visual system for looking at your partitions, that should allow you to see what your partition status looks like.  It will also let you edit partitions on the fly iirc

sudo apt-get update && sudo apt-get install gparted

---

### Post by boriquajake on 2008-01-02
> **forestpixie said:**
> can you do these in terminal and post the outputs

```
df-h
cat /boot/grub/menu,lst
sudo fdisk -l
```

For the first one:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.1G  3.0G  1.9G  61% /
varrun                248M   92K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   88K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
jake@jake-crappy-lenovo:~$ 


for the second:
>  cat /boot/grub/menu,lst
cat: /boot/grub/menu,lst: No such file or directory


I know I messed up something.

---

### Post by stump138 on 2008-01-02
you're showing a comma instead of a period in your syntax, please try again just in case it was a silly typo :)

---

### Post by forestpixie on 2008-01-02
:oops:

changed it now

---

### Post by boriquajake on 2008-01-02
The comma was exactly the problem, thanks so much. Here are the results:

> jake@jake-crappy-lenovo:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=24c8888c-dc27-479c-99be-ce22fbda838b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=24c8888c-dc27-479c-99be-ce22fbda838b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=24c8888c-dc27-479c-99be-ce22fbda838b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=94abbcab-7daa-474c-8492-043c3e2e5b0f ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=94abbcab-7daa-474c-8492-043c3e2e5b0f ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, memtest86+ (on /dev/sda3)
root            (hd0,2)
kernel          /boot/memtest86+.bin  
savedefault
boot

jake@jake-crappy-lenovo:~$ 



---

### Post by boriquajake on 2008-01-02
And here are the results of the last one.

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7371    59207526    7  HPFS/NTFS
/dev/sda2            9063        9729     5357677+  12  Compaq diagnostics
/dev/sda3            7372        8273     7245315   83  Linux
/dev/sda4            8274        9062     6337642+   5  Extended
/dev/sda5            8986        9062      618471   82  Linux swap / Solaris
/dev/sda6   *        8274        8947     5413842   83  Linux
/dev/sda7            8948        8985      305203+  82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by forestpixie on 2008-01-02
can you do the fdisk command

oh you did :)

---

### Post by forestpixie on 2008-01-02
you have ubuntu on sda3 as well - it boots from sda6

you could use a partition tool to sort that  - there's one on the gutsy livecd - gparted

depends on waht you want to do with it then

---

### Post by boriquajake on 2008-01-02
> **forestpixie said:**
> you have ubuntu on sda3 as well - it boots from sda6

you could use a partition tool to sort that  - there's one on the gutsy livecd - gparted

depends on waht you want to do with it then

I installed gparted but when I run it I have no idea how to make sense of what it tells me and I don't dare start deleting partitions without really knowing what I am doing.

I would like to end up with my HDD in roughly two pieces. I say roughly because as ignorant as I am I do not know if I need extra partitions for things like backups or "swap" or whatever. Essentially I just want one for Windows and one for Ubuntu. I would like as much space as possible dedicated to the Ubuntu side, maybe like 80/20 Ubuntu/Windows.

---

### Post by thelatinist on 2008-01-02
The question is, which installation of Ubuntu are you actually using?  The one on sda3 (which appears last in your grub menu, or the one on sda6 (which appears first)?  We need to know that before we can advise you which partitions it's safe to delete.

---

### Post by forestpixie on 2008-01-02
if you mean you installed it in gutsy - it won't allow you to edit mounted partitions - which is good :)

try going to the gparted [site]("http://gparted-livecd.tuxfamily.org/"), download the livecd and burn it as an iso - then you can boot with it

It references the partitions in the same manner as the fdisk -l command did

---

### Post by boriquajake on 2008-01-02
Both the Ubuntu partitions are 7.10 but the most recent one is the one that I am using. The other can be deleted.

I am going to the gparted site to download and burn the iso. When I have it should I post here or is it self explanatory for a n00b like me to pull it off?

---

### Post by thelatinist on 2008-01-02
> **boriquajake said:**
> Both the Ubuntu partitions are 7.10 but the most recent one is the one that I am using. The other can be deleted.

Most recent?  We really can't tell from what you've posted which is the most recent.  Are you choosing the one at the top of the grub boot menu?

---

### Post by antisocialist on 2008-01-02
i had a similar problem earlier, once you have the gparted livecd or if u boot into the ubuntu livecd and open the terminal (in the live cd) and type```
sudo gparted
``` it will open gparted, right click the ubuntu you want to delete, select delete, then right click the one you want bigger, and click resize and add all the space you can till the first number entry box says 0 (i usually just type 999999999 in second box and hit enter) and then click "start" or something like it, it will take between 5 and 30 minutes depending on your hard drives size

---

### Post by boriquajake on 2008-01-02
> **thelatinist said:**
> Most recent?  We really can't tell from what you've posted which is the most recent.  Are you choosing the one at the top of the grub boot menu?

Yeah, sorry, I am using the one at the top of the grub boot menu. :confused:

---

### Post by forestpixie on 2008-01-02
as it stands you have about 15Gb of the drive being used by linux in some form.

If you wan to make that more you're ging to have a bit of work to do.

And as thelatininst has said we need to know which one you're using 

To achieve what you want you'll need to resize the windows partition first, then you can resize the sda3 partition and use it as a data partition. It looks like the compaq recovery is at the end which will be helpful

---

### Post by boriquajake on 2008-01-02
> **antisocialist said:**
> i had a similar problem earlier, once you have the gparted livecd or if u boot into the ubuntu livecd and open the terminal (in the live cd) and type```
sudo gparted
``` it will open gparted, right click the ubuntu you want to delete, select delete, then right click the one you want bigger, and click resize and add all the space you can till the first number entry box says 0 (i usually just type 999999999 in second box and hit enter) and then click "start" or something like it, it will take between 5 and 30 minutes depending on your hard drives size

Sweet, I think I am almost there. Now that I have gparted up I see the list of partitions. How do I know which is the one I want deleted and which is the one I want expand. The only Ubuntu I need is the one that shows up at the top of the grub boot menu but how do I know which one that is on this list?

---

### Post by forestpixie on 2008-01-02
> Yeah, sorry, I am using the one at the top of the grub boot menu.

ok that one is sda6 then

first make sure that win has been defragged a couple of times then
get the gparted cd sorted out and boot with it

once it's loaded - I would resize the win partition to get the space you want - make sure you leave it enough room for what you use it
then apply - you will then have unallocated space - delete sda3 and then you can make a new partition with the resulting space which should hopefully be bigger

once you've done that and you've booted back into ubuntu you can then edit the menu and it will go from there - but I'd deal with one thing at a time

---

### Post by forestpixie on 2008-01-02
yea that looks like I was expecting

---

### Post by thelatinist on 2008-01-02
Okay, now that we know this, here is what you need to do (as forestpixie warned, there will be lots of steps):

1) Boot into Windows.  Defragment several times.  Yes, you need to do it several times to make sure everything is as defragmented as possible..
2) Back up any essential data.  Although GParted is a very good program, you should always have a backup before messing with partitions in any way.
3) Boot into the GParted LiveCD.
4) Resize /dev/sda1 (your Windows partition) to the size you want.  Leave at least 2 GB free for expansion.
4) Delete /dev/sda3
5) Delete /dev/sda5
6) Resize /dev/sda4 to fill all the space freed by resizing /dev/sda1 and deleting /dev/sda3
7) Resize /dev/sda6 to fill all the free space in /dev/sda4/
8) Click apply.
9) Wait.  This will take a long time.  Maybe hours.  There are a lot of steps to be done here.

---

### Post by antisocialist on 2008-01-02
the post above could be kind of confusing, so heres an easier to understand way:

in gparted, delete the ext3 partition that doesnt say / in the mount category, now go to sda6 and right click and click resize, do what i said in my other post, click apply, if you still dont have enough space resize the windows partition (ntfs filesystem) so that the aount of space u remove is what you want in ubuntu, then right click the ubuntu one and resize and give it all the unallocated space, click apply and you are done (after gparted finishes, of course)

hope i helped, i think i just got my problem fixed a min ago too (stupid windows install just has to delete grub, doesnt it)

EDIT: woot, i just passed 200 posts

---

### Post by thelatinist on 2008-01-02
**antisocialist:** take a look again: this person has an extended partition that contains his linux and swap partitions (plus an extra swap partition).  He cannot simply delete /dev/sda3 and resize /dev/sda6 without first deleting this extra swap partition and resizing his extended partition.  Also note that he wants about 20% for his Windows partition and 80% for his Ubuntu partition.  The steps I listed will accomplish exactly what he wants.  Yours won't work.

---

### Post by boriquajake on 2008-01-03
> **thelatinist said:**
> Okay, now that we know this, here is what you need to do (as forestpixie warned, there will be lots of steps):

1) Boot into Windows.  Defragment several times.  Yes, you need to do it several times to make sure everything is as defragmented as possible..
2) Back up any essential data.  Although GParted is a very good program, you should always have a backup before messing with partitions in any way.
3) Boot into the GParted LiveCD.
4) Resize /dev/sda1 (your Windows partition) to the size you want.  Leave at least 2 GB free for expansion.
4) Delete /dev/sda3
5) Delete /dev/sda5
6) Resize /dev/sda4 to fill all the space freed by resizing /dev/sda1 and deleting /dev/sda3
7) Resize /dev/sda6 to fill all the free space in /dev/sda4/
8) Click apply.
9) Wait.  This will take a long time.  Maybe hours.  There are a lot of steps to be done here.

Before I get too much farther into following your instructions I do have a question about my Windows partition. According to gparted I am using like 54 GiB but I have almost nothing on my HDD in the way of personal data. I have long since moved or deleted all of my music and photos and even my text documents. I went through and uninstalled a bunch of programs I didn't need...Anyway, the point is there shouldn't be much more than the OS and a few basic aps, like Open Office on the Windows side, why is it that I can't shrink the Windows partition down beyond 54 GiB? Also, I defragged 5 times and according to the little windows defrag tool most of the files were contiguous with very little to be gained by defragging more.  Windows also said said the same thing about my disk usage as gparted,  i.e. that I was using about 54 GiBs of space but I wrote it off as stupid and went on. 

Anyway, why would my HDD be so full when I have nothing saved and how do I shrink this puppy?

---

### Post by boriquajake on 2008-01-03
Well, it looks like a did something very bad. I left the Windows partition alone and I just deleted the extra Ubuntu partitions as instructed. (At least I think I followed the instructions, it is just as likely that I made a mistake) and now when restart the computer I get "Grub loading, please wait..... Error 22" 

That's bad, isn't it?

---

### Post by forestpixie on 2008-01-03
boot the ubuntu livecd and do 

```
sudo fdisk -l
```

then we can all have a look 

as far as the windows partition size goes I really don't know why gparted won't resize it - you are using the gparted livecd - yes or no ? if what you're saying is true you should probably be able to resize it right down

---

### Post by boriquajake on 2008-01-03
> **forestpixie said:**
> boot the ubuntu livecd and do 

```
sudo fdisk -l
```

then we can all have a look 

as far as the windows partition size goes I really don't know why gparted won't resize it - you are using the gparted livecd - yes or no ? if what you're saying is true you should probably be able to resize it right down

That's the thing, there is nowhere to code anything. Once that Error 22 shows up in the boot process everything just hangs there. I let it sit for 10 minutes and nothing happened. I ended up just putting in the Ubuntu Live CD and re-intalling over everything. Screw Windows anyway.

I thought gparted only let you shrink partitions down to the limit of the empty space. If you tried to shrink a full partition what would it do, compress data? Delete stuff at random?

---

### Post by forestpixie on 2008-01-03
you could probably have got it sorted without a reinstall 

certainly you'd of been able to get the partition information, and supergrub would have been able to get grub back

but now you've reinstalled I guess you're ok now :)

gparted can't shrink a full partition afaik, I still not sure why ghparted wouldn't shrink the partition

---

### Post by perixx on 2008-01-03
If I may add my 5 cents here...

perhaps grub couldn't resize Windows' partition, because of the prefetching and superprefetching features were enabled; those will pick frequently used data (also system files) and places them (somewhere) on the outer zones of the HDD platters, in order to get lower access times. Also, the pagefile.sys (MS-'swap', usually about 2.5 times the RAM's size) and hiberfile.sys (cache for suspend mode) may contribute a little.

Anyway, perhaps it's a good idea to switch off the prefetching features in the registry + the suspend mode before defragging and, disposing of any unneeded programs and temporary junk (with 'Clearprog', for instance) - can save up to a few gigabytes of space. Btw. it's by far better to use the tools 'bootvis' and 'pagedefrag' instead of Windows' native defragger, for those goodies will defrag while Windows is booting (and even the system files!). Additionally, one might delete the 'pagefile.sys' file from Linux, gaining a really lean basic XP installation and be able to create a complete Windows-backup of a size as low as 3,5GB...

perixx

---

### Post by boriquajake on 2008-01-03
> **perixx said:**
> If I may add my 5 cents here...

perhaps grub couldn't resize Windows' partition, because of the prefetching and superprefetching features were enabled; those will pick frequently used data (also system files) and places them (somewhere) on the outer zones of the HDD platters, in order to get lower access times. Also, the pagefile.sys (MS-'swap', usually about 2.5 times the RAM's size) and hiberfile.sys (cache for suspend mode) may contribute a little.

Anyway, perhaps it's a good idea to switch off the prefetching features in the registry + the suspend mode before defragging and, disposing of any unneeded programs and temporary junk (with 'Clearprog', for instance) - can save up to a few gigabytes of space. Btw. it's by far better to use the tools 'bootvis' and 'pagedefrag' instead of Windows' native defragger, for those goodies will defrag while Windows is booting (and even the system files!). Additionally, one might delete the 'pagefile.sys' file from Linux, gaining a really lean basic XP installation and be able to create a complete Windows-backup of a size as low as 3,5GB...

perixx

Is there any reason why my XP partition would have had 54 GiBs of data on it? I mean, seriously, I didn't have any movies, or music or photos or anything. What the heck?

---

### Post by perixx on 2008-01-03
Well, might be the case inspite...

You should've run Easycleaner and look for the lost space, it's got a very nice graphical disk usage feature.

Apart from that, depending on how long you've been surfing without cleaning up your temporary internet files (and what content you've been viewing) there can easily stack up some several GB's. Also temp-files from installations and similar belong to that category.

As movies are dropping out (are you sure ? :]), music files use a lot of space, as do games, if installed directly to the HDD (up to about 10GB just for WoW, for instance). System settings like virtual memory and and suspend mode can use about 2-5GB. The system file backups (i386 folder if I'm not mistaken) and the system update backups can easily sum up to a few gig's as well.

Perhaps you had a problem with a corrupt filesystem and lost clusters or a virus infection or you had a hidden recovery partition connected to it, who knows? As you've re-partitioned everything now, you maybe can let the matter rest ;)
But I'd like to advise you to make frequent use of 'Clearprog' - if you're not doing so already - which can, if configured once, clean up all your temp-files, surfing traces and a lot more with a single click... (very tiny proggy that is)!

best regards,

perixx

---

