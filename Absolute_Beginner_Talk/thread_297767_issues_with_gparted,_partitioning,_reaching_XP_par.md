---
title: "issues with gparted, partitioning, reaching XP partition"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by turtlewars on 2006-11-11
Having installed Ubuntu last week, I can't reach my Windows XP partition and it's driving me crazy.  Attached is a screenshot of gparted that shows the was my partitions are formatted.  When seeking advice a few days ago, I was told to enter code into terminal, but have no idea what that is or where to get to it.  I was also asked if I meant that I couldn't reach XP from startup or if I meant that I couldn't access my NTFS partition while in Ubuntu.  Unfortunately, I can't do either one, and I have no idea what I'm doing wrong or how to add Windows back in.  Please help!

---

### Post by ReaderRat on 2006-11-11
[quote=turtlewars]When seeking advice a few days ago, I was told to enter code into terminal, but have no idea what that is or where to get to it.[/quote]

You can find the original thread by going to the top of the screen and clicking on 'Search' and then clicking on 'Find all your threads'.

---

### Post by ReaderRat on 2006-11-11
Here it is, and it is good advice:
**[http://www.ubuntuforums.org/showthread.php?t=293931](http://www.ubuntuforums.org/showthread.php?t=293931)**

---

### Post by catlett on 2006-11-11
Let's try to manually mount your xp partition and see what happens. Open the terminal and enter the following commands. 
First make a mount point for xp
```
sudo mkdir /media/windows
```
Now we will mount the partition to /media/windows
```
sudo mount /dev/sda5 -t ntfs /media/windows 
```
Now go to ther top panel and enter into Places>Computer>Filesystem>Media>windows when you open the windows folder you should see your XP files.
Post any error. If this works we can make it permanent by editing the /etc/fstab file.
The other question is, when you start your computer and entet the grub menu, is there an option for Windows? Can you boot into windows or is that an issue too.

P.S. Enter this command ```
sudo apt-get install mpg321 vorbis-tools
``` After it is installed you will have the ability to play mp3's and ogg files just by hovering your mouse over them. I saw your files on your desktop, I like to preview or play them off my desktop with the mouse-hovering effect. (Not a 'breakthrough' app but I like it and it impresses your xp friends who have to wait  minutes before wmp opens up :) )

---

### Post by turtlewars on 2006-11-11
The code you posted did seem to relocate my XP folders; however, when I went to view them, I got error "The folder contents cannot be displayed: you do not have the permission necessary to view the contents of 'windows'." 

Additionally, to answer your question, no, I can't access Windows from startup; it doesn't appear in the grub list.  How can I make it so that I might boot into Windows?

Thanks for the music tip.  :P  I'm a fan.

---

### Post by djsroknrol on 2006-11-11
Post your fstab...I don't think that your sda5 mount has proper permissions for you to access it....

To get your windows back in you need to edit your menu.lst file to include it. You can find it in /boot/grub and you can edit it with any text editor. I still run vfat for my legacy equipment, so I can't help you with the lines but read the man for grub in a terminal (type man grub) and you'll find your answers.

---

### Post by catlett on 2006-11-11
Don't worry about finding the files right now, we'll fix that when we make the change permanent. I just wanted to make sure the partition was OK.
I need you to post the output of 3 commands to get the necessary info.
```
sudo fdisk -l
```That will open in the terminal. The next 2 will open up in a text editor, gedit. Just copy/paste out the contents and then close the files. We'll open them back up later.
```
sudo gedit /etc/fstab
```
```
sudo gedit /boot/grub/menu.lst
```
Post the outputs and I'll return the changes needed.

---

### Post by turtlewars on 2006-11-11
first:

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

second:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

third:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Post the outputs and I'll return the changes needed.[/QUOTE]

I'm happy to hear it means that my Windows stuff is still there, at least.  :X  Thanks so much for all of your help!

---

### Post by Bartender on 2006-11-11
How come his 'ntfs' partition is inside the extended partition?  That's not right, is it? 
EDIT: I'm referring to the attachment

---

### Post by catlett on 2006-11-11
> **Bartender said:**
> How come his 'ntfs' partition is inside the extended partition?  That's not right, is it? 
EDIT: I'm referring to the attachment

That's a good point. I am not sure if windows can boot from an extended partition. Hopefully service pack 2 took care of it because if it was an earlier version it would definately be a no go. Let's edit the files and see what happens. I'll post again in a couple of minutes with the entries.

---

### Post by catlett on 2006-11-11
The first edit will be to grub. Enter this to open the file
```
sudo gedit /boot/grub/menu.lst
```
Then paste this to the bottom
```
# This entry is for windows on /dev/sda5
title           Microsoft Windows XP 
root            (hd0,4)
makeactive
chainloader     +1
```
Save and close the file.

Enter this to open the mounting file /etc/fstab
```
sudo gedit /etc/fstab
```
Paste this into the end of the file 
```
/dev/sda5 /media/windows ntfs defaults 0 0
```
Save the file and close it.
Now is the test time. Reboot your computer and select the windows entry from grub and see if it will boot.
After that boot into Ubuntu and try to open the windows folder again. The permissions issue should be taken care of.

---

### Post by turtlewars on 2006-11-11
With a deep sigh and heavy heart, I report that this did not work.  The error I got was this:

root    (hd0,4)

Filesystem type unknown, partition type 0x7
makeactive

Error 12: Invalid device requested.

Additionally, I am still unable to view my windows files through Ubuntu.

Any more ideas?

---

### Post by catlett on 2006-11-11
I am nervous about windows being in the extended partition. How did you create the dual boot. Was xp installed and then you installed ubuntu? How did xp get in the extended partition? If XP's installer did the partitioning it would have made a primary paretition for windows.
What happesn when you try to view the files from windows in Ubuntu?

You double posted the menu.lst before, could you post the output of fdisk for me so I can make sure we have the right partition.
```
sudo fdisk -l
```

---

### Post by bigken on 2006-11-11
use the qparted live cd and set the bootable flag on the ntfs partion ;)

