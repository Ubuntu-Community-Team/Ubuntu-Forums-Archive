---
title: "Love Ubuntu Want to Leave Windows - Help"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-09-10
Hi everyone! Thanks for reading

I love Ubuntu just sent for my powered by ubuntu stuckers, about to run it as my main os and vmware Windows.

My Problem is that i partitioned my hard drive with only 20gigs for ubuntu. I want to extended that partition to 200gs and leave the 35gs or so left over for vmware.

I need to move files over first. I have about 90 gs free on the Windows parition and a 30g external drive. 

I have to move around 80 gs of stuff. Whats the best way to do it?

---

### Post by JerMe on 2006-09-10
I'm not sure which files are where, so here's a general rundown.

Use what you know - boot into Windows, download the EXT2IFS driver from [www.fs-driver.org](www.fs-driver.org) which will allow you to see your linux (ext3) partitions, then move the data to wherever it needs to go.

---

### Post by redDEADresolve on 2006-09-10
I need to move the data from the win part to the linux. I need to make room first. I only have about 5gs avaiable on the ubuntu part.

Hope that clears it up

---

### Post by JerMe on 2006-09-10
Still fuzzy.  How big is the hard drive?  Is there only one hard drive?  Are there any other partitions besides Ubuntu and Windows?  Could you list everything (#partitions, size of each partition, partition type, etc.)

---

### Post by Jareth on 2006-09-10
I have win 98 and ubuntu on together, about to get rid of win myself actualy. A mate in work showed me how to view my windows partition from ubuntu so I just copied files accross. not sure if it will work on xp but here goes:

First off open a console >>>
 
cd /
 
sudo mkdir windows
 
sudo chmod 777 -R /windows
 
then >>>
 
sudo gedit /etc/fstab
 
then add this line at the end >>>
 
/dev/hda1  /windows   vfat   iocharset=utf8,umask=000   0       0
 
then press enter to the next line down
 
and save the file and reboot, you will then have your windows drive accessable and writeable
 
to get to it goto System > places > filesystem > windows
 
HAVE FUN

---

### Post by redDEADresolve on 2006-09-10
I'm on a single 250 gig drive. My Ubuntu part is only 20gs so it doesnt have enough room to move over the data yet.

I need to know how to expand my ubuntu partition, so i can copy the files over and then delete my windows partition to expand my ubuntu partition agian.

Leaving only 30gs or so to run windows in vmware.

Can I do this are am I just retarded?

Sorry it wasn't very clear.

My WindowsXP MCE part is 210gs
My Ubuntu is 19gs
there a 800mb swap file partition also

I have about 90 gs free on the win part and about 4.5 on the ubuntu part.
I also have a external 30g drive i can use to move files/store while resizing.

---

### Post by Najand on 2006-09-10
Back up your data. Delete Windows Partition. Then Use Gparted or similar to resize the Linux ext3's partition. Don't forget to erase Windows Booting Parameters at your grub configuration file, i.e. /boot/grub/menu.list
*****
DON'T FORGET TO BACKUP YOUR DATA FIRST, BECUASE THERE IS ALWAYS POSSIBILITY  OFDATA LOSS DURING REPARTITIONING.

---

### Post by bodhi.zazen on 2006-09-11
It depends on your partitioning scheme.

I suggest you move the data you want from the windows partition to your 30 GB usb drive.

Re-format the windows partition to you fav Linux file-system.

Then copy you data back from the usb drive. Use the old windows partition as a data partition.

Resizing your Ubuntu partition will not be so easy. You can not easily add space in front of a partition to a partition. Clear as mud?

Say you have 3 partitions: hda1, hda2, and hda3; each 10 GB.

You can easily make this into hda1 = 10 GB + hda2 = 20 GB (delete hda3 and add space to hda2).

But you can not easily hda2 = 20 GB + hda3 = 10 GB (delete partition hda1 and add space to hda2).

To do this you will have to back up and move all of your ubuntu partition.

If you wanted to do this it would be almost easier to back up all your data, wipe the hard drive, and start anew.

If you want to move your ubuntu partition see here:
[Backup **Restore** System](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by JerMe on 2006-09-11
> **bodhi.zazen said:**
> If you wanted to do this it would be almost easier to back up all your data, wipe the hard drive, and start anew.

I'll second this.  If you're hellbent on removing Windows, It will be a lot easier if you nuke the drive.  If Windows wasn't the first partition in your partitioning scheme (I'm assuming it is), then it would be a matter of wiping, resizing, and moving - you wouldn't have to touch the Ubuntu partition at all.

Here's another alternative. You can do nothing and use the NTFS-3G driver in Ubuntu to write to your NTFS-formatted Windows partition.  Anything that you have in your Ubuntu home directory can be moved to the NTFS drive, leaving your Ubuntu "/" partition only for installed software - your current 20GB is plenty for installation.  When you get to using vmware-server, you can set it up where the virtual machines will be installed on the NTFS partition rather than your Ubuntu "/" partition.

Regardless of what you decide to do, you should dump your most important data onto that 30GB external drive, then burn off whatever you can, if not all of it, onto DVDR.

---

### Post by redDEADresolve on 2006-09-11
Ok ill borrow a drive from microcenter tommorrow and just put everything on a 200g external drive.

So once I back up. i have reformat the hard drive, restall ubuntu, (not that major, i have my back up), then repartition the main drive leaving a section for my virtual machine.

Copy files over, clear drive, return it and enjoy.

Or am I oversimplifying things?

---

### Post by JerMe on 2006-09-11
Chop the drive into three pieces - one for "/", one for swap, and leave the rest for data.  It's up to you how big you want your "/" partition to be.  

Not sure what you mean by "leaving a section for my virtual machine", but just create a folder named "virtual_machines" on the data partition and point to it when vmware asks.

Before you return the extra drive, make sure you wipe it out with something like [DBAN]("http://dban.sourceforge.net/").

---

### Post by bodhi.zazen on 2006-09-11
That is what I would do.

/ = 15 - 20 Gb
swap = RAM x2
vmware 35-40 Gb
I prefer a data partition to a /home partition. Give it all ya got. There is nothing in /home that you need except data.

---

### Post by Requiem on 2006-09-11
Your windows partition is on ntfs or fat32? ntfs is the default in xp. Ubuntu partitions are by default ext3.

A program called gparted can rezise both partition types, its easy to use has a nice gui, but you need to unmount your main drive before resizing it. that means you have tu use some kind of liveCD, dapper liveCD includes gparted, there is a mini distro with only gparted as main app, other mini distros also carry gparted.

Once in the live CD/floppy/usb launch gparted and resize as much as you can before you start before gparted tellsyou that you can't do that because the partition can't be resized without loosing files.

Now get into you ubuntu partition, now larger than before, and start copying files from windows to ubuntu, once the partition is full, boot into windows and delete the same files you just copied.

This means the windows partition has now more room to loose, boot into your live os and resize again.

Repeat until your windows partition has the desired size.

If you only have to move 80GiB and you have 250GiB you probably only need to do this twice.

The

---

### Post by bodhi.zazen on 2006-09-11
> **Requiem said:**
> A program called gparted ......

Nice thought, but see my first post.....

---

### Post by redDEADresolve on 2006-09-11
I should have a 6 gig swap file then? (I have 3gigs of DD2 667 ram)

One last question I dont think I understand how the vmware works. Anyone what to break it down for me like im stupid?

Thanks for your help everyone,you guys rock.

I'm writing this as I back-up data on my win partition and its just so ugly. I've gotten used to XGL/Compiz and wtf why don't I have 4 workspaces?!

---

### Post by anaconda on 2006-09-11
6GB swap would be waaaay too much. Actually if you have 3 GB ram you dont need swap at all, but if it makes you happy you can make 1 GB swap-partition. (I have 512MB ram and 1GB swap, and most of the time the swap isn't used at all..)
And if you dont make any swap, and later think that you need some, then you can always make a swap-file to your ubuntu partition..

And I don't understand why you want to make a separate partition for VMWare. It doesn't need one. When you install windows (or linux) to VMWare it makes a file for windows and then windows is made to believe that the image-file is actually a hard-disk and then windows can be installed to that file.
The image-file can be anywhere. eg. in your home directory, or in your data-partition. Actually you dont even have to make a fixed size imagefile.. it is possible to make an image-file that takes only as much room than the actual data in your windows installation. But with fixed-size image VMWare is supposed to be a bit faster..

---

### Post by redDEADresolve on 2006-09-11
cool i didnt know that, i didnt find a ton of stuff on vmware. now that i know i'm not gonna have to partition my drive for windows at all my jpb just got way easier.

thanks

Now I'm offically saying good by to dual booting. THANKS EVERYONE

---

