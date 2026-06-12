---
title: "Help with Partimage with 2 HDD"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-14
[IMG]http://i13.tinypic.com/6fj0duv.jpg[/IMG]

**The Psychocats tutorial is available here:**

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I get to step 5 but then where does the program know where to transfer this image file to as their is no mention of a destination drive.

---

### Post by bodhi.zazen on 2007-09-14
From gparted select hda1

Edit -> copy

Go to the box in upper right, select hdb from pull down menu

Edit -> Paste

======

To answer your question, you would install patimage

The with partimage (not gparted) :


Close gparted, open a terminal and type ```
sudo partimage
```

continue with psychocats tutorial ...

---

### Post by chrome307 on 2007-09-14
Just to clarify

Is it as simple as copying over hda1 to hdb1

nothing else ??  Seems too simple, but I'd love Ubuntu more if it was :)

Would that mean that I could simply swap over drives and it would boot up as normal (minus my personal files) ?

==================

With regards to PartImage, I'm using the System Rescue Cd available from the PartImage site.

It contains PartImage, Gparted etc ...... as I'm using this as a LiveCD, I just type in 

partimage

to load the application, and then attempt to work my way through the steps.

The initial steps are straightforward, but I'm confused when I'm about to create the image, it does not specify a location, so I stopped it there as I was worried it would simply create an image file onto hda1 and not hdb1.

Hope that makes sense?

---

### Post by bodhi.zazen on 2007-09-14
> **chrome307 said:**
> Just to clarify

Is it as simple as copying over hda1 to hdb1

nothing else ??  Seems too simple, but I'd love Ubuntu more if it was :)

Would that mean that I could simply swap over drives and it would boot up as normal (minus my personal files) ?

If all you want to do is copy the partition, it is that simple.

==================

> With regards to PartImage, I'm using the System Rescue Cd available from the PartImage site.

It contains PartImage, Gparted etc ...... as I'm using this as a LiveCD, I just type in 

partimage

to load the application, and then attempt to work my way through the steps.

The initial steps are straightforward, but I'm confused when I'm about to create the image, it does not specify a location, so I stopped it there as I was worried it would simply create an image file onto hda1 and not hdb1.

Hope that makes sense?

I am not sure with that live CD, you need to run partimage as root, so either sudo or su if needed. If you are already root, well you are good to go with "partimage" then.

Not sure exactly where you are getting hung up exactly, it has been a while ...

[img]http://img263.imageshack.us/img263/9397/partimage12gk1cg6.th.png[/img]

> Once you launch PartImage, use the Up and Down arrows to select which partition to back up.

[color=green]Type the name of the path and file where you're going to back up the partition. Since I mounted the backup partition at /backup, I have to type /backup/hda1partition and not just hda1partition. You can use whatever name you want, though. I could have called it /backup/gobbledygook[/color]

Action to be done should be Save partition into a new image file.

Then tab to <Next (F5)> and press Enter to move to the next screen.

Is this where you are stuck ?  What part are you having problems with ?

---

### Post by chrome307 on 2007-09-14
That's right at that point.

All that I see is an OK tab - what I'm might confused at is where is this image being added to?

/backup/hda1partition  (source)
...........................      (destination ??)

there does not seem to be a place to specify where the image will be created to or added to ........... or do I simply choose OK and it will then give me a location to add it to?

Sorry about asking so many questions, but it's my 1st time using the software and finally I'm happy with my installed OS, I just want to back it up, in case I do something stupid in the future.

[EDIT]

BTW The 2nd drive is only 9.53GB in size not a full 10GB .......... will this cause a problem ? Or will it simply cover over the 2.88GB only?

---

### Post by bodhi.zazen on 2007-09-14
>  ...backup actual used space and compress the backup image to your choice of compression. Example, my "/" partition (hda1) is 10GB but my install only uses 3GB. Partimage only backs up the 3GB actually used and compressed my image to around 1GB. That's cool.

Well, you need to mount hdb1 somewhere, no ?