---

### Post by turtlewars on 2006-11-11
how is this done?

---

### Post by bigken on 2006-11-11
if its the gparted idea download and burn iso boot from the cd and select the ntfs partion right click and set bootable flag

---

### Post by turtlewars on 2006-11-11
it's actually pretty complicated.  I installed XP way back when, but when I installed it, I created a partition to keep an amount of empty space free, knowing that I wanted to install Ubuntu later.  When I was then trying to install Ubuntu, I ended up deleting that partition so that I could reformat the empty space for Ubuntu.  I was confused about what it was prompting me to do in creating the partitions, so I ended up creating one, it looks like, that isolates both the Windows XP and the Linux swap partition from the Ubuntu partition.  Is there any way to fix this or somehow delete or otherwise penetrate the outside partition?

```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1218     9783553+  83  Linux
/dev/sda2            1219        3648    19518975    f  W95 Ext'd (LBA)
/dev/sda5            1276        3648    19061091    7  HPFS/NTFS
/dev/sda6            1219        1275      457789+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by bigken on 2006-11-11
I read some where that you can boot from the knoppix cd and transfer your data to a usb device if it loads the ntfs partion this might be your only option as it looks like the windows partion is corrupted :-k

---

### Post by catlett on 2006-11-11
The partition is the correct one so the commands should have worked if everything was fine. 
One issue may be the fact that windows is now in a different partition than when it was installed. Meaning instead of it being C (in windows terms) it is F (that isn't necessaruly correct it is just to show the order has changed)
This is a big issue when boting. XP has a boot.ini file that will have XP on the first partition but it is now on the 3rd partition.
Actually when you look at your screenshot, there is an exclamation piont opn the ntfs. This means gparted thinks something is wrong.

First question, do you have important data on XP? At this point it is better to reinstall both OS's. Everything would be fine if the ubuntu and xp partitions were reversed.
XP on the first primary partiton and ubuntu on an extended partition. Linux can boot from anywhere.
If you have important data, I would start trying to rescue it and then reinstall everything to get it straight.
What error do you get when you try to open thw windows folder? Is it a permissin issue or something else?

I have to run an errand, I'll be back in under an hour and I'll check in.

---

### Post by bulldog on 2006-11-11
Windows need to boot from a primary,only when you have two different windows versions you can put one on an extended partition,as long as there's room to place the boot programs on the first partition.

The way I see it is to copy the important data from the disk and start from scratch,or buy a second disk to put windows on.

I would be very surprised if this configuration will boot windows.

---

### Post by turtlewars on 2006-11-11
Apparently all is not lost, at least according to GParted; upon opening it to tell you that you're right and that it doesn't recognize XP at all, it came up with a different image than what I've been looking at.  I'm attaching it; as you can see, the data in the XP partition is no longer unreachable and unacknowledged, I simply don't seem to have permission to access it.

I see your point about the booting issues, and unfortunately have absolutely no idea what to do.  Is looking for a file system in one place instead of another something that can be changed?

That GParted has changed gives me hope, though.  Additionally, I do have important data in XP, and haven't backed up for a while, so it's pretty important to not lose that data, if at all possible.

The error I get opening the Windows folder is a permission issue; it tells me that I do not have "the permissions necessary" to view its contents.

Sounds good, and thank you for all your help thus far.

---

### Post by bulldog on 2006-11-11
When you use ALT>>F2 and ```
gksudo nautilus
``` can you open your NTFS partititon and copy your data from it?

---

### Post by turtlewars on 2006-11-11
Do you know how I might go about accessing that data in order to copy it?  There's a lot of it, and at the moment, I don't have permission to access it from Ubuntu.  Is there any way to change that, and if not, how else might I go about getting it?  I'm fine with starting from scratch, but I really, *really* don't want to lose all of that data unless I can help it.

---

### Post by bulldog on 2006-11-11
Read my previous post please,do ALT F2 and type gksudo nautilus  in the box.
This opens your file browser with root privileges.

Try to open your windows partition within this file browser and see if you can read and copy any data from it.

EDIT:
Don't you worry,if the NTFS partition is not damaged,you just have to reinstall windows.
This will erase your Ubuntu,but you can save your data from the other partition.

When you have the possibility to copy it to another drive you just can reinstall ubuntu and copy your data back.
I only want to know now if the NTFS partition is in good shape for the moment.

---

### Post by turtlewars on 2006-11-11
I can!
I feel like crying in relief.  :)

I'm a little unclear on how to go about writing the files to a CD; Ubuntu doesn't seem to be recognizing my CD drive.  Do you have any suggestions on how to go about mounting the drive?

---

### Post by turtlewars on 2006-11-11
In response to your edit, it is in good shape and all the files etc are intact.  My question now is where do I put them?  I was thinking I'd burn them to CDs, but while it seems I was wrong earlier and that my CD drive is at least mounted enough to do things like play inserted music CDs, I'm having trouble getting the data onto the disk.  How do I go about doing that?

---

### Post by bulldog on 2006-11-11
If you have a windows installation disk with the key code,you can just install windows again.

Do you have the gparted live cd?

If so boot from it and delete your ext3 [ubuntu] on sda1 no more.

You can do the same with the live cd if you haven't got the gparted live cd.

Just remove the ubuntu partition and install windows in this partition.

Just be sure to **not** reformat your data partition :D

---

### Post by bulldog on 2006-11-11
> **turtlewars said:**
> In response to your edit, it is in good shape and all the files etc are intact.  My question now is where do I put them?  I was thinking I'd burn them to CDs, but while it seems I was wrong earlier and that my CD drive is at least mounted enough to do things like play inserted music CDs, I'm having trouble getting the data onto the disk.  How do I go about doing that?

I don't think you can because only root can acces the disk.
I think you better install windows and get the data from the disk.

Then you have space to install ubuntu again and put your data back if you want to do so.

Make a partition plan on forehand how much space windows and ubuntu should get.
Don't forget your data partition it should be created again.

But your data is save and that's the important thing.

---

### Post by turtlewars on 2006-11-11
...And you're sure that reinstalling Windows won't erase the data I have on the NTFS partition?  Wouldn't it just write over it, or go somewhere else, or something?  I'm afraid I don't understand the process very well, but I'm terrified of losing all of my data.  

...Actually, looking it over, I think I get it, but let me make sure that I actually have this.  I'll remove Ubuntu, reinstall Windows XP in the space that Ubuntu occupied (the primary partition), transfer the data I have in NTFS from within the new Windows XP, and then reinstall Ubuntu in the secondary space.  Is all of that correct?  

Additionally, what do you mean by my data partition?  I thought that partitioning systems for dual-boot capacity only involved essentially splitting the hard drive into two parts and then installing two different systems with two different data sets on each side.  Is there a way to make a shared data space, and if so, how do I do that?

I'm so sorry to bog you down with questions, but I really appreciate all of your help and just really want to get this right this time around!  Thanks so much.

---

### Post by bulldog on 2006-11-11
Well you understand me well :D 
That's exactly what I meant.

About the data disk,that's for you to decide,but I presumed you wanted a separate data partition.
If not forget that part.:D 

If you just format the Ubuntu space to NTFS and leave the rest of the partitions as they where,you can safely install windows.

EDIT:
Just be sure there's nothing in your ubuntu you want to save!!

---

### Post by louieb on 2006-11-11
I see Bulldogs sugestion of gksudo nautilus works. So forget you saw the previous version of this post. That one way of getting at data I won't forget.

---

### Post by bulldog on 2006-11-11
> **louieb said:**
> Unfortunately I have to agree with catlet. 
If you followed his instructions in post #7 to the letter then there is no good reason not to be able to mount and copy off your important window data.

You could try a live CD Knoppix was mentioned earlier by bigken. My favorite is the Puppy live CD. 

If you use Puppy there is an icon on the desktop labeled Drives click on it. It will give you a list of all your partitions click the mount box next to your windows partition and if all goes well the file manager will open up and you can use it to copy your data somewhere else (USB stick recommended).
       
I hope the live CD works but I would bet against it. For the simple reason that a live CD uses the same programs as your Ubuntu installation.

Bulldogs suggestion of doing an XP install and hope you can read or repair your current NTFS partition may be your next best hope. BTW an install of XP home uses a little under 4 gig of disk space. So it looks like you have enough room.

But if the data is important enough it may be time to shell out a few hundred bucks and haul the thing down to your local data recovery service.

If you read all you shouldn't say this :D 
The data is save and the partition is undamaged.

The change windows will boot this way is zero.
He has to reinstall windows if he want's a dual boot.
By removing ubuntu and reinstalling windows in that partition,he can copy his data to the new windows partition.

Then reinstalling Ubuntu in the extendend ex. windows partition,with or without resizing, and he's up and running again.

But thanks to think with us.

---

### Post by catlett on 2006-11-11
open the file browser as root with```
 gksudo nautilus
