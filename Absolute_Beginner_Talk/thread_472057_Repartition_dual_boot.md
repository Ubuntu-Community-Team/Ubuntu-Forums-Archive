---
title: "Repartition dual boot"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by afflusso on 2007-06-12
I just installed Feisty and my XP install was left intact, to my relief.  When I was adjusting the partition sizes, I thought the size was for the ubuntu install, but instead it set the size for the XP.

From my 80 GB hard drive, about 40 GB is set aside for ubuntu.
I only have 1.8Gb left on the XP partition, but I would like to have a lot more than that. 

I used the first option for partitioning on the install, and I am pretty sure there are just those two partitions.

How can I safely shift about 20 GB from my ubuntu partition to the XP one?

---

### Post by Bohlio on 2007-06-12
Thats gonna be a little tricky... Im assuming your Ubuntu partition is after your XP partition. And i dont think you can snip off the beginnings of partitions, only the end. My advice to you would be to shrink your Ubuntu partition from the end. Then format that extra space for shared media storage and what not. You can format it pretty much anything, Fat32 is natively readable and writable in both OS's, NTFS is readable and writable in both OS's (with NTFS-3D), and EXT3 is readable and writable in both OS's (cant remember what its called but im using it) If you move all your videos and songs from your XP partition onto your shared one, that should clear up some room

EDIT: Or you could delete your Ubuntu partition, Add whatever space you want to your ubuntu partition, Then reinstall, selecting the empty space.

---

### Post by afflusso on 2007-06-12
Yes, the ubuntu partition is after the XP one.  This is my first time using ubuntu, so I'm not sure what to do.  I would like to add room to the XP partition because there aren't too many files I can trim (mostly a lot of apps installed).

Is it not possible to increase the size of the XP partition without risking any problems?

---

### Post by Bohlio on 2007-06-12
I dont think you can, but I may be wrong, Since Ubuntu Is directly after your XP, All the ubuntu files are stored at the front end of that partition. What you want to do is take away that front end and add it to XP which may cause some problems. I dont know for sure, but there might be a tool out there that can safely reposition your data and then partition that space, But I dont really know.

Edit: Im sorry man, I guess Gparted can do just that, I was under the impression that it couldnt :) Sorry :-P Apparently it will just take a loooonnnng time :-)

---

### Post by afflusso on 2007-06-12
I don't mind if I have to reinstall ubuntu, I just don't want XP to be messed up at all.

How do I run Gparted to correctly do this? Is it on the live cd or something?

---

### Post by Bohlio on 2007-06-12
boot to your LiveCD, Then in the terminal, Type "gparted" that'll bring up a GUI for you to work with.

---

### Post by afflusso on 2007-06-12
Here is the gparted screen I have now. I really don't want to mess anything up, so I want to make sure I do it right.

What's my next step to take about 20GB from sda2 to bring to sda1 (XP)?

---

### Post by Bohlio on 2007-06-12
Yes, You need to shrink sda2 from the **left**, and then expand sda1 to the **right**.. All you do is click on the partition you want to edit, then hit the resize button, Then drag the side that you want to move, Gparted is really user friendly in this way. Good luck! :-)

Oh, and make sure you are running from the live cd :-)

---

### Post by afflusso on 2007-06-12
Thanks. I can only shrink sda2 from the **right**, and I don't want to do that unless I know that it will also shift it over to the right so that sda1 can be expanded.

Anyone know how to do this, or if I should indeed shrink sda2 from the **right?**

---

### Post by Bohlio on 2007-06-12
It wont let you shrink from the left?? I just opened Gparted and checked, and I could shrink from the left, you just drag the arrow over. Im a little confused...

---

### Post by afflusso on 2007-06-12
Here is what the window looks like when I select sda2 and click Resize/Move.

I can only drag it from the right.

---

### Post by Bohlio on 2007-06-12
Im sorry, but i dont know why it is doing that... Mabye you cant do it with ext3 partitions, I had mine mounted so i was looking an a Fat32 for referance...  

To go a different route... How much space on your XP partition would you be able to free up if you moved all your music, videos, pictures, and documents onto a "shared" partition. That way, You could Shrink Ubuntu from the right, Then make a new partition just for your media files that you can access from both Operating systems. The only problem I can see with that is that the Zune Meda Player doesnt allow you to have your library on a different drive, but you might not even use that so it wont be a problem...  What do you think of the shared partition Idea?

---

### Post by afflusso on 2007-06-12
I would definitely try the shared partition if there isn't an alternative, but I think I'll wait to see if there is some way to fix the problem by just increasing the size of the NTFS partition.  I could probably clear up a few gigs, but I usually like to have over 10 available, which I can't do.

