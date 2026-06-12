---
title: "How to create Ext3 partitions?"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Dingen on 2006-01-29
Hello. I just installed Ubuntu 5.04 on a computer that formerly ran on Windows XP. There are 3 drives in the machine, which were all partioned as NTFS.

Now I want to completely erase them and make Ext3 partitions instead. How do I do this? The main drive (hda) is already Ext3 because of the installer. But what should I do to get the other drives (hdb and hdc) as Ext3?

I'm completely new to Linux and I really hope you can help me out.

---

### Post by ubuntuuser on 2006-01-29
I think the easiest way for you is to install gparted and do it there. It is pretty self-explanatory, just like PartitionMagic, for example.

---

### Post by Dingen on 2006-01-29
[QUOTE=ubuntuuser]I think the easiest way for you is to install gparted and do it there. It is pretty self-explanatory, just like PartitionMagic, for example.[/QUOTE]

Hey, thank you very much. I looked up GParted on [http://ubuntuguide.org](http://ubuntuguide.org) and followed the instructions. It works :)

But how do I access my drives? I don't see them in the Places window :confused:

I plugged in my external drive and it showed up on the desktop and in the Places window instantly. But I can't figure out how to copy the stuff on my external drive to the new Ext3-drives I just created with GParted.

---

### Post by ubuntuuser on 2006-01-29
In GNOME, open System -> Administration -> Disks. There, select your disks and enter a mountpoint.

---

### Post by Dingen on 2006-01-29
[QUOTE=ubuntuuser]In GNOME, open System -> Administration -> Disks. There, select your disks and enter a mountpoint.[/QUOTE]

Thanks again for your fast reply. But I'm afraid I have no "Disks"-option in the Administration-section of the System-menu :(

---

### Post by az on 2006-01-29
If you upgrade to breeze, you will.  The hoary version of the disk mounter was buggy before release and so they removed it.

You can always do it by hand using the command line

make a mountpoint (you only need to do this once)

sudo mkdir /mnt/hdb

and then mount the drive
sudo mount /dev/hdb1 /mnt/hdb

---

### Post by Dingen on 2006-01-29
[QUOTE=azz]If you upgrade to breeze, you will.  The hoary version of the disk mounter was buggy before release and so they removed it.[/quote]

Hmm... okay. Well the reason I'm running Hoary is because the installer of Breezy would freeze when running the partioner. The Hoary installer ran fine, so I used that one instead.

Is it hard to upgrade my system to Breezy? I already upgraded everything using Synaptics Smart Upgrade, but I still don't have the Disks-option described above.

[edit] Ah, I just found this: [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

I'm going to follow these steps. I hope I get the Disks-option by doing this!

> 
You can always do it by hand using the command line

make a mountpoint (you only need to do this once)

sudo mkdir /mnt/hdb

and then mount the drive
sudo mount /dev/hdb1 /mnt/hdb

Ok, I'm gonna try this :) Thanks!

---

### Post by Dingen on 2006-01-29
Ok, I upgraded to Breezy and there's the Disks-option. Whoohoo \\:D/

---

### Post by Dingen on 2006-01-29
Well. It's almost working. I can mount my disks and since I've mounted them in /media I can also see them on my desktop, as I like. But I cannot write to them. It says I'm not the owner and I can't work with these disks. What do I have to do to get ownership?

Oh and by the way, will these drives remain mounted when I reboot my machine? And if not, how do I make it so that it will remain mounted as it is now?

Thanks in advance!

---

### Post by Dingen on 2006-01-29
A friend told me to edit the "/etc/fstab"-thing to get the drives mounted on boot. I tried this and it works, but I still cannot write to my own harddrives :(

This is what I added in the /etc/fstab-file:
```

/dev/hdb1	/home/martijn/hdBig	ext2	rw,user	0	0
/dev/hdc1	/home/martijn/hdSmall	ext3	rw,user	0	0
```

/home/martijn is my homedir and I've created the "hdBig" and "hdSmall" folders.

At first I had "defaults" instead of "rw,user", but that didn't work either.

I'm getting prettty frustrated here :cry:

---

### Post by Dingen on 2006-01-29
Hmm... after searching the internet, I found out the "chown"-command could change the owner of a folder. So I did "sudo chown -R martijn hdBig" and "duso chown -R martijn hdSmall" from my homedir and now I can write to my harddisks.

Is this the proper way to do it? And will my drives remain writeable after a reboot now?

---

### Post by Herman on 2006-01-29
Hello, Dingen, I have been interested in your question, and have been working to help solve it, but you have been one step ahead of me all the way. :-D
I made a similar ext3 partition, named hda11, in a computer here, and mounted it in a directory also named hda11, in /media, with:
```
sudo mkdir /media/hda11
sudo mount -t ext3 /dev/hda11 /media/hda11
``` Then I used chmod to give me access to it,
```
sudo chmod -R 777 /media/hda11
``` I think they will re-mount themselves and remain writeable each time we re-boot. If mine doesn't behave the way I want I'll try your slightly different commands, or visa-versa perhaps, if you need to.
I do know for sure that all my other partitions like fat32 logical partitions, Windows partitions and other Ubuntu installs (Multi booting (eg Dapper)) do auto-mount read and write. 
I didn't realize mounting a seperate ext3 partition would be this much different, other Ubuntu operating system ext3 partitions are mounted pretty much automatically, and FAT32 partitions we are all well practiced with. I have enjoyed this and learned something from it, thanks, :D (Herman)

Edit: The most important thing for having them re-mount automatically each re-boot seems to be having edited /etc/fstab.

---

### Post by Dingen on 2006-01-29
[QUOTE=Herman]Hello, Dingen, I have been interested in your question, and have been working to help solve it, but you have been one step ahead of me all the way. :-D[/quote]

Hi Herman. It's nice to hear someone reply, I almost thought I was doing a monologue here :D 

> 
I do know for sure that all my other partitions like fat32 logical partitions, Windows partitions and other Ubuntu installs (Multi booting (eg Dapper)) do auto-mount read and write. 
I didn't realize mounting a seperate ext3 partition would be this much different, other Ubuntu operating system ext3 partitions are mounted pretty much automatically, and FAT32 partitions we are all well practiced with. I have enjoyed this and learned something from it, thanks, :D (Herman)

Edit: The most important thing for having them re-mount automatically each re-boot seems to be having edited /etc/fstab.

I hope it's working with you now. It's working fine here, but I've really put some hours into it, while it should have been really simple. When I plug my external USB 2.0 drive in, everything just works. But with an internal native-Linux harddisk, I had to configure for hours to get it working. I think that's a really weird situation.

Ah well, at least I got it down now :cool:

---

### Post by mediaservant on 2006-02-03
Does QTparted let me convert an NTFS disk to a linux filesystem without losing any data?  Or is the only way to reformat?  I have lots of DV video files etc. I don't want to erase yet, but I want R/W to the disk....

---