sudo mkdir /media/backup #or /mnt/backup
sudo mount /dev/hdb1 /media/backup

There is a box in the middle of the screen "Image File to Create/use"

you have to manually type in the backup file name (with path)

so type "/media/backup/home" without quotes and your home directory will be saved on the hard drive in a directory named "home" without quotes.

Use what ever mount point and back up name you like.

---

### Post by chrome307 on 2007-09-14
[IMG]http://i1.tinypic.com/61kenm9.jpg[/IMG]

[IMG]http://i4.tinypic.com/4pxoakg.jpg[/IMG]

So now I've used these commands:

[B]sudo mkdir /backup
sudo mount /dev/hdb1 /backup[/B]

So I will now boot up with PartImage and when it tells me where to backup from I type in:

**/backup/hda1partition**

and then go through the other steps ending with **f5** to finish

this as you have told me will transfer the contents onto the hdb1 with the folder /backup

........ I'll have to grab the screenshots after I've carried out the next steps

---

### Post by bodhi.zazen on 2007-09-14
\o/

Except it creates a compressed image, possibly broken into 2 Gb pieces, not a direct copy.

You can restore from the image if you wish (you should of course try this to make sure it works)

You can burn the 2 Gb files to DVD if you wish ...

---

### Post by chrome307 on 2007-09-14
I just tried it out ......... went through the steps (not shown on the Psychocats tutorial) and it told me it was backing up hda1 @ 10GB and it showed me a dialog box for the transfer of speed etc ...

10secs in and it told me that the disk was full and that it could not continue ...... 

This I am guessing is because I choose 'None' for compression, as my understanding was that it was only going to copy over the 2.8GB and therefore did not need a full 10GB on the SLAVE.

---

### Post by bodhi.zazen on 2007-09-14
I would guess so as well. I have never received an error message with partimage. I usually stay with the default options.

---

### Post by chrome307 on 2007-09-14
No joy again  ( outlined the steps I took below)

Checked the size of both drives ........ not changed from above  .... checked the 'backup' folder just in case the image was contained within

[IMG]http://i15.tinypic.com/52us9ah.jpg[/IMG]

Steps taken:

Downloaded the SystemRestoreCD and burned it:
[B]
Bootable CD-Rom image with Partition Image 0.6.6 (stable):[/B]

[http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964](http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964)

Reboot PC

Press Enter to start once the CD gets to the command line

Choose keyboard layout number

Type in '**partimage**' to load the program

In the 1st dialog box entered:  ( you can use the TAB and Spacebar to highlight your selections if needed )

**/backup/hda1partition** (then F5 to continue)

Left the default settings for all including compression GZip ( F5 to continue )

Typed in description for backup ( OK to continue )

Then presented with a dialog box with information ( OK to continue )

Shown another dialog box informing me that it will take 5 mins to complete

After 2 mins presented with a new dialog box ' **Disk Full** ' choose a new directory to continue

 ....... then I quit by choosing CANCEL and typed 'exit'

[IMG]http://i5.tinypic.com/548plqe.jpg[/IMG]

---

### Post by bodhi.zazen on 2007-09-14
Ah, well from that last screen shot, your second HD is mounted at /media/disk

So I presume /backup is directing to RAM ???

Try a path of : /media/disk/hda1partition

---

### Post by chrome307 on 2007-09-14
That's what I thought myself, but reading the blurb on PartImage it only needs 384MB to run and I have 512MB installed.

I did as you suggested but received this error message in the final dialog box

[CENTER][B]Cannot create temp

[/media/disk/pi67ca3ca3.tmp]

Please, check there is space enough and you have access rights[/B][/CENTER]

then I only had the option to cancel.

==================================

Just to let you know that I used GParted (LiveCD) to format the slave drive, and appreciate you never get the full amount from any HDD, but I did not create the Media folder and it shows up in my browser as 'Lost & Found '

If I haven't said it earlier - 'Thanks' for your input ......... I can't work out what I'm doing wrong or if the application is at fault ie buggy  (did download the stable version)

Oh well .........

---

