---
title: "Rookie issues installing Ubuntu as a 2nd OS"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by xanderificus on 2006-09-06
I've looked through the forums and tried to help the learning curve but I'm not as successful as I'd like to be.  :D 

BACKGROUND:  I've got my main HD partitioned as a C,D,E,F.  The C is NTFS and is my WinXP partition.  I've cleared off the E: drive where I plan to put Ubuntu as a dual boot.  (I hope to make Ubuntu my -main- OS and reserve XP for those tasks that don't port over.)

PRESENT DAY:  I boot up the Live CD (Dapper) and try the Install.  It, however, doesn't find any partitions on the HD, just the full thing.


I accept that setting up a dual boot, and installing another OS can screw up my main partition but I'll accept those risks.  I would like some input from folks who know better what they're doing than I.

**1)  How can I get it to see my partitions?**
2)  If I can get it to see the E: drive, will Ubuntu set up the dual boot automatically, or will I have to set up 'grub' that I've read about?
3)  The other issues that I foresee might come along such as accessing the NTFS partition later ... I'll deal with later.
4)  I understand that entering 'terminal instructions' may be necessary but not sure where to do so.  I don't see the equivalent to a Start|Run option.

Thanks.


*(Throwing in some extra phrases to help Searches down the road:  unrecognized hard drive, doesn't see partitions)*

---

### Post by dunklegend on 2006-09-06
Start the live cd and you once inside you can use the linux partitioning program (Gparted I think it's called).
I had a lot of problems with the partitioning until I did that based on somebody's recomendation.

---

### Post by LeslieL on 2006-09-06
I've done this several times but it's been awhile so I'm a little foggy on the details. 
I have WinXP on one partition (FAT, not NTFS, but that doesn't make much of a difference), and my documents and other stuff I don't want to lose on another FAT partition so both Windows and Linux can write to it. The rest of my hard disk, as far as Windows knows, is healthy and available - I didn't format it under Windows.
When you're installing Ubuntu you come to a point where the installer offers to take over the whole disk or let you tell it where to put things. If you choose to do it yourself, you'll see your various partions called hda1, hda2, hda3, etc. In my case, the Windows C partition is hda1, the docments partition is hda2, and I put Linux on hda3. 
If you're not seeing these partitions, I don't know what to do (but I'm sure someone else does & will answer soon). 
When you install Ubuntu the grub boot loader will be set up automatically and you'll be able to choose to start Ubuntu or Windows. You don't have to fool around with grub unless you really want to. 
I think Ubuntu makes it easy to access NTFS partitions. Not having one, I don't know. At worst, you'll have just read access. 
Don't worry, it will all work out okay.

---

### Post by scantellay on 2006-09-06
I think that your best bet would be to have Ubuntu start the install and when the sereen comes up and asks you if you would.

1) Repartition Hda1
2) Use the free space 
3) Manuel partition 

Go with option 3 and it will take you to the graphical partition tool where you will be able to see all of your partitions and make the slection as to which one you want as / , /home , and swap. make your slections but be carful not to do anything to your partition with Windows on it. 

Good luck and welcome to Ubuntu

---

### Post by geezerone on 2006-09-06
Welcome to Ubuntu. I have a dual boot system and found [ this ](http://video.google.com/videoplay?docid=-6104490811311898236) useful with Windows already installed. I plan to install it on another PC and set aside about 16GB for this with Windows taking virtually all the space available.

The GRUB loader will default to booting Ubuntu by default so you will have to add "default=3" at the top of the list if your Windows install ("menu.lst" in the /boot/grub folder)is the 3rd one mentioned; believe you count the "title" lines to find out how far down it is and therefore what number to use.

---

### Post by geezerone on 2006-09-06
.

---

### Post by xanderificus on 2006-09-06
Thanks for the quick replies, folks.

I've rebooted into the LiveCD.  Once again, gone into Installa and getting the same options.  It's recognizing my main 60gb drive, second 20gb, and showing the Manual Edit choice.  When I opt for #3, I'm still getting "unallocated" for the entire drive.

FWIW, when I go into the Administration menu and go "DISKS", it's showing 4 drives:  hda, hdb, unionfs, and tempfs.  Each one of them has a "There aren't any known partitions" message.


New thought:  I've cleared the E: drive of files but haven't formatted it or removed it's partition.  Should I?  Would Ubuntu have an easier time recognizing space that's completely unallocated?  (I would expect it shouldn't be needed as it should be more intuitive than that).

---

### Post by petri on 2006-09-06
There are two good places to go.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

The latter is aysius who is quite often on these forums.

---

### Post by xanderificus on 2006-09-06
The image from the Psychocats page is exactly what I'd be expecting to see...**_but don't._**
[IMG]http://img155.imageshack.us/img155/3233/w2u302wy.png[/IMG]


Would I be better off burning an older LiveCd for this purpose?  Is it a glitch with the latest release?

---

### Post by Rumor on 2006-09-06
Two thoughts. 
One: When you go to manually partition your disks, are you toggling between drives in ther upper right hand corner of gparted's screen?

What file system is currently on your e: drive? You say you haven't formatted it. I presume it is not unformatted, correct?

Two: I'd recommend downloading the gparted live cd and using it to set up your partitions. Create two partitions on your current e: drive. One for swap (no more than 2 gb) and the other for / (you can also set up a seperate partitions for /home if you wish.

You can grab gparted live cd here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then you can proceed with the install by assigning the new installation to the respective partitions. 

Hope this helps.

---

### Post by xanderificus on 2006-09-06
The E: drive is empty of files and still rests as FAT32.  I haven't yet **re-**formatted it or removed it's partition.

Right now, when I get to the 'manually edit' screen, it shows either/both HDs as being completely unallocated (they're not).  


I'll boot back to XP and try the GPedit ISO.

---

### Post by msandersen on 2006-09-06
> **xanderificus said:**
> I've looked through the forums and tried to help the learning curve but I'm not as successful as I'd like to be.  :D 

BACKGROUND:  I've got my main HD partitioned as a C,D,E,F.  The C is NTFS and is my WinXP partition.  I've cleared off the E: drive where I plan to put Ubuntu as a dual boot.  (I hope to make Ubuntu my -main- OS and reserve XP for those tasks that don't port over.)

PRESENT DAY:  I boot up the Live CD (Dapper) and try the Install.  It, however, doesn't find any partitions on the HD, just the full thing.


I accept that setting up a dual boot, and installing another OS can screw up my main partition but I'll accept those risks.  I would like some input from folks who know better what they're doing than I.

**1)  How can I get it to see my partitions?**
2)  If I can get it to see the E: drive, will Ubuntu set up the dual boot automatically, or will I have to set up 'grub' that I've read about?
3)  The other issues that I foresee might come along such as accessing the NTFS partition later ... I'll deal with later.
4)  I understand that entering 'terminal instructions' may be necessary but not sure where to do so.  I don't see the equivalent to a Start|Run option.

Thanks.


*(Throwing in some extra phrases to help Searches down the road:  unrecognized hard drive, doesn't see partitions)*
1) I think the LiveCD has GParted on it (under System->Administration I think). You can have a look if it recognises the partitions. It's the same tool used during installation, so if you can see it here, the installer should too.
The key is to choose Manual install/partitioning, which lets you edit your existing partitions. It's a good idea generally to have at least 3 partitions for Linux, at least that is the custom.
One for Root (/), the System itself, one for Home (/home) which is your personal files (so you can reinstall without affecting you files), and one Swap partition, which is a special Pagefile partition. Generally the latter is 1-1.5 times your RAM, much as the Windows pagefile is. For the Root (system) 4-5 Gb seems enough, depending how many apps you install. 
I've always partitioned with Partition Magic beforehand, so it's simply been a matter of choosing the partitions for root, Home, and Swap.
Personally, because I'm a little paranoid about the new installer (anything new is more likely to have bugs), I used the Alternate CD which has the old Text installer. But if you're new, that's a little less friendly.

2) Yes Ubuntu should see your Windows installation and set up the Grub bootloader (GRand Unified Bootloader) with both. Linux doesn't use letters for partitions, it uses hda for the 1st disk, hdb for the second etc, and hda1 for the ist partition on the 1st disk, hda2, hda3, etc, and hdb1-n for the 2nd.

