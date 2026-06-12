---
title: "[SOLVED] Get rid of Mandriva Partition"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Homosuperior on 2008-04-01
About a year - year and a half ago I made my first attempt at switching to Linux with Mandriva. I didn't like it at all and it was way too complicated for my young children, and I was too busy at the time to mess with learning a new OS. So I deleted it (so I thought) and just kept going with windows. Now, about 7-9 months ago, I decided to give it another try with Ubuntu. I LOVE IT! My kids are zipping through it like it's always been there (now I just have to convert my wife). But back to the issue, since I have installed Ubuntu when GRUB starts up I've always noticed that there are my Ubuntu kernels on top, then my windows xp, and then there are "other" Linux programs at the bottom. I thought that maybe it was a failsafe or something along those lines. However I recently started looking a little farther into it and realized that it was Mandriva still hanging around in the background. I have windows and Mandriva on the same smaller hd, and then I have Ubuntu on a secondary larger hd. I'm starting to run out of room in windows (I've been moving stuff into Ubuntu to compensate), but I would like to get rid of Mandriva to free up space on the windows hd. But doing so, I also don't want to mess up anything on windows doing it. Is there a way from Ubuntu that I can delete mandriva, remove the partition and expand the windows partition to the full hd? I have isolated which partitions are which, I'm just still new enough at this that I could seriously mess something up if I start messing around with it without advice.

---

### Post by c-ron on 2008-04-01
Use the LiveCD to run gparted to delete the old Mandriva parition. You can resize the Windows NTFS partition to fill the disk afterwards. 
See: [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

You will also have to edit the /boot/grub/menu.lst file to remove the old GRUB entries for Mandriva.
It's a text file, so restart after applying changes to your partition table, boot up Ubuntu and type from the terminal:


```
sudo nano /boot/grub/menu.lst
```

It sounds like the Mandriva entries were displaying AFTER the Windows entries when your computer starts, so it's more than likely that those Mandriva entries are at the very bottom of the file. Isolate the ones for Mandrive (starting with: title Mandriva) and take that block out. Save the file (Ctrl+X) and say 'yes' when asked if you want to save. Press enter to save to the default file name (menu.lst)

---

### Post by rsambuca on 2008-04-01
The simplest method is to just reformat the Mandriva partition as NTFS.  Then re-assign the partition as your Documents folder from Windows.  That way, you don't have to bother with deleting the partition and expanding your Windows partition.  Since it is on another hard drive from your Ubuntu partition, you can easily does this from within Ubuntu, using gParted, which is in Synaptic Package Manager.  It is very easy to use.  

If you have any problems, I am sure either I or someone else can help you out.

---

### Post by Homosuperior on 2008-04-01
Will I need to get an ISO disk for hardy (I just upgraded via updater), or will the gutsy ISO work?

---

### Post by rsambuca on 2008-04-01
You don't need either iso to do what you want.  You can just use the program called gParted.  If you open Synaptic Package Manager, search for gParted and install it.  You can then use this program to do what was described in previous posts.

---

### Post by c-ron on 2008-04-01
The Gutsy LiveCD will work fine for this.

---

### Post by c-ron on 2008-04-01
> **rsambuca said:**
> You don't need either iso to do what you want.  You can just use the program called gParted.  If you open Synaptic Package Manager, search for gParted and install it.  You can then use this program to do what was described in previous posts.


PLEASE NOTE: You cannot modify partitions on hard drives that are MOUNTED!
That's why I suggest rebooting with the LiveCD so that no partitions will be mounted.
If you really want to do this from Ubuntu, you can, but make sure all partitions on the drive you want to modify are unmounted first!
```

sudo unmount /dev/(partition)
```

Repeat for each partition on that drive and then run:

```
sudo gparted
```

---

### Post by rsambuca on 2008-04-01
> **c-ron said:**
> PLEASE NOTE: You cannot modify partitions on harddrives that are MOUNTED!
That's why I suggest rebooting with the LiveCD so that no partitions will be mounted.
If you really want to do this from Ubuntu, you can, but make sure all parttions on the drive you want to modify are unmounted first!
```

sudo unmount /dev/(parttion)
```

Repeat for each partition on that drive and then run gparted.

I know that the drives have to be unmounted.  Since it is another drive from Ubuntu, you can do the unmounting and reformating entirely from within gParted.

---

### Post by c-ron on 2008-04-01
> **rsambuca said:**
> I know that the drives have to be unmounted.  Since it is another drive from Ubuntu, you can do the unmounting and reformating entirely from within gParted.

That was for Homosuperior. Not you. :) Plus, gparted doesn't always unmount the drives.

---

### Post by Homosuperior on 2008-04-01
Okay, I have it downloaded and installed gParted from Synaptic, but I can't find a way to start it anywhere. Do I need to run it from Terminal?
Also, thank you both very much!

---

### Post by Duck2006 on 2008-04-01
System>>Administration>>Partition Editor

I like using the live cd of parted magic, but gparted will do what you want to do.

---

### Post by c-ron on 2008-04-01
> **Duck2006 said:**
> System>>Administration>>Partition Editor

Or from the terminal:

```
sudo gparted
```

---

### Post by Homosuperior on 2008-04-01
Got it! Thanks, wasn't paying close enough attention. Now, even though when I was installing Gutsy it asked where I wanted to install, and I chose to use the entire drive of my secondary hd, which I verified (so I thought) by the disc space. But now, running gParted, it looks like everything is on the primary hd with just linux swap, extended and ext3. I found my entire Ubuntu section on hda (supposed to be on hdb right?). Is there a way that I can move Ubuntu to hdb without messing stuff up, or am I going to have to back everything up and start from scratch again?

---

### Post by Homosuperior on 2008-04-01
Okay, maybe not. Maybe I'm still looking at Mandriva stuff. Lemme look again.

---

### Post by Homosuperior on 2008-04-01
Okay, I got all that taken care of, but now it won't let me do anything with the unallocated space or with hda period. Plus there is an ! icon with a triangle around it next to the windows partition stating that it is "unable to read the contents of the file system! Because of this some operations may be unavailable." Any advice there?

---

### Post by rsambuca on 2008-04-01
Have you completely shut down Windows?  If you have left it in hibernate mode, then it can definitely cause problems with moving/resizing.

Edit:  Perhaps you can post a screenshot of your gParted screen so we can see exactly what is going on here.

---

### Post by Homosuperior on 2008-04-01
I double checked windows and it was shut all the way down correctly, so that is not the issue.

---

### Post by c-ron on 2008-04-02
Try a good old disk check and defrag from Windows first.

---