### Post by bodhi.zazen on 2007-09-14
Make sure you are running as root !

"lost and found" is a system file , used by ext3 as a part of the Journaling. In addition some of the disk space is reserved for root in the event the disk is full. You can modify this second property and recover significant amounts of disk space.

```
	sudo tune2fs -r 0 /dev/xxxx
```
	
sets the number of reserved blocks in the filesystem to 0.

Reserved blocks are available only to specific users (normally root), so that the system can continue to function if the filesystem gets filled up. You only really need this on your / partition.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by chrome307 on 2007-09-15
OK, that would help with the filing >300mb ........ but it doesn't explain why I'm not able to  use PartImage and create a clone of my HDD.

Also I had expected to see the directory 

**/backup**

on the SLAVE drive but that's not there either.

**[EDIT] **

I entered the command via the LiveCD and repeated the steps undertaken as before ........ same result ... ' Disk Full ' :confused:

---

### Post by chrome307 on 2007-09-15
So do I take it the Psychocats tutorial is wrong ??

---

### Post by bodhi.zazen on 2007-09-15
No, I am not sure of the problem. I have used partimage following the psychocats tutorital without any problem.

Note : That tutorial is also using partrimage on a live Ubuntu CD, not that I would know what difference that would make.

---

### Post by chrome307 on 2007-09-15
Yes the tutorial uses a Ubuntu LiveCD, but I didn't think it would make any difference if I used a stable copy of the program and run it by itself.  The program is still the same and the commands.

I will make one last attempt at this using the Ubuntu CD and see how it goes.

---

### Post by chrome307 on 2007-09-15
[IMG]http://i2.tinypic.com/67rwuht.jpg[/IMG]

---

### Post by bodhi.zazen on 2007-09-15
Awesome, who would have guessed ?

You can test the backup, if you wish, as follows (I test backups for mission critical things and advise you the same. The time you need to restore is NOT the time to discover you back up failed.)

I looked back at this thread, specifically at your first post.

It seems you have some space on the HD

If you would like to test your backup, resize hda2 (with gparted) making a new 10 Gb partition.

Restore and test to that new partition.

If it works, you can then resize again (with gparted), deleting this test partition, and restoring hda2 to it's original size.

After you restore your backup to the test partition you will need to edit /boot/grub/menu.lst and /etc/fstab to reflect the proper root partitons. You can do this from a live CD after restoring (mount and edit the restored partition). You then boot from the grub command line ...

See here for some hints if needed : [http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

### Post by chrome307 on 2007-09-17
I have attempted to backup directly from my Slave hdb1 to Master hba1 , and am unable to do so.

The program tells me that it cannot find a directory/path fro the image (named hda1partition)

I have tried

/dev/hdb1

/dev/hdb1/backup/

/dev/hdb1/backup/hda1partition

Needless to say I am none the wiser :confused:

---

### Post by bodhi.zazen on 2007-09-17
Mount and serch the hdb partition. I think you are looking for a file "hda1partition.0" or something like that .

---

### Post by chrome307 on 2007-09-17
OK let me get this right

I boot up with LiveCD - enable the UNIVERSE repostitories - update and download/install PartImage

I then need to mount drive hda1 or hdb1 ?

The reason I am asking is that the Psychocats tutorials tells me to mount the drive I wish to work with ie hda1

I then run PartImage via Terminal and then go through the steps to restore the backup image

(I have selected both hda1 and hdb1 to work with at different times with no success)

So I'm stuck at which partition to mount (also not sure what commands to use to do this) because if I mount the slave drive how will it know that I am transferring the image to the primary partition.

I have read the PartImage tutorial for restoring image files but this only explains the options not a 'walkthrough'

[http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file](http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file)

I appreciate the fact what I need is a having my hand held during this process ..... but how else am I supposed to learn.

Ubuntu and Linux are great pieces of software but I feel that for most users (including myself) that it can be daunting and no understanding or being able to work things out in a logical fashion (to ourselves) is a bit of turn off.  It maybe that I'm not suited for Linux but I willing to give it a try.

---

### Post by logos34 on 2007-09-17
If your backup image is stored on hdb1 in 'backup' folder, and you are using partimage to restore it to hda1, then you want to mount the former (to 'read' the image you have to mount the partition to access it) but not the destination/partition being restored.  Just click on hdb1 in nautilus browser and it should automount at 'media/disk'.  Then start partimage and select /dev/hda1, the partition to which you are restoring the image.  Type in the path to the image on hdb1, '/media/disk/backup/hda1partition...' and select restore.

---

### Post by bodhi.zazen on 2007-09-17
Thanks for the assistance logos34 ;)

