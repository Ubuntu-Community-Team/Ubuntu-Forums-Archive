---
title: "Changing Windows and Ubuntu on physical harddrives possible?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Lofticus on 2005-11-30
Hi People,

I'm pretty new so maybe my question sounds really stupid, but please take time to read it anyways (-: It would help me a lot!

So, I got 2 Harddrives. One with 120 gigs and one with 20 gigs.

Well, I don't really like windows but it's not possible to get rid of it the whole way.

Ok first things first, I installed Ubuntu on my 20 gigs for the purpose of trying. 

It does well. On my other 120 gigs there's running a huge fat Windows NTFS (bah... h8 ntfs (-: 

So if I would format my Windows, would it be possible to just "switch" my Ubuntu to the - then unused - 120gigs and then get my Windows installed on the 20 gigs w.o. problems?

(I can't get rid of Windows because I need programs like that stupid sony mp3-player program which will allow me to update it with mp3s, because the mp3player itself won't recognize mp3-files, just the stupid sony way, or my Webcam under AIM to chat with people using Mac, or my "&#167;$& Lexmark AOI Printer... u c, it's a bit like a disease heh...)

So if you have an advice, spit it out, I'm eager to hear!

thanks! ;)

[EDIT: Oh, hell, almost forgotten, is there a way to get Ubuntu and Windows to conversate, like writing and reading files under Ubuntu on Windows and the other way back?] <- Important &#178;

---

### Post by basketcase on 2005-11-30
My Advice would be to just back everything up, make sure you have the cd's or download locations available and rebuild from scratch for each OS.  

As far as writing something in one OS and editing it in another.  Open Office in either both OSes or Open Office in Ubuntu and MS Office on your Windows Box.  

Good luck.

---

### Post by Lofticus on 2005-11-30
hehe, I don't like MS Office either, I'm using OOo since 2 years now (-:

But I mean with ntfs there's that restriction that I can only read from, not write to, or not?

So if I pick up Fat32, will I am able to read my Windows Partition?

And what will I have to pick for Ubuntu so that Windows will recognize my Ubuntu partition? Or isn't that possible?

---

### Post by ex` on 2005-11-30
You can ship it all to the other harddrive by using dd, but I can't recall the exact command at the moment, and as you just started Ubuntu reinstalling might be easier?
If you really want to copy it over to the other harddrive, give me a shout and I'll try to find the exact command back for you.

As for conversating between both OS'es / filesystems, you can mount NTFS filesystem on your linux installation with the following commands:

> mkdir /<windowsfoldername>, for example: mkdir /windowshdd
mount ntfs /dev/hdXX /windowshdd

If you don't know which harddrive your Windows hdd is in linux terms, run df -h and try to recognize it from there. It'll probably be either /dev/hda1 or /dev/hdb1, if that's the case and it's there, replace /dev/hdXX with the drive of your choice.

[edit]
Just read your latest post, indeed, only NTFS-read is supported, there *is* a NTFS-write module which seems to work okay, but I'd only use that as a last resort. If you want to mount a fat32 filesystem simply replace 'ntfs'  with 'fat32' (or heck, even nothing will work as it'll auto-detect it) in the above command and you're good to go.

