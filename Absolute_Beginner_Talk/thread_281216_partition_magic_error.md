---
title: "partition magic error"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by whatismouse on 2006-10-20
ive got a 114gb harddrive and im trying to downsize it by 20gb so i can make a partition for ubuntu. 

i tried using the ubuntu partioner but got so confused that i went back to partitionmagic.

when it was resizing my partition it said error 983 and that it aborted the resize. now i have no clue what that means or what i am supposed to do.

thanks.

---

### Post by Sef on 2006-10-20
Sorry to say this, but use another partitioner.  Partition Magic does not work well with GNU/Linux.

Get [GParted]("http://gparted.sourceforge.net/livecd.php") to do your partitioning.

If you have any questions on GParted or about the problems that you had using the Ubuntu partitioner, please post them.

---

### Post by whatismouse on 2006-10-20
ok i will check it out - or just go back to the ubuntu partitioner.

in the 5th section of ubuntu install it asks where it wants to be installed. i tried "resize primary partition and make room for new one using free space" but it said i did not have enough free space for the partition or something. 88 gb is filled of the 114 so i definitely have enough space for a 700 mb installation of ubuntu.

then i tried "install in largest free space section" which sat there forever with the spinning wheel not doing anything. i assume free space means hard drive space not already on a partition - of which i have none, so that would make sense that this would not work.

---

### Post by Sef on 2006-10-20
I would use GParted and delete that partition, then reinstall it with GParted, see how that works.  Note:  Like PM, GParted has a graphical interface, so easy to figure out.

---

### Post by seshomaru samma on 2006-10-20
How many partitions do you have on your Windows?
I think that you need to defragment Windows first in order to resize it. If you have several partitions on Windows (C,D,E...) you get just move all important files from it and then ask the Ubuntu partitione to format it and install Ubuntu there.
Just remeber that Linux names partitions differently , so it will appear with a different name on Ubuntu's partitioner (you will still be able to identify it by its size and order of appearance)

---

### Post by whatismouse on 2006-10-20
i have 1 114gb partition that is 88 gb filled.

all of windows and all of my files are on this 1 partition.

sef - did you mean to delete this ^ partition? wouldnt that remove everything on it?

i will try this gparted thing...

edit: how do i even open the program...i downloaded the iso and burned to a disc, put the disk in the drive and there is a gparted file of 22 mb that doesnt open with anything...

---

### Post by BigLebowski on 2006-10-20
Ok what you are doing wrong.. is resizing your partition when you have only one.


in Partition Magic, just click create a new partition and take space from your single existing partition you can use NTFS or Fat32... as the partition you will install on.

---

### Post by ReaderRat on 2006-10-20
You need to burn the ISO file as an image, not  data.
ISO - Downloading & Burning
          [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)
          [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by whatismouse on 2006-10-20
biglebowski - i tried that and got the same "error 983 - too many errors found"

readerrat - i will do that, thanks.

---

### Post by whatismouse on 2006-10-21
Readerrat - were you referring to the ubuntu cd or the gparted cd. because if i did the ubuntu cd wrong then how did it work from the live cd and all that...

---

### Post by smoker on 2006-10-21
if you burn the gparted iso as a boot disk (nero does this i know of), then change boot sequence to cd first. gparted will boot and you will be able to work on partitions without any interference from windows or ubunto.

remember as suggested clean up windows partition by getting rid of temp files, and defrag.

hope that helps

---

### Post by whatismouse on 2006-10-21
is there a difference between burning gparted as a boot disk rathe than burning it as an iso? because i have nero but have no clue what i am doing because nero = uber confusing...

thanks...

---

### Post by bigken on 2006-10-21
use [this]("http://isorecorder.alexfeinman.com/isorecorder.htm") to burn the ISO all you need to do is install the ISO burner reboot the pc and right click the iso file and select burn ;)

---

### Post by whatismouse on 2006-10-21
oh jesus, i try to install it, but it says another version is already running. i try to use the other version, but it doesnt work for some reason. i try to uninstall it but it gives me a fatal error. 

so i guess i cant use iso recorder...

---

