---
title: "GRUB loader error, some questions on repair."
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Cafwin on 2006-06-07
OK, first I've already decided to just get a second box for Linux. Live and learn, I guess. 

Anyway, I need some advice on the current problem I'm having. Right now I'm running the system from a LiveCD. I was running dual boot with XP and all was working well. (Though I haven't figured out how to access my Windows files. More on that in a later thread.)

The way the HDD was set up was 30GB NTFS for XP, 60GB unallocated, 1.5 GB swap, and 30 GB ext3. All was working well. Except that I didn't do the partitioning right when installing Linux. I originally wanted 30 for Linux and 90 for XP. 

What happened was last night while in XP I went to disk management and formatted that 60GB to NTFS to make the space available for use.

But when I went to boot to Linux, I got an immediate error. I didn't write down the exact error ( ](*,)  ), but it was 3 lines and pretty much said there was a problem with grub (removed? not found?) and an error code 17. So somehow formatting the unassigned space as NTFS screwedup the GRUB boot loader.

I ran the CD and tried to install the loader and it took me straight to the partition section. And that's where I'm stuck. Not sure what to do from there. Do I need to just reinstall Ubuntu? That wouldn't be a problem as far as losing anything I've done in Linux, but a guy at work mentioned that may affect my Windows files. He mentioned backing up my XP programs to DVD, but again I'm not sure how to access them. When I click the hd1 icon it says I don't have permission.

So what's the easiest thing to do? Reinstall the loader (how?) Backup XP apps and reinstall? Just reinstall? Or is this something I just need to nuke the Moon over and start from scratch?

Thanks for any help.

---

### Post by nalmeth on 2006-06-07
Try this before resorting to a reinstall
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by Cafwin on 2006-06-07
OK, I tried the stops in the link, but didn't do it right apparently. I should have mentioned I'm new to Linux. (Obviously.)

So I started the install and got the partitioning. I went to the partition (mount?) that has the Linux on it. I clicked on the size and get to the "!!! Disk Partition".  Then I selected "manually partition". Here's where I got lost. 

I entered "/", then went back in and entered "/boot", then entered "/swap" (wouldn't allow just "swap"). So then I went to the save changes and tried to continue, but every time I hit next it just refreshed that screen. No errors, nothing.

I think I understand basically what these steps are meant to do in theory, but no idea what the exact step by step, dumbed down to 5 y/o level instructions are. (As in, what exactly am I supposed to do to "mount" the partitions /, /boot & swap?)

Thanks again

---

### Post by xyz on 2006-06-07
How about this one with pictures and all:
[http://www.ccs.neu.edu/home/jabra/breezy-docs.html](http://www.ccs.neu.edu/home/jabra/breezy-docs.html)

---

### Post by Cafwin on 2006-06-07
[QUOTE=xyz]How about this one with pictures and all:
[http://www.ccs.neu.edu/home/jabra/breezy-docs.html](http://www.ccs.neu.edu/home/jabra/breezy-docs.html)[/QUOTE]

One last question. In images #6 & #7 it relates to erasing partitions. I don't want to erase the Windows partitions, so will selecting erase disk allow me to select the Linux partition? Would I need to manualy edit to erase the Linux partition? A reinstall of Linux is what I was suspecting, but I want to limit the chance of the XP programs and files getting corrupted/deleted.

---

### Post by confused57 on 2006-06-07
This site has some pretty good screenshots of partitioning:
[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

I think when you're setting up the swap partition, after you've done the "/" partition, 
is to select  "use as", press "enter" & you have the option to select it as swap, I think I did it as a logical partition...I got a little "confused" reading through this thread, but this may work...if you haven't tried it already.

I think your initial grub error in your first post, partitioning the "unallocated" space may have changed the root where grub was to look for your linux partition.
You may have needed to have changed it, by pressing "e" at the grub menu and changing root from something like (hd0,1) to (hd0,2),etc...I don't know for sure.

---

### Post by xyz on 2006-06-08
[QUOTE=Cafwin]One last question. In images #6 & #7 it relates to erasing partitions. I don't want to erase the Windows partitions, so will selecting erase disk allow me to select the Linux partition? Would I need to manualy edit to erase the Linux partition? A reinstall of Linux is what I was suspecting, but I want to limit the chance of the XP programs and files getting corrupted/deleted.[/QUOTE]

In image #6, select "Manually edit partition table".  The image #7 will let to pick and choose which partition requires your attention: in your case Linux (press Enter here)...that way you won't touch your windows and you should be safe.
Let us know how it all went!

---