chrome307 :lolflag: That is why I suggested you test the process. The time to figure this stuff out is NOT when you need itto restore mission critical data !

---

### Post by chrome307 on 2007-09-18
Still trying to do this .... but it's a lot harder as I have to move this PC to get a 'wired' net connection

No luck at present .... 

[IMG]http://i15.tinypic.com/61jc479.jpg[/IMG]

[IMG]http://i17.tinypic.com/689gzn9.jpg[/IMG]

[IMG]http://i7.tinypic.com/5xo3o93.jpg[/IMG]

---

### Post by chrome307 on 2007-09-19
Can anyone help me with this ?

I've nearly reached the finishing line ........... but yet so far away :confused:

---

### Post by logos34 on 2007-09-19
looks like you need to change ownership and/or permissions on those images--they're owned by root.

like this

sudo chown <yourusername> /path/to/file

Ex.:
[B]
sudo chown chrome301 /media/disk-2/hda1partition.000[/B]

make sure to get the path to file right in partimage--you put in '/media/disk/...' when it was actually mounted at /media/disk-2 (the livecd names partitions according to sequence of mount--i.e. 'disk', 'disk-1',  'disk-2', etc,)

---

### Post by bodhi.zazen on 2007-09-19
partimage should be run as root ...

---

### Post by chrome307 on 2007-09-21
[IMG]http://i3.tinypic.com/660zfow.jpg[/IMG]

[IMG]http://i15.tinypic.com/62n4p69.jpg[/IMG]

**@ bodhi.zazen**

I am running PartImage as root ie

*sudo partimage*

**@ logos34**


[I]' looks like you need to change ownership and/or permissions on those images--they're owned by root.

like this

sudo chown <yourusername> /path/to/file '[/I]

My user name when the drives are mounted is 'user' and I have entered the command in as suggested via terminal which simply leads me back to the prompt

So does this apply also when using the LiveCD ?  The reason why I ask is that when entered it tells me that this user does not exist.

As you can see from above the only disk mounted is the SLAVE as 'disk1'

It's apparent to me that the information at Pyschocats is not detailed enough for me as a walkthrough as it assumes I know these additional commands, also the PartImage website does not even go into this depth for restoring images.  In both instances it assumes the reader has this knowledge already and the lack of documentation does not inspire confidence in me using this application in working with my data. 

At this point, if I was required by necessity to go through the backup/restore image process, I would resign myself to having to do a complete  'Reinstall' of the Operating System.  

As data is so important to us, it's a shame to see that Ubuntu has not prioritised this feature and included it as a built in application similar to Windows 'System Restore'.

---

### Post by bodhi.zazen on 2007-09-21
You might want to look at this : 

[http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php](http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php)

---

### Post by chrome307 on 2007-09-23
It's an interesting article and hope that the software progresses from Alpha stage.

If I can't use the HDD for backups, I guess I could always reformat it and store some MP3's on it to listen to instead.

---

### Post by Drakkor on 2007-10-14
I can't seem to input anything in the * Image file to create/use box, I keep clicking on it,
and can't seem to type anything in there !!

---

### Post by antmenj on 2007-11-06
Just a quick post so I can find this thread again.  No use using bookmarks from the live cd.:)

---

### Post by bodhi.zazen on 2007-11-06
> **Drakkor said:**
> I can't seem to input anything in the * Image file to create/use box, I keep clicking on it,
and can't seem to type anything in there !!

Use the tab key

---