### Post by podunk on 2006-10-21
You know - it might be a real good idea to back up any real important stuff before you get to far along. Pictures of your kids, old tax returns, stuff like that.

---

### Post by whatismouse on 2006-10-21
yep...everything important has already been backed up.

im considering just erasing the harddrive and reinstalling windows and ubuntu simultaneously. but i dont think i can handle that much computer tinkering at once, especially without being able to come on here and ask for help.

---

### Post by podunk on 2006-10-21
The first time I installed Ubuntu I defragged a couple of times, then when it got to the part about partitions I just let it do it's thing. It gave me the choice to screw around with everything or let it decide the best place to install to ("Use the largest free space" was the way it put it I think.)

I decided that since it could think at a gazillion hertz per second it just had to be smarter than I was so I let it do it's thing. :-) Worked perfect.

Don't get discoured or to frustrated. :-) Since yopu have everything backed up you got nothing to lose here. Take a break, have a cup of Ubuntu on me:

:C:

---

### Post by seshomaru samma on 2006-10-21
> **whatismouse said:**
> is there a difference between burning gparted as a boot disk rathe than burning it as an iso? because i have nero but have no clue what i am doing because nero = uber confusing...

thanks...

In Nero , look for 'burn as image' 

Reinstalling both OS is probably a good idea.
Install Windows first
Windows come with a primitive partitioner .Create 3 partitions .format all as FAT32. Install Windows on the first one and then install Ubuntu on the second . you can use the 3rd as a data partition that both OS share.
If you have any problems just use the Live CD (that you burned as image) to connect to the internet if you need to ask questions.
Once you are on the live cd you can open a terminal and run:
```
sudo apt-get install xchat
```
xchat is an application that allows to connect to Ubuntu irc channel where you can get online help. in the xchat menu choose 'freenode' and 'connect'
then join "ubuntu" channel.
it's possible that xchat is already on the live CD- cant remember . check through applications>internet

good luck

---

### Post by whatismouse on 2006-10-22
the only real reason i didnt want to reinstall both os's at the same time is because i wanted to get ubuntu working right, and then just delete windows entirely and expand the ubuntu partition. 

i dont exactly feel like an entire windows install if it means i will be replacing it with ubuntu as soon as i get it running.

[random]ps. have you ever wondered about the way your fingers type things incorrectly on the keyboard? for instance my fingers always type "yuo" and "ubunut" - frieking annoying.[/random]

---

### Post by whatismouse on 2006-10-22
i nero i did not find "burn as image" but i did find "make boot disk" however when it asks for the "image file" i assume it is asking for the gparted .iso which i cant select because it is not a .IMA .

i also tried the ubuntu partitioner again, and realized i might have mis-interpreted one of the steps. when it asks for the size of the new partition, i put 15GB of something thinking it was asking for the size of the #2 partition after resizing partition 1 down by 15gb. it said there was not enough free space. i realized that maybe it was asking for the NEW size of the primary partition, so i put it at 95gb so that there would be 15 left over with which to make the secondary partition. obviously that still cant be right because it still told me there is not enough free space.

---

### Post by gn2 on 2006-10-22
This may cast some light on your difficulties.

[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/48fac5120b7ea3b888256e75007c6a53?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no](http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/48fac5120b7ea3b888256e75007c6a53?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no)

Partition Magic is a superior tool to gparted.

The problem's with your hard drive.

Did you de-frag first?

---

### Post by bigken on 2006-10-22
> **whatismouse said:**
> the only real reason i didnt want to reinstall both os's at the same time is because i wanted to get ubuntu working right, and then just delete windows entirely and expand the ubuntu partition. 

i dont exactly feel like an entire windows install if it means i will be replacing it with ubuntu as soon as i get it running.

[random]ps. have you ever wondered about the way your fingers type things incorrectly on the keyboard? for instance my fingers always type "yuo" and "ubunut" - frieking annoying.[/random]


if thats the case just wipe your hard drive and install ubuntu as stand alone :cool:

---

### Post by whatismouse on 2006-10-22
> **gn2 said:**
> This may cast some light on your difficulties.

[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/48fac5120b7ea3b888256e75007c6a53?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no](http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/48fac5120b7ea3b888256e75007c6a53?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no)