3) The Linux kernel currently has read-only access to NTFS partitions built-in. Ubuntu automatically detects your NTFS partitions and "mounts" them. They'll appear on your Desktop and under the Places menu. Work is currently underway for a full read-write driver, currently in Beta. It will be available from the [Linux NTFS project](http://www.linux-ntfs.org/) (the ntfsprogs package in the Ubuntu repositories will eventually be updated when its stable). If you really need write support, you can look for the Beta test driver called ntfs-3g here in the forums [here](http://www.ubuntuforums.org/showthread.php?t=217009).

4) The Terminal is located in Applications -> Accessories. 
Hopefully Linux will eventually mature enough to make it unnecessary for any operation, and become a matter of choice, like it is in OSX. KDE is further along than Gnome on that point.

---

### Post by msandersen on 2006-09-06
If neither Gparted/QTParted or the installer sees your partition layout (especially the latter, of course) then it is dangerous to proceed. Whatever you used to partition your disks with may not have left a completely clean partition table, at least not to the above's satisfaction.

---

### Post by xanderificus on 2006-09-06
Just plain FDISK :(

---

### Post by xanderificus on 2006-09-06
Hmmm...  I thought I'd see if that state of the E: partition was affecting anything so I went back into XP's disk management and deleted it and created an empty Primary partition (didn't even format it).

Now - when I'm back in the LiveCD, the GParted never seems to get past the "Scanning All Devices" stage.  It's been running about 15 minutes so far (and still not done) where it only took a minute before.


If there's a corrupt partition table on *both* hard drives, what's a recommended way to re-write them safely?

---

### Post by Rumor on 2006-09-06
I had a similar problem with an old Dell computer with two physical hard drives in it. I used gparted from the GParted Live CD. It scanned for a very long time before allowing me to change the partitions. If I remember right, it took a good 40 minutes to scan the drives.

Once I was able to access the drives, the partitions were written with no problems and Ubuntu installed and booted fine, automatically recognizing the WinXP install on the machine.

I don't know how to work around the problem you are describing, though

---