I can wait to see if there is a way to do what I want, and if there isn't, I will do the fat32 thing in a few days. Thanks a lot for all your assistance.

---

### Post by Bohlio on 2007-06-12
Yah, No problem :-) This community is extremely helpfull, So If you just wait a while, someone else is bound to pop in on this thread and try and help :-) Im surprised no one else has already! If you need help doing the shared partition, Just post back in this thread and I'll be glad to help you sort that out. It doesn't have to be FAT32 either, You could go with something more stable like NTFS or EXT3, Its all about your preferances :-) Good luck and i hope you get it worked out!

---

### Post by bone43 on 2007-06-12
If you want to reinstall ubuntu i think you need to delete the swap and then sda2 resize your windows partion from the right and leave the rest free space and tell ubuntu to use the free space during install?

---

### Post by afflusso on 2007-06-12
bone43, I don't know why I didn't think of that. I'll try that now.

How do you delete the swap? it won't let me.

---

### Post by Bohlio on 2007-06-12
Oh, I didnt know that you would settle for reinstalling Ubuntu :-P  I dont think you even need to delete the swap, but if you do, It shouldnt be too hard during install. Just run the LiveCD, Click on install, Go through that, Then go to manual partition. Once in that, you should be able to delete the ubuntu partition, expand the XP partition, then install ubuntu to the empty space :-P, I dont think you need to delete the swap partition, Just select it as your swap. It shouldnt be too hard. If you do get stuck, all you have to do is hit cancel and it'll not change your system at all. Im pretty sure It only changes the hard drive once you accept all the partitioning.

---

### Post by afflusso on 2007-06-12
I deleted the ubuntu installation and started the new install.  I went to manual config. I'm not sure what to do now. I have my 30GB NTFS and 40GB of empty space. 

How do I resize the NTFS?

---

### Post by Bohlio on 2007-06-12
cant you do it with the installers partitioner?? If not, just run Gparted to do it. It doesnt matter which you do, as long as you get rid of your current ext3 partition, resize your NTFS, and then use the empty space.

---

### Post by afflusso on 2007-06-12
There's no option in the installer's partitioner to change the size of the NTFS.  I just realized that I could maybe just create the ubuntu partition from about 15 gigs of the empty space, and then use gparted later. Does this sound good, or is there a way to resize the NTFS from the installer?

---

### Post by bone43 on 2007-06-12
> **afflusso said:**
> I deleted the ubuntu installation and started the new install.  I went to manual config. I'm not sure what to do now. I have my 30GB NTFS and 40GB of empty space. 

How do I resize the NTFS?

Sorry was away from the pc go here read the guide for manual install..

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

Also you could do a gui install but dont forget to resize your MS 30GB! :)

---

### Post by afflusso on 2007-06-12
The problem I'm having is that when I hit enter like it says on the walkthrough, there is no option for size of the NTFS, just "use as" and "mount point."

Is it not possible to make the NTFS bigger? Otherwise I guess i'll have to make a big fat32 (no pun intended).

---

### Post by Bohlio on 2007-06-12
Lol, Big Fat32 he he!
Anyways, If you cant do it with the installation, do all of the partitioning with gparted , ***then*** install it, then you should just be able to select your ext3.

---

### Post by antoz on 2007-06-12
Use the Live CD and delete the ext3 partition then resize your windows partition to the size you want.
In the empty space you can then create your new partition ext3 again make sure you remember the exact size and number and then go back to install. Choose manual install and use that partition for your install "/" and the existing swap partition for "swap" **[COLOR="Red"]Very important these 2 are the only ones to be checked to format[/COLOR]**

PS: You could create a separate home partition helps later if you reinstall. A couple of good links
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

### Post by afflusso on 2007-06-12
I just decided to create a fat32. antoz, the problem was that it wouldn't let me resize the ntfs after i deleted the ext3 even though there was empty space. 
All i need to know is the mount point for the fat 32.


Note: on the screenshot, the ext3 mount point is "/"

---

### Post by Bohlio on 2007-06-12
You make your own Mountpoint, In your normal Ubuntu, type in the terminal... ```
sudo mkdir /media/(name you want)
sudo mount /dev/sda6 /media/(Name you want)
``` That should be it to mount it, Ill have to check on what you put in the fstab, hold on a sec. :-)

Edit: Alright, Im pretty sure this goes in your fstab ```
/dev/sda6	/media/(name you want)	vfat	defaults	0 0
```

---

