---
title: "[SOLVED] Relocate Ubuntu"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-03-13
Hi there. Iv searched the forums and found a number of threads with similar requirements, but none seem to have the same kind of setup as me so Ill ask the question.

Using Ubuntu 7.10 - I have rather a strange setup:

hda1 = Windows 2000 C drive - NTFS
hda5 = Logical Windows partition - NTFS
hda6 = Logical Windows partition - NTFS
hda7 = Ubuntu (In logical partition) - ext3 (6 Gig)
hda8 = Swap (In logical partition)
hda9 = /home (In logical partition) - ext3 (3 Gig)

hdb1 = Windows XP C drive - NTFS (58 Gig)
hdb2 = Windows XP Storage drive - NTFS

Currently GRUB finds the Windows bootloader which then lets me choose between XP and 2K.

Questions:
I would like to format the XP partition (hdb1) and install Ubuntu there, giving myself more space. I would also like to leave my current Ubuntu installation where it is, as a kind of testing-ground for new software or even different distros.

However, I would like to transfer (Copy) my current Ubuntu installation to the new, larger space so that I don't need to set everything up again.

Can this be done?
Am I likely to hit problems? (Remembering that the new installation will be on a different drive entirely)
How will GRUB handle the new Ubuntu, will it still see the original Ubuntu, and it will it still see the Windows bootloader (So I can still get into 2K if I need to)?

I'm still flailing a bit with this. I want to move Ubuntu to a larger space and preferably lose Windows XP (I have more stuff on 2K) but I'm not sure which way to jump. If it comes to it I can just as easily back things up and install over the whole of hda, but of course that will destroy my current Ubuntu, and I don't want to have to set everything up again.

I have backups of / and /home, produced with the excellent Quickstart 6 (Found on these forums), but again, I'm unsure about restoring to larger partitions (Which might even be on a different physical drive).

Any advice would be very helpful.

Thanks

Max

---

### Post by kpkeerthi on 2008-03-13
> hda1 = Windows 2000 C drive - NTFS
hda5 = Logical Windows partition - NTFS
hda6 = Logical Windows partition - NTFS
hda7 = Ubuntu (In logical partition) - ext3 (6 Gig)
hda8 = Swap (In logical partition)
hda9 = /home (In logical partition) - ext3 (3 Gig)

hdb1 = Windows XP C drive - NTFS (58 Gig)
hdb2 = Windows XP Storage drive - NTFS

This method requires *no changes* to GRUB

1. Delete hdb1 and format it as ext3.
2. Mount it as new /home by changing your fstab. See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
3. Now copy any data files over from hda9 (your old home) to your new home
4. Delete hda8 & hda9. This will produce some unallocated space.
5. Resize hda7 to occupy portion of unallocated space (leave unallocated as big as the size of swap you need)
6. Format the rest of the unoccupied space as swap partition hda8

You need to all this from a Live CD. I recommend [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
* Be sure to backup when altering your partition *

---

### Post by MaxVK on 2008-03-13
Thanks for the reply, but this method will destroy my / installation, and I want to copy that across too so that I don't need to re-install my applications (There are quite a few now, all working well, and bandwidth is tight).

Is there not a way to retain the entire current setup?

Regards

Max

---

### Post by MaxVK on 2008-03-15
Hmm. I think Id better leave this for a while yet. I'm not prepared to install everything again and it seems that transferring the actual OS is not going to be straightforward.

Thanks anyway

Max

---

### Post by djamu on 2008-03-15
This is very easy & you don't need to install any packages.... it's all buildin & you won't lose a bit buddy

Summary > you want to copy/clone your entire existing ubuntu to the old XP partition right  ? including your /home ? ( doesn't really matter )

so either /dev/hda7 + /dev/hda9 > /dev/hdb1
or just /dev/hda7 > /dev/hdb1


1.  format /dev/hdb1 to the fs of your liking ( ext3 / reiserfs ) 
2. mount /dev/hdb1 to a temporary folder ( /media/temp for example ) **just make sure the mount point is excluded in following command**
3. issue following commands > 

```

cd /

sudo tar cvpzf /media/temp/ubuntu-backup.tgz --exclude=/etc/fstab --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

cd /media/temp

sudo tar xvpfz ubuntu-backup.tgz -C /media/temp


```

if you don't want to copy the existing /home just add --exclude=/home to the command. Do not forget to end the tar command with / ( pointing to the source, this is easily overlooked )
This will keep all permissions & users intact.
You'll need to recreate the /etc/fstab file to match your new environment + you'll need to edit the /boot/grub/menu.lst   just duplicate the boot command of your old installation ( way down ) and point it to /dev/hdb1 ( generating a UUID is actually the preferred way )

then just reboot & point to your cloned installation...


):P

---

### Post by MaxVK on 2008-03-15
Thanks djamu.

Iv looked at the --usage of tar but there are lots of options and I cant seem to find those that relate to the options you specified. Any chance you could explain those tar commands for me? Am I copying the files, archiving them and then copying them or what?

I'm assuming that I can follow this procedure for both /home and /root, excluding the correct thing each time (So that I can make hdb1 into two partitions and have a separate /home partition again)?

Ill have to swat up on fstab and menu.lst as well, because Iv just been looking through them and they are far from straightforward!

Thanks again, I'm starting to make headway now.

Regards

Max

---

### Post by djamu on 2008-03-15
> **MaxVK said:**
> Thanks djamu.

Iv looked at the --usage of tar but there are lots of options and I cant seem to find those that relate to the options you specified. Any chance you could explain those tar commands for me? Am I copying the files, archiving them and then copying them or what?


for a complete explanation type >man tar
the v flag is a verbose flag > you'll see what is copied
the p flag is preserve permissions ...
the rest just defines type of archive, nothing fancy...

You'll actually archive & then unarchive it ( so you'll have a complete system backup... )
hint:
 I usually crontab this ( daily ) on my servers & write the backup to a mounted share... easy....