Partition Magic is a superior tool to gparted.

The problem's with your hard drive.

Did you de-frag first?

yes i defragged it. i didnt delete temporary files though, didnt know how. 

i will check out the link though, thanks.

> **bigken said:**
> if thats the case just wipe your hard drive and install ubuntu as stand alone :cool:

extremely tempting...

---

### Post by gn2 on 2006-10-22
Very tempting to just wipe out Windows but I would urge caution.

Ubuntu's good, but not as good as it's hyped up to be. 

There's no harm in keeping Windows till you are absolutely certain you no longer need it.

If you wipe it then want it back it isn't as easy as Ubuntu to install, sort drivers, install anti-virus etc and update...

---

### Post by whatismouse on 2006-10-22
true...but i havent had a clean windows install since i bought the pc 3 years ago. and thats probably 1/2 the reason i am having so much trouble working with these partition programs..

anyways i ran the check disk and found zero problems with the harddrive. i didnt try to use partition magic since but seeing as how there was nothing wrong to correct i dont know why any different result would be found...

so im pretty much getting help on 3 different partitioners simultaneously. its a race to see which one of the 3 will work first. 

oh just wondering, on ubuntu what program is used as an AIM replacement?

---

### Post by gn2 on 2006-10-23
> **whatismouse said:**
> true...but i havent had a clean windows install since i bought the pc 3 years ago. and thats probably 1/2 the reason i am having so much trouble working with these partition programs..

anyways i ran the check disk and found zero problems with the harddrive. i didnt try to use partition magic since but seeing as how there was nothing wrong to correct i dont know why any different result would be found...

so im pretty much getting help on 3 different partitioners simultaneously. its a race to see which one of the 3 will work first. 

oh just wondering, on ubuntu what program is used as an AIM replacement?

A potential source of problem is the amount of data that's on the drive. If you create a 20Gb partition, then the reduced Windows partition will not have much free space on it. If this falls less than 25% it can cause difficulties.

Also, there's a chance Partition Magic (or whatever other tool you attempt to use) will have to move data out of the space where you want to create the Ubuntu partition.

Perhaps try moving your files to a backup drive and try again?

---

### Post by seshomaru samma on 2006-10-23
> **whatismouse said:**
>  

oh just wondering, on ubuntu what program is used as an AIM replacement?

[Gaim]("http://gaim.sourceforge.net/")

---

### Post by jwdvd on 2006-10-23
partition magic is evil,i destroyed my laptop last weekend trying to resize an ntfs drive with windows, when i rebooted grub through an error 17, it didnt like the fact that i had changed a partition at all :-(

---

### Post by gn2 on 2006-10-23
> **jwdvd said:**
> partition magic is evil,i destroyed my laptop last weekend trying to resize an ntfs drive with windows, when i rebooted grub through an error 17, it didnt like the fact that i had changed a partition at all :-(

Dual booting on one drive is not without it's problems.

I simply would NEVER try it again.

Don't be too quick to condemn Partition Magic when your problem is with Grub and Ubuntu?

Did you change the start point of the Ubuntu partition?

If so, Grub would have to be re-configured.

Other Distros allow Grub to be installed on the Linux partition, and have the Windows loader point to it.

An altogether friendlier solution.

A standard Ubuntu dual-boot install does not offer this option, instead it infects your MBR with a particularly nasty virus-like utility called Grub.

Avoid.

---

### Post by jwdvd on 2006-10-23
I wasnt dual booting on 1 drive, its a laptop with 3 partition...

10Gb XP
20Gb blank
10Gb ubuntu

I used partition magic to take space from the blank drive to the XP partition, and it killed grub :-(

---

### Post by gn2 on 2006-10-23
> **jwdvd said:**
> I wasnt dual booting on 1 drive, its a laptop with 3 partition...

10Gb XP
20Gb blank
10Gb ubuntu

I used partition magic to take space from the blank drive to the XP partition, and it killed grub :-(

Three partitions on on one hard drive.

Unless you've got a twin hard drive laptop?

The Ubuntu implementation of Grub's still the problem.

---