### Post by afflusso on 2007-06-12
I'm not sure what all that is.  I don't have normal ubuntu installed yet.  I am in the installer and I just need to know what the mount point is for the fat32. Should it be "/"? not sure.

---

### Post by antoz on 2007-06-12
Check through the links I gave you before ther are very good instruction for mounting partitions and adding them to the fstab. It needs to be done in the terminal. Just copy and paste the commands that way you won't make any typo errors. In case you don't know in Ubuntu select what you want to copy then click the wheel on the mouse to paste.

---

### Post by antoz on 2007-06-12
Don't mount it as "/" I think you could just call it whatever you want, like share or fat. If you have created this partition before it should not really need to be formatted again.
Also if it does not mount during the install it is not a problem you can do that after.

---

### Post by Bohlio on 2007-06-12
Yah, Your Fat32 is for storage, pick whatever mountpoint you want. Your ext3 needs to be "/".

---

### Post by drowner on 2007-06-12
If I were you

I would delete the ubuntu partition

then use windows the make the NTFS partition bigger

then reinstall ubuntu into the free space.

No fuss.

---

### Post by Bohlio on 2007-06-12
> **drowner said:**
> If I were you

I would delete the ubuntu partition

then use windows the make the NTFS partition bigger

then reinstall ubuntu into the free space.

No fuss.

lol dude... Im pretty sure he just did that :-P

---

### Post by drowner on 2007-06-12
> **Bohlio said:**
> lol dude... Im pretty sure he just did that :-P


Did he?

I thought he tried to do it using the Ubuntu partitioner.

What i mean is to use a windows app to repartition it.

---

### Post by afflusso on 2007-06-12
No, I didn't use windows. I just tried to install ubuntu with a fat32 and I got a fatal error with the grub installer.  
When I boot it without the cd, it says grub loading... error 17.

Hopefully my XP is still ok. I guess I should have stayed with what I had before. I'm going to have to put this problem off until tomorrow.

Thanks to all who helped.

---

### Post by Bohlio on 2007-06-12
Oh I apoligize, I thought your main point was that he reinstall, Not use the windows partitioner :-P.

You made your ubuntu partition a FAT32? and what is your fatal error? Just to clear up a little confusion, exactly what partitions do you have now and what format.

---

### Post by antoz on 2007-06-12
Provided your NTFS partition was not checked during the install it should still be there. If you need to boot into Windows before you fix grub you will have to retore your mbr you can do that with your XP CD it will get rid of grub alltogether but of course will not help getting into Ubuntu for that you will have to fix grub or reinstall again.
Herrmans link I gave you earlier has tutorials about all that.

---

### Post by Bohlio on 2007-06-12
Well tomorrow when you try to sort this out, Boot to your LiveCD and check out your Partitions, As long as your NTFS partition is there, Chances are that its %100 ok, I wouldn't worry about it. I assume that you have a NTFS partition for windows, then an ext3 partition for Ubuntu, then a FAT32 partition, then a SWAP partition. If thats what you have, then you probably did it right. I've seen plenty of threads around here about the Grub error 17, You should be able to find a fix for that. If you need anymore help, come back here and we'll be glad to help :-)

---

### Post by antoz on 2007-06-12
Yes agree with Bohlio, one thing I noticed the screenshot you posted earlier was during the install if you want to do anything with partitions it is better with the live Cd to go System->Administration-> Gnome Partition Editors maybe this is why you could not resize your NTFS partition earlier.
 I purposely booted with the Feisty Cd just now to try it out all you have to do first is click unmount,  since I noticed feisty automatically mounts all the partitions when you open Gnome Partition Editor, the Dapper live CD does not do that.
I am sure you will get there, my install was not problem free either but managed in the end with all the help on this forum.
Good luck, A
PS: I attach a screen shot of my partitions taken with the live CD you could post one here tomorrow to see what you got.

---

### Post by Bohlio on 2007-06-12
A tiny bit off topic but... What is the "Extended" partition and why does it encompass all the linux partitions.

---

### Post by antoz on 2007-06-13
Basically you can only have a certain number of primary partitions (I think it is 4) but as many logical partitions as you want residing in an extented. I my case there are 2 primary 1 (sda1) for windows and one (sda3) for the linux install, the others are all logical sda8 is my home partition. I suppose I could have made swap into a primary, sda6 is a fat 32 for sharing, sda5 is where I have my documents in windows; linux can install in a logical partition no problem but windows needs to be a primary.

In a nutshell if you want to have more then 4 partitions all up you need to create an extented one first and then add logical partitions inside it.

---