> 
I'm assuming that I can follow this procedure for both /home and /root, excluding the correct thing each time (So that I can make hdb1 into two partitions and have a separate /home partition again)?


sure... just keep in mind the copying is not on a block device level ... > so you'll have to mount any partitions you want to copy from & to 


> 
Ill have to swat up on fstab and menu.lst as well, because Iv just been looking through them and they are far from straightforward!


Nah! it's easy... you'll just copy fstab > change 1 line in ... ( look for the mountpoint / )

looks like this > 
```
# /dev/sda2
UUID=a3b688ce-58cf-4539-90b5-3c1c58ec59df   [COLOR="Red"]/[/COLOR]               ext3    defaults,errors=remount-ro,usrquota,grpquota   0       1

```

and make it look like this > 

```
# /dev/sdb1
UUID=a3b688ce-58cf-4539-90b5-3c1c58ec59df     [COLOR="Red"]/[/COLOR]               ext3    defaults,errors=remount-ro,usrquota,grpquota   0       1

```

just change the #/dev/sda2  ( or whatever that's there ) & **update the UUID** 

**> how to find UUID for the drive >** 
```

 ls /dev/disk/by-uuid/ -alh

```

look for the UUID of /dev/sdb1  ( or whatever )





same for /boot/grub/menu.lst 

look for the lines ( near the bottom )
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a3b688ce-58cf-4539-90b5-3c1c58ec59df ro
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

just copy this block ( which will look slightly different ) and place it just below or above this one 

change > root (hd0,1) to root(1,0)  > meaning look for physical disk 2 partition 1 ( 0 = the first )

change UUID=....     ( same as with fstab )

change also the title ( this is shown in the grub menu, so you'll know what you're booting )


if you don't see a grub menu, go near the top of /boot/grub/menu.lst & look for following line

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

comment out hidden menu like this ( no spaces )

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

you can also enlarge the timeout value ( it's just above the hiddenmenu statement )


:popcorn:

---

### Post by MaxVK on 2008-03-16
Excellent explanation, thanks djamu.

---

### Post by louieb on 2008-03-16
> **djamu said:**
> for a complete explanation type >man tar
the v flag is a verbose flag > 
As an option to using tar the latest versions of GParted can copy one partition to another.  The downside to doing this is the partitions UUID gets copied also. Leaving Ubuntu quite confused when it starts back up.

Short of reformatting the original partition   haven't found out how to give a partition a new UUID.  
The only work around I've found is to scrap the UUID in /boot/grub/menu.lst and /etc/fstab. and use the device name ie. /dev/sd@#. 

Oh well time to diddle.

---

### Post by djamu on 2008-03-16
> **louieb said:**
> As an option to using tar the latest versions of GParted can copy one partition to another. 


As a side note.. problem with gparted is that it's unable to recognize raid array's, is does "see" the individual devices but not the MD devices... so it's kind of .... useless with them....
Since this works on a block device level, **the target should be exactly equal in size**... which is not the case, so one should always resize a partition to match them > copy the partition & resize again..
quite a lengthy operation... and not fool proof.... ( I just mean to say, things can go horribly wrong on that one )


;)

---

### Post by MaxVK on 2008-03-16
Hold on now, Iv a feeling I might have an even easier method, although Id appreciate it if someone could let me know if this is feasible or not:

