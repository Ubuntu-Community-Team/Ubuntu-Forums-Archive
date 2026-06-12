---
title: "Just accidentily installed ubuntu/xp dual boot"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Chrispyballs on 2008-01-02
I had been trying to dual boot xp and ubuntu 7.10 on my dell inspiron laptop according to [this tutorial]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") for the better part of the past few hours.  My problem seemed to be that I could not find any option for making my primary ext3 partition bootable, nor had I encountered any mention of GRUB at any point during the installation.  Finally, I flagged the ext3 partition as bootable in Gpart, ran the installation again, specified my swap and shared partitions as instructed during the install, hit "advanced" before final install (and changed hd0 to hd0,1), and like magic, upon reboot I was able to choose between ubuntu and xp.  Both boot just fine.

Now I'm having a problem (or perhaps it's just a misunderstanding, as I've still not gotten the hang of this whole "mounting" business) accessing my shared partition.  Again, the reference to this issue in the above tutorial does not exactly match what I see in real life.  When editing fstab, there is no uid or gid, but instead I have this line:
# /dev/sda6
UUID=477B-006F  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1

(another thing... why are my drives listed as sda, when in every tutorial I have seen thus far, the drives are listed as hda?)

Instead of changing uid and gid, as in the tutorial, I changed umask and gid to my user id and group id (both 1000).  Upon reboot, I still cannot find my shared partition.  Come to think of it, I cannot find the partition I specified as / either.  Despite every warning against the practice, I even tried logging in as root to see if I could find my shared partition... still, I could not access it (and quickly logged back in as a regular user).  

This noob is in over his head...

---

### Post by fiddledd on 2008-01-02
That's a rather old guide you used (05/08/2006). I installed Ubuntu on a Hard Drive that already had XP all I did was create free space on it after defragging XP partition etc. The rest of it was done by Ubuntu Live CD pretty much automatically. When I first booted I had the Grub Menu with the chioce of Ubuntu/Memtest/Recovery etc and an option to boot XP. When Ubuntu loaded all my XP partitions (FAT32 and NTFS) were all mounted for me. I didn't have to mess with fstab until I decided not to automount all the XP partitions. So for over a year I've been dual booting Ubuntu and XP with no problems.

---

### Post by PmDematagoda on 2008-01-02
First create a file in /media:-
```
sudo mkdir /media/shared
```

Then open the fstab file for editing using:-
```
gksudo gedit /etc/fstab
```
and change the fstab line to:-
```
UUID=477B-006F [COLOR="Red"]/media/shared[/COLOR] vfat defaults,utf8,umask=007,gid=46 0 1
```

After that is done, save the file and execute:-
```
sudo mount -a
```

Then see if you can access "shared".

---

### Post by Chrispyballs on 2008-01-02
Actually, you know what?  I think this is just an issue of my still "thinking in windows mode".  Shared is plainly visible as a folder in ubuntu.  Is that correct?  When I saved something to it, it showed up under the drive letter for that partition in XP.

So I formatted the shared partition as fat32 because I was under the impression that ubuntu could not read NTFS partitions... however, I am also able to access, save to and read from my NTFS drives from ubuntu.  Why did I have to format a special partition as fat32 then?  Could I have just kept one big ext3 partition and a swap partition?  Is there any way to do that now?

---

### Post by Hightide on 2008-01-02
I used the GParted Live Bootable CD to create a second partition, installed ubuntu and GRUB appeared after reboot with dual boot options XP or Ubuntu.

:)

---

### Post by PmDematagoda on 2008-01-02
You can use Gparted to delete the NTFS partition and resize the Ext3 one to fit it, but since you are resizing the root partition it brings about a few complications.

So here are(What I think) the options:-
1) Delete the NTFS partition and format it to Ext3 without resizing the main root partition so that you have two seperate Ext3 partitions, this is the safer thing to do and is easier. 

You can use Gparted through Ubuntu for this. Gparted can be installed using:-
```

sudo apt-get install gparted

```
2) Delete the NTFS partition and resize the root partition to make it occupy the entire drive, this is a little risky and also is more difficult since you will have to use the Gparted Live CD instead of through Ubuntu. You may download the Gparted Live CD from [here]("http://gparted-livecd.tuxfamily.org/").

The reason that you cannot resize the root partition while in Ubuntu itself is because the partitions to be modified need to be unmounted throughout the partitioning process.

---

### Post by Chrispyballs on 2008-01-02
Ok, so I used the rescue CD to run Gparted, deleted the fat32 partition, and resized the ext3 partition that ubuntu is installed on.  Then, I booted back into ubuntu and ran the disk analyser to make sure the extra space is accounted for.  

It was so easy in windows, but in linux, apparently all the drive space bleeds together, and I can't tell one drive from another.  So I still can't tell if my space was reclaimed or not.

Here is a screenshot of my disk analyser results and Gparted run from within ubuntu.

[IMG]http://img.photobucket.com/albums/v286/BlueCalx/Screenshot.jpg[/IMG]

Can anyone tell if what I did actually worked?  I'm still trying to understand how linux's filesystem works, so I don't understand what is meant, for example, when it says the size of / is 28.3 GB.  If / is the drive that ubuntu is installed on, shouldn't it be larger than that?  Shouldn't it be 51.64 GB like it says in Gparted?

---