There *is* an ext3-explorer out there on [http://sf.net/](http://sf.net/) for Windows , so that should work, too. (If you're using ext3 ofcourse).
[/edit]

---

### Post by squirrelyosis on 2005-11-30
This is definetly doable.  I used Acronis True Image, you can make an image of either your Ubuntu install or your M$ install the same as you would with Norton ghost.  Save the images to the opposite hard drives, and figure out a way to swap the images to get what you want.  I have backed up and restored images in Breezy so I can guarantee that works an M$ definetly will also.  Just make sure you backup all partitions on both, just select them all.  Also the MBR's might get screwed up so you might have to reinstall grub (search the forum for that one) or repair your windows install from the cd.  Just make sure you backup everything important! 

On you other question,  Ubuntu can mount and read and execute from NTFS/Windows, but it cannot write to it.  I'm not sure about Windows reading from Ubuntu(ext3, reiserfs, whatever it is). Well, i guess it can then!  But I would stay away from writing to NTFS

---

### Post by kwaanens on 2005-11-30
There is an option, and I've done this myself, sort of. I could have guided you easier if you provided your partition table.
What I mean by "sort of" is that I moved the Ubuntu partition, but I never did anything to the NTFS one except resize it. But I think it will work.

If you want to do this, you'll need to have enough free space, to use for a temporary space.

First, defrag your windows partition. (to make sure that all data is stored at the beginning.

Now, you need to use a partition manager to resize the NTFS-partition. I've always used qt_parted which ships on [sysresccd]("http://www.sysresccd.org"), but I'm told that it is doable with gparted on the Ubuntu Live CD as well. I haven't tried this, but you're going to need Ubuntu Live anyway, becuse Gparted can duplicate ext3-partitions, and qt-parted can't.

Now, shrink the NTFS file system. I don't know where your partitions are placed, but this is the time to plan your actions.

Copy the partitions where you want them. When you're done, reformat the old space(s) and decide whether you should be using them as separate storage partitions or whatever. It might be a good idea to keep them until you have booted in your new system, and see that everything works. (Remember, if you keep them, that you will boot into your old systems, you need to edit your boot commands when entering Grub.

Remember to make a note of where your partitions gets placed, bacuse you manually have to enter the commands when you boot in to grub. (E.g. Ubuntu may have been placed at hda2, now it may very well be at hda6. Check your system)

The windows chainloader thingie is set up in /etc/grub/menu.lst like this: ```
root            (hd0,1)
``` where the numbers mean "first partition","last partition to be skipped". On my system it is number 2 as you probably understood.

Also you may need to change /etc/fstab. Finally I also had to reinstall ati-drivers for 3d to work again, although I have no idea why.

I had some hickups with Ubuntu, meaning that she took a while to understand

Last, but not least: BACK UP YOUR SYSTEM!

I tried this myself. I didn't hear about any experience with this beforehand. So there are no guarantees that your system will be usable.

Good luck!

- Ketil

---

### Post by Lofticus on 2005-11-30
[QUOTE=ex`]There *is* an ext3-explorer out there on [http://sf.net/](http://sf.net/) for Windows , so that should work, too. (If you're using ext3 ofcourse).[/QUOTE]

Anyone knows the complete name of the ext3-explorer?

I searched for it under sf.net but I didn't find anything.

To the changing thing: I want to erase my M$-Partition, so I don't really want to backup or so. So I have to format it to ext3 (because of that windows ext3-explorer) and then I can just copy "/" to my newly generated ext3 Partition, will that work? I don't really care for that Windows-stuff because there's not much what's important (windows tends to get reinstalled after a time). 

ATM hda is Windows and hdb is Ubuntu. So if I leave hdb as it is and just overwrite hda with hdb will that work?

My MBR is on hda, but Ubuntu on hdb would still boot, wouldn't it? Or will the MBR be affected if I repartition hda?

*getting confused*

Greez Lofticus

---

### Post by kwaanens on 2005-11-30
Did you install Grub on your MBR?
I'm not sure, but I don't think Gparted will touch your MBR. I'm assuming that your /boot partition is pretty important to keep in place. Other wise you'll have some tweaking to do.
I don't know too much about this, so someone else should confirm my thoughts.

If you boot with Ubuntu Live you get the possibilty to duplicate your ext3 partition if that's what you'd like to do. (The point is that you can't boot up your partitions, and then format them and stuff.)

Sorry if this is unclear, as I am obviously unable to make myself understood today :)
If you have concrete questions I'll try to answer them! (If I can...)

- Ketil

---

### Post by Lofticus on 2005-11-30
My MBR is GRUB'bed

so will repartitioning of hda affect grub or my mbr?

:???:

---

### Post by kwaanens on 2005-11-30
I don't think so.
But if your MBR should be affected in a bad way, I'm guessing you could boot with your Ubuntu installation CD and set it straight again.

- Ketil

---

### Post by Lofticus on 2005-11-30
Seems that it would affect my MBR, how can I repair GRUB afterwards?

Lofticus

---

### Post by squirrelyosis on 2005-12-01
From what I've read its'

## Booting from Disc and reinstall GRUB
At CD prompt
boot: rescue
then...
grub-install /dev/hda

---

### Post by daller on 2006-01-08
[QUOTE=Lofticus]Anyone knows the complete name of the ext3-explorer?

I searched for it under sf.net but I didn't find anything.

To the changing thing: I want to erase my M$-Partition, so I don't really want to backup or so. So I have to format it to ext3 (because of that windows ext3-explorer) and then I can just copy "/" to my newly generated ext3 Partition, will that work? I don't really care for that Windows-stuff because there's not much what's important (windows tends to get reinstalled after a time). 

ATM hda is Windows and hdb is Ubuntu. So if I leave hdb as it is and just overwrite hda with hdb will that work?

My MBR is on hda, but Ubuntu on hdb would still boot, wouldn't it? Or will the MBR be affected if I repartition hda?

*getting confused*

Greez Lofticus[/QUOTE]

What exactly do you mean by an explorer?

This is the driver-project:

[http://e2fsprogs.sourceforge.net](http://e2fsprogs.sourceforge.net)

(Installing and enabling the driver will make ext2/3 drives work under windows!)

To be more precise:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

...And YES it DOES support ext3!!!

---

### Post by devnulljp on 2006-01-10
It's called 
[e2fs]("http://e2fsprogs.sourceforge.net/ext2.html") and it works really well.

[QUOTE=Lofticus]Anyone knows the complete name of the ext3-explorer?

I searched for it under sf.net but I didn't find anything.
...[/QUOTE]

---