I use Quickstart to backup my system ([Found Here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462")) and I have asked a question on this subject once before in that very thread, although I then moved onto something else and forgot about it for a while.

Quickstart allows me to backup /,  my /home folder, and my configuration files as separate archives. Would it be possible to use a partitioner (Like gparted etc) to format and partition my larger drive (One partition for root and one for home), and then use Quickstart or some other manual method, to restore my current system to the relevant partitions?

If this is possible I would presumably be left with my current installation, and another, identical installation on the larger drive. Of course my current installation would still be the boot installation, so assuming that this is all possible, which files would I need to edit to *include* the new, larger installation in the GRUB startup, and make it the first choice? (Hopefully leaving me with two fully working Ubuntu installations that I can choose from)

As another connected side note, when I manage to relocate my current installation to the larger drive, I will still have my current installation intact. Will the two be able to see each other? In other words will they see each other and automatically add links to the drives on the desktop, in the same way that my current installation sees and adds links to my Windows drive?

Thanks for all your help

Max

---

### Post by djamu on 2008-03-16
> **MaxVK said:**
> 
If this is possible I would presumably be left with my current installation, and another, identical installation on the larger drive. Of course my current installation would still be the boot installation, so assuming that this is all possible, which files would I need to edit to *include* the new, larger installation in the GRUB startup, and make it the first choice? (Hopefully leaving me with two fully working Ubuntu installations that I can choose from)

As another connected side note, when I manage to relocate my current installation to the larger drive, I will still have my current installation intact. Will the two be able to see each other? In other words will they see each other and automatically add links to the drives on the desktop, in the same way that my current installation sees and adds links to my Windows drive?
Max

I'll take a look at that quickstart stuff, but first of all, I'm not a GUI guy.. for these low level manipulations I don't trust GUI's for the simple fact that gnome is not completely stateless .... meaning some files might be opened ( some files might have swap files )... to make a long story short... it most likely uses the same ( or about ) commands & alterations I proposed...
That whole operation > executing these, the   tar + editing fstab + menu.lst  < takes less time ( for me ) then writing this reply.... 

Both OS's  surely will be able to "interact" ( specify interact )  if your shortcuts ( symbolic links ) are absolute.... ( starting with / ) and all disks are mounted...

For the setup you want to achieve I usually keep a separate shared  /boot  partition ( 100MB is sufficient ) and a shared /home with 2 separate /   system disks
But then again I'm a server dude ( meaning very few things ever get changed in my /home )..
with you it might be the opposite ... consider that....

Nothing more to add....

:tongue:

---

### Post by mdpalow on 2008-03-17
Hi...

This is the author of QuickStart 6.0, which I see you're using and mentioning.

You've already got / and /home backed up. QuickStart doesn't care if you've changed your partition around to make it larger or whatever.

Just don't restore your config files and you'll be fine. After restoring / and /home, you should be right where you were when you made the back-up; no configuring or setting it up again from scratch.

---

### Post by MaxVK on 2008-03-17
djamu: Thanks for all your time, its very much appreciated. I think from reading what you've said I might have to start using the command line more often. At the moment, as an ex-long-term Windows user, I still find it quite daunting if I don't have some command lines in front of me to copy and paste, along with an explanation of what they actually do.

Thanks again.

mdpalow: Many thanks for taking the time to pop in and give an answer. Its good to know that the system can be relocated like this - I'm starting to feel the squeeze on the smaller drive now, and Windows is just sitting there doing nothing so....


Many thanks to you both

Regards

Max

---

### Post by MaxVK on 2008-03-18
Hi there, just an update:

I have now done the deed and I'm working on my new, larger partition. 

Thanks for all the advice.

Max

[EDIT]
Just for completeness I decided to explain exactly what I did, just in case anyone else is in a similar position:

I make regular backups using Quickstart (There's a link in this thread) placing the files onto an external HD which is large enough for me to keep a reasonable system history, allowing me to go back in time if need be.

I installed Ubuntu onto the larger partition (This is where I want to relocate to), using the swap partition from my original installation, and then didn't actually do anything to it once there, not even installing the NVIDIA drivers. I then plugged in the backup drive and installed Quickstart, which has been stored there, and tried to restore the last backup files.

However, as soon as Quickstart tried to perform the backup, it finished straight away and told me that it was complete. Certainly too fast to have restored 2 gig! I then ran Quickstart from the console, and noted that there was an error finding the file on the external drive so I copied the backup files to my desktop and tried with them instead.

Everything worked just fine on the first attempt, although my marble trackball configuration wasn't restored, possibly because I didn't restore the config backup (As per the advice above). However, since my original installation was still there it was only a matter of a few moments to copy the relevant information across. Aside from that one thing everything else seems to have been restored just fine, and I still have a backup of the original files both on the external backup drive, and as a live installation on my original setup.

So there you go. Quickstart worked just fine for this job and Im very happy in my new, far roomier Ubuntu installation!

Regards

Max

---