```Browse to /media/windows. You should be able to open it now. If not post why.
Next put in a dvd. It should prompt for you to choose a data cd etc. Choose 'data cd'.
That will open up another file browser window. Drag and drop files. Make sure to hit 'write to Disk'.

If everything is fine, that will work.

---

### Post by bulldog on 2006-11-11
> **catlett said:**
> open the file browser as root with```
 gksudo nautilus
```Browse to /media/windows. You should be able to open it now. If not post why.
Next put in a dvd. It should prompt for you to choose a data cd etc. Choose 'data cd'.
That will open up another file browser window. Drag and drop files. Make sure to hit 'write to Disk'.

If everything is fine, that will work.

Maybe you should read a little back Catlett.
I did the same suggestion and we came to delete ubuntu and reinstall windows in that space.
I let you to it now.

---

### Post by catlett on 2006-11-11
> **bulldog said:**
> Maybe you should read a little back Catlett.
I did the same suggestion and we came to delete ubuntu and reinstall windows in that space.
I let you to it now.

I saw it but I thought your suggestion was ignored. I missed the 'I can' part in the next post. Just a little confusion on my part.
Reading it a little further, there was a mount error when trying to mount the cd drive. Is thsat resolved or is he just going to reinstall?

Also I think there is confusion about the XP installer savinmg data. I think you are saying, install XP to ubuntu's space and after it installs, access the old XP partition from the new XP partition and copy it over? Is that correct? That is the best option at the moment by far. I'm glad you joined the thread and brought some fresh perspective.

Turtlewar, Bulldog already mentioned it but I will say it again, make sure you copy out any important ubuntu data because it will be lost when xp formats that partition

---

### Post by turtlewars on 2006-11-12
I absolutely will, and thank you both so much for your help.  I'll let you know how it goes when I wade into the fray tomorrow.

---

### Post by bigken on 2006-11-12
dont you have another hdd set it as a master and your old 1 as a slave then install windows and get all your files and use[ this ]("http://uranus.it.swin.edu.au/%7Ejn/linux/ext2ifs.htm#Download")to get any ubuntu files in windows ;)

---

### Post by bulldog on 2006-11-12
> **bigken said:**
> dont you have another hdd set it as a master and your old 1 as a slave then install windows and get all your files and use[ this ]("http://uranus.it.swin.edu.au/%7Ejn/linux/ext2ifs.htm#Download")to get any ubuntu files in windows ;)

Yes,**if** he had another hdd,it was  a little easier to solve this problem :D ,but if he had another hdd this problem was never happened I suppose.:cool:

---

### Post by bulldog on 2006-11-12
> **catlett said:**
> 
Also I think there is confusion about the XP installer savinmg data. I think you are saying, install XP to ubuntu's space and after it installs, access the old XP partition from the new XP partition and copy it over? Is that correct? That is the best option at the moment by far. I'm glad you joined the thread and brought some fresh perspective.

Turtlewar, Bulldog already mentioned it but I will say it again, make sure you copy out any important ubuntu data because it will be lost when xp formats that partition

Yes the best option in his case is to reinstall XP and save the data,although there are other ways to do it,but you need a little experience and confidence to do so.
You had to go and I toke over to try and help him out.

We all try to help as much as we can and I learn from you guys more than you know.

---

### Post by bigken on 2006-11-12
> **bulldog said:**
> Yes,**if** he had another hdd,it was  a little easier to solve this problem :D ,but if he had another hdd this problem was never happened I suppose.:cool:


Cant he borrow 1 from a mate ?

Just trying to make it as easy as possible :D

---

### Post by Bartender on 2006-11-12
> **bigken said:**
> Cant he borrow 1 from a mate ?

Just trying to make it as easy as possible :D

Taking bigken's suggestion a step further, what about talking a friend into opening up his Windows PC and installing the poster's HDD as a slave?

---

