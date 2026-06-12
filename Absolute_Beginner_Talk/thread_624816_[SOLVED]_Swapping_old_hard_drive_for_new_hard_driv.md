---
title: "[SOLVED] Swapping old hard drive for new hard drive"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-27
It's incredible! I've been searching the forums and google since last night. When the mention of more than one drive is keyworded, all I get is people who have microsoft and Ubuntu.

I have a 20 gig drive as primary master. It is Gutsy v.7.10.

I have a new, never before used Maxtor 320gig drive.

I want to install the 320 gig, physically. I want t clone the old drive to the new one so that the fully updated gutsy OS and all it's settings, passwords, and other 'registered' items are there on the 320gig.

Then I want to remove the old drive. 

I would like it if the 320gig became primary master. Primary slave unused or used only for temporary work.

---

### Post by samuel.rajesh on 2007-11-27
> **Mark_in_Hollywood said:**
> It's incredible! I've been searching the forums and google since last night. When the mention of more than one drive is keyworded, all I get is people who have microsoft and Ubuntu.

I have a 20 gig drive as primary master. It is Gutsy v.7.10.

I have a new, never before used Maxtor 320gig drive.

I want to install the 320 gig, physically. I want t clone the old drive to the new one so that the fully updated gutsy OS and all it's settings, passwords, and other 'registered' items are there on the 320gig.

Then I want to remove the old drive. 

I would like it if the 320gig became primary master. Primary slave unused or used only for temporary work.

Wouldnt be easier to move ur home folder once u install ubuntu fresh ,there might be some cloning software whch works on linux,best of luck ,do post if u manage to solve it

---

### Post by gn2 on 2007-11-27
Have you looked at using a CloneZilla Live CD?

[http://clonezilla.sourceforge.net/clonezilla-live/](http://clonezilla.sourceforge.net/clonezilla-live/)

---

### Post by Mark_in_Hollywood on 2007-11-27
Samuel. Rajesh. What you propose is what I am trying to avoid. All the Gutsy Gibbon 7.10  updates are already installed on the 20 gig (old) drive. If I did as you ask, I would lose those and have to reinstall them. This is not to mention passwords, usernames, userIDs, etc., ad infinitum, ad nauseum. Thanks.

gn2: Complicated, but it's worth a close read, thanks.

---

### Post by malangaman on 2007-11-27
I have installed  hard drives in  several  PCs, both as replacement and as dual boot. I recommend a fresh install on the 320 G. It is cleaner, and painless with Gutsy 7.10. Connect the old as slave then transfer between the drives as you see fit, later.

---

### Post by hyper_ch on 2007-11-27
Hmmm, I'd try "dd"

If your 20GB drive is /dev/hda and your 320GB drive is /dev/hdb then I'd try:

```

sudo dd if=/dev/hda of=/dev/hdb

```

if = input file
of = output file
--> important, don't mess them up!

I have no clue if that works or not... if it works as I envision, then it should make an exact copy 20GB drive to the 320GB one... however I don't know how the partitioning will be handled on the 320gb drive.

---

### Post by bobpur on 2007-11-27
You could always leave the 20 gb drive alone as a master and install the 320 gb as a slave. Partition a portion for Ubuntu (say, I dunno, about 20 gb)  and then partition the rest as FAT32 and have a dualboot machine with a large storage area that both OS's can access. 
Just a thought.
OOPS! I read your post more thoroughly. I agree with Malangaman
Good luck.

---

### Post by Bigbird999 on 2007-11-27
Googling "clone Linux drive" gave this hit and many others.
[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)
Dated but sounds like what you want.

BB

---

### Post by gn2 on 2007-11-27
Create an installable Live CD of your current installation: [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

Or use Partimage: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) (think it's in the repos)

---

### Post by mocoloco on 2007-11-27
For actually moving the data I know what you can do, but you'll still have to probably fix some things in fstab and /boot/grub/menu.lst.

Googling, I found a page outlining [doing a hard drive move for Knoppix]("http://www.oreilly.com/pub/h/2504").  I've never done a full move of / but that appears to have some great info on the subject. 
I have done what's listed on psychocats.net that talks about [moving your /home to a new partition]("http://psychocats.net/ubuntu/separatehome").  The same idea wold work moving your entire filesystem from root.
Skip down to the heading for "Using the new partition".  You can also forget the stuff about backing up the mount point, etc.  The line you're most concerned with is this one:
```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
``` You would of course cd into the root partition of your old drive, and the destination would be the mount point of your new drive, probably something like /media/sdb1.  The idea behind cpio is getting special file types that would get screwed up just using cp.

Again, you'll still have to fix some things in /etc/fstab and for grub, and possibly other things I'm not aware of.

I know you don't want to reinstall, but have you looked at aptOnCD?  It's great for grabbing all your installed apps and updates, which you can then put on a CD, or in your case just save in a directory on one of your drives and then point synaptic to it.

---

### Post by CatKiller on 2007-11-27
> **hyper_ch said:**
> Hmmm, I'd try "dd"

That's what I'd do, too. That would make a 20 GB partition on the new drive, but you can always make it bigger with GPartEd anyway. It will take a while to do the copying.

As an alternative, you can use **tar**. Boot up the live cd, make your partitions on your new hard drive, mount your old hard drive at /mnt/source and your new hard drive at /mnt/target and use ```
( cd /mnt/source && tar clf - . ) | ( cd /mnt/target && tar xvpf - )
``` to copy all the data across intact.

---

### Post by Bigbird999 on 2007-11-27
and this one [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

BB

---

### Post by Lakefall on 2007-11-27
Moving the system with the basic system tools is easy if you know what you are doing, but a bit complicated. You need to be the root user throughout the process.

[LIST=1]
[*]Carefully create the new partitions (at least swap and root) on the new disk. They do not need to be the same size as the old ones (but obviously there has to be enough room for your data). Note that partitioning programs may cause severe data loss if you don't think before doing things.
[*]Carefully create the filesystem and swap. Use "mkswap [new swap device]" and "mke2fs -j [new root device]". Note that these commands may cause severe data loss if you don't think before giving them.
[*]It's probably a good idea to boot from a live-CD at this point to keep things simple. You should be able to do the previous steps from the live-CD also, if you want to.
[*]On the live-CD create some mount points ("mkdir /old_disk /new_disk") and mount the partitions ("mount -r [old root device] /old_disk", "mount [new root device] /new_disk").
[*]Copy all files from the old partition to the new one using the command "cp -a /old_disk/* /new_disk". Don't forget the "-a" option. Obviously you'll need to wait for a pretty long time for this to complete. Mounting the new device as ext2 might speed things up somewhat.
[*]Modify the file /new_disk/etc/fstab so that it points to partitions on the new disk, not the old one. Obviously you need to know how to edit fstab.
[*]Modify the file /new_disk/boot/grub/menu.lst so that it points to partitions on the new disk, not the old one. You need to know how to edit menu.lst and what "update-grub" does.
[*]Install grub on the new disk with grub-install. This may be tricky too.
[*]Boot from the new disk to make sure everything works. Also try to make sure you really are using the new disk for everything (swap etc.).
[*]After removing the old disk, you may need to redo steps 6 and 7, perhaps 8 too, I'm not sure.
[/LIST]

---

### Post by Mark_in_Hollywood on 2007-11-28
I've taken lots of people's time with this and am marking this thread as "solved".

Thanks to the community.

---

### Post by CaptainInsaneO on 2007-12-02
Mark, I'm trying to do exactly the same thing as you. What finally worked for you? Could you shed some light on this for me? Thanks.

---

