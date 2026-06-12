---
title: "Resizing A Linux Mint Partition?"
date: 2012-04-07
forum: Any Other OS
---

### Post by ken0069 on 2012-04-07
Linux Mint v12 x64 upgraded from Ubuntu 10.10.  This install was originally on a 20GB hard drive and yesterday I used Clonezilla to move Mint to an 80GB drive so I can install Virtual Box then Windows inside that.

I'm having problems trying to get Mint to use the entire 80GB on that drive as that partition is only like 20GB.  I've tried Mint LIve using GParted but all I seem to be able to do with that is shrink that original 20GB partition.  The remaining 60GB on that drive is listed as "Free" and is not formatted with anything at the moment.  

So does anyone know how I can make use of this entire drive without having to format and reinstall Mint?  I have a limited use 3G USB Data Card connection so I really don't want to have to download all those updates over again.

Any help?

Thanks PPL,

Ken

---

### Post by Basher101 on 2012-04-07
i will write a solution once im done eating in 5 minutes or so..

---

### Post by Basher101 on 2012-04-07
well it took longer than i thought but anyways..

So, if clonezilla does not make it use the whole space, try making a backup with Remastersys. It will compress your current install to a live.iso that you can put on a USB stick and just install your "custom live CD" on that partition. With that, all your settings, programs, changes and whatnot will be preserved and also installed. 

Remastersys has only ONE limitation - Space. The compressed .iso must not be larger than 4 GB, becasue it has to fit a DVD. The install program, ubiquity won't work if you use .isos larger than 4 GB. 

I have so far managed to compress 14 GB. You should move your large files somewhere else for the time being (e.g. downloads, music, movies) as you can just copy them back.

After you managed to create your iso, use the in-built tool in Ubuntu to create a bootable USB stick and install it on the 80 GB partition.

regards

p.s. if you have any questions feel free to ask

---

### Post by ken0069 on 2012-04-07
Questions?  Ok so I have no clue what you are talking about?  :confused:  Sorry.  I can do this partition type stuff on a Windows system with Partition Magic or Acronis Partition Manager but they won't work with this Linux type file system.

I do still have that 20GB drive with Mint 12 still on it?  

So there's no software out there that will allow me to enlarge that 20GB partition out to 80GB??:confused:

Thanks,

Ken

---

### Post by drs305 on 2012-04-07
The LiveCD and Gparted should do what you want.

I can think of 3 things that might have caused problems. The first is to make sure the swap partition isn't mounted (even on the LiveCD). If you see the swap partition in the Gparted partition window make sure it doesn't have a 'keys' icon next to it, which means it's mounted. Unmount the swap partition using the 'swapoff' option. (Right click the partition, then Swapoff)

The second problem could be if your swap partition is between your Ubuntu partition and the free space. If it is, you can delete it or move it to the end of the partition so the free space is touching your Mint partition.

Third, your Mint partition and free space must either be primary partitions or within the extended partitions. You can't join them if they are split between the two.

If you don't understand partitions the best thing to do would be to take a screenshot of Gparted so we can see how your drive is divided.

---

### Post by ken0069 on 2012-04-08
Basher, DRS thanks to both of you for trying to help!!  

DRS you were correct in that the swap was mounted even with Mint Live!  I deleted that as per your instructions then was able to move that partition out as far as I wanted.  

Which brings me to another problem of sorts.  I left 5GB on the end of that drive to allow for creating a new swap since this computer has 4GB of RAM but didn't know exactly how to do that.  I thought that maybe Linux would do that automatically so I rebooted and it seemed to work fine so I went and checked and sure enough, there was NO swap on that drive?  I did a Google search to try to find out how to recreate the swap only to find that most say that it's not needed with computers with 2GB or more of memory.  So, I went back in and just extended that partition to the full capacity of that drive.  Seems to be operating normally at this point so I'll use it like this until or if something goes wrong.

Basher, there's usually more than one way to "skin a cat" and I'm sure there are other ways to accomplish what was done.  I'm not sure where you were going with the ISO stuff and an explanation written down on my skill level (Linux novice) would be appreciated if you have the time or desire to do so.  

And again, thanks for the help guys!!

Ken

---

