---
title: "how i run gparted"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-08-16
I have a dual boot, windows XP and Ubuntu 7.04. I also still have Ubuntu 6.10 (which i want to remove)

I have ubuntu 7.04 which is 56.8GB on my hard drive
windows which is 9.6GB
and ubuntu 6.10 which is 9.8GB on my hard drive.

I want to run Gparted. First i got the live CD file, downloaded and burned onto a CD. I had the CD in the tray, turned off the computer, turned back on. It never loaded, instead GRUB loaded. I ran ubuntu from there, downloaded the normal Gparted. Now i have it and it WILL NOT RUN because I am not root... I tried some sudo apt commands but I'm no good with the terminal, so someone please help me run Gparted.

Once Gparted is working i will need to:

- erase ubuntu 6.10 partition
- resize windows partition to about 100GB

EXTRA INFO:
my Hard drive is a 160GB 7200RPM Seagate IDE (MASTER) Hard Drive.
I have close to no experience with Linux

---

### Post by overdrank on 2007-08-16
HI you don't have the live cd you installed feisty with? If not and the cd you downloaded and burned is not working, did you change the boot order so the cd drive doesn't boot before the hardrive?

---

### Post by {A}Poly on 2007-08-16
> **overdrank said:**
> HI you don't have the live cd you installed feisty with? If not and the cd you downloaded and burned is not working, did you change the boot order so the cd drive doesn't boot before the hardrive?

1) Yes I have the CD i installed Feisty with, why?
2) It burned correctly, it has not been touched, no scratches or anything. should be working fine.
3) I never touched the boot order.

---

### Post by amazingtaters on 2007-08-16
You can run GParted via the live CD. That's what I did to change and resize partitions recently. So try booting to that.

---

### Post by overdrank on 2007-08-16
> **{A}Poly said:**
> 1) Yes I have the CD i installed Feisty with, why?
2) It burned correctly, it has not been touched, no scratches or anything. should be working fine.
3) I never touched the boot order.

Ok the live cd with feisty has gparted on it that is why I asked. You can use it to repartition your space. Just make sure your partitions are not mounted and the you are on your way.

---

### Post by dannyboy79 on 2007-08-16
you will always want to start "GUI" apps that require admin priveleges with this command in front of the GUI command
gksudo
this will give you root priveleges for that program. You can use just sudo for any command that does run inside a gui. so the command altogether will be
gksudo gparted
make sure that the partition with Edgy on it is NOT mounted. You can find out which one it is by issuing
sudo fdisk -l
then just look for the identifier being something like /dev/hda3 or /dev/sda2. The "s" is for usb drives and serial-ata drives. the "h" is for parallel-ata hard drives. I am not sure what the "d" stands for but the next letter is what drive it is. "a" would be the first primary hard drive, b would be the next and so on. Then is the number which is the partition on that disk, "1" is the first partition.
Here's what my sudo fdisk -l returns:
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  Linux
/dev/hdc2              14        1281    10185210   83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

You can see this is a 20gb hard drive, it's an ide-pata drive, it has 4 partitions. It's the 3rd drive in this computer. You'll want to ensure you don't delete the wrong drive, so to ensure you know which partition is what, you'll see that your windows drive has a "NTFS" within it's System column. So make sure you don't delete that one. You can also ensure a partition is NOT mounted by entering the command mount at the command line.
here's what my "mount" command shows:
/dev/hdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
tmpfs on /dev/shm type tmpfs (ro)
/dev/hdc1 on /boot type ext3 (rw)
/dev/hdc4 on /home type ext3 (rw)

good luck

---

### Post by bodhi.zazen on 2007-08-16
Set you bios to boot from CD first

Boot a live cd. I advise the gparted CD as it is more powerful and the unless you run the gutsy CD you may have problems ...

open a terminal, enter this command :

```
gksu gparted
```

partition away ....

---

### Post by stevebakerj on 2007-08-16
> **{A}Poly said:**
> I have a dual boot, windows XP and Ubuntu 7.04. I also still have Ubuntu 6.10 (which i want to remove)

I have ubuntu 7.04 which is 56.8GB on my hard drive
windows which is 9.6GB
and ubuntu 6.10 which is 9.8GB on my hard drive.

I want to run Gparted. First i got the live CD file, downloaded and burned onto a CD. I had the CD in the tray, turned off the computer, turned back on. It never loaded, instead GRUB loaded. I ran ubuntu from there, downloaded the normal Gparted. Now i have it and it WILL NOT RUN because I am not root... I tried some sudo apt commands but I'm no good with the terminal, so someone please help me run Gparted.

Once Gparted is working i will need to:

- erase ubuntu 6.10 partition
- resize windows partition to about 100GB

EXTRA INFO:
my Hard drive is a 160GB 7200RPM Seagate IDE (MASTER) Hard Drive.
I have close to no experience with Linux

As always backup any important info before using gparted

I would install/reinstall gparted, in the terminal type

```
sudo apt-get install gparted
```

you will be prompted for your password

you will then see the d/l and will be prompted to continue Y/N hit Y enter

then in the terminal type

```
sudo gparted
```

and the gparted GUI will load, it will be scanning your drive/drives so give it a few secs. Then go from there but remember you are using the 'hand of god'

---

### Post by dannyboy79 on 2007-08-16
FYI, I used the Gparted LiveCD to make a NTFS partition BUT windows did NOT want to boot from it. I would use Windows tools to resize your windows partition after you delete the Edgy partition.

---

### Post by dannyboy79 on 2007-08-16
> **stevebakerj said:**
> As always backup any important info before using gparted

I would install/reinstall gparted, in the terminal type

```
sudo apt-get install gparted
```

you will be prompted for your password

you will then see the d/l and will be prompted to continue Y/N hit Y enter

then in the terminal type

```
sudo gparted
```

and the gparted GUI will load, it will be scanning your drive/drives so give it a few secs. Then go from there but remember you are using the 'hand of god'
I strongly suggest NOT using sudo with graphical apps. Most of the time it will be ok BUT on the other hand there are plenty of occasions that will have unfavorable results. Anything from  Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed.  see here: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by {A}Poly on 2007-08-16
OK

Gparted is running well, Now i need to delete ubuntu 6.10. I just deleted something, and now theres tuns more of stuff! I don't know what's what! I know windows is the NTFS (duh). but theres lots more. Which ones do i delete?

[B]
CLICK BELOW FOR SCREEN SHOT ( FULL SIZE )[/B]
[http://img524.imageshack.us/img524/2506/gparted0012fa1.png]("http://img524.imageshack.us/img524/2506/gparted0012fa1.png")

[IMG]http://img405.imageshack.us/img405/2222/gparted0012ln1.png[/IMG]

So I don't delete the first one - NTFS which is windows.
The second is Ubuntu 7.04 - ? right ? so i don't delete that partition.
The third and after that are all 6.10???? right ?  ? ? so i delete all those?


little confused with all the partitons... there's only supposed to be 3 or so....

---

### Post by dannyboy79 on 2007-08-16
no, your second one is only a storage location, well at least it's mounted within /media/. I would say that your feisty install is /dev/hda6 and the swap for that install is /dev/hda7. You will only want to delete /dev/hda5. Plus I don't see how you'll actually be able to do this. You won't be able to grow your windows partiiton if the space is at the end of the drive within an extended partition. NOt to mention, how can you erasing an approx 10 gb edgy partition and somehow make your windows drive 100gb?? It's impossible as the math doesn't add up unless you also want to delete /dev/hda3 which appears to be just a storage location BUT you do ahve 4gb of something on it. Plus it's locked. you have to unmount anything that want to change. From what it sounds like you want to do you'll be able to get the /dev/hda3 deleted and then joined to windows but not the 10gb of space that's at the end. You could always use partimage or g4u or g4l to backup each of your partitions so you can create a brand new partition table with the sizes that you want, then just extract the image back onto each of the parittions. Good luck

---

### Post by {A}Poly on 2007-08-16
> **dannyboy79 said:**
> no, your second one is only a storage location, well at least it's mounted within /media/. I would say that your feisty install is /dev/hda6 and the swap for that install is /dev/hda7. You will only want to delete /dev/hda5. Plus I don't see how you'll actually be able to do this. You won't be able to grow your windows partiiton if the space is at the end of the drive within an extended partition. NOt to mention, how can you erasing an approx 10 gb edgy partition and somehow make your windows drive 100gb?? It's impossible as the math doesn't add up unless you also want to delete /dev/hda3 which appears to be just a storage location BUT you do ahve 4gb of something on it. Plus it's locked. you have to unmount anything that want to change. From what it sounds like you want to do you'll be able to get the /dev/hda3 deleted and then joined to windows but not the 10gb of space that's at the end. You could always use partimage or g4u or g4l to backup each of your partitions so you can create a brand new partition table with the sizes that you want, then just extract the image back onto each of the parittions. Good luck

I tried deleting hda5 (which is ubuntu 6.10). No luck, it asked to unmount. I did and still it didn' work. 

What i meant by 100GB for windows is this :

i have 160 GB (I should)

about 60 GB for Ubuntu 7.04
and
100GB for Windows XP
or something around that.... right now i only have less than 10GB for windows! I can't install a *&&^ thing!!!! 

All i want to do is split my hard drive in two : windows and ubuntu. NOT have all these usless partitions sitting around taking up most of my hard drive, and then NOT BEING ABLE TO REMOVE THEM.  Just please, tell me how to simply do this. All i want , i repeat is half my hard drive windows and half ubuntu! not 9GB windows and the rest ubuntu!

---

### Post by dannyboy79 on 2007-08-16
> **{A}Poly said:**
> I tried deleting hda5 (which is ubuntu 6.10). No luck, it asked to unmount. I did and still it didn' work. 

What i meant by 100GB for windows is this :

i have 160 GB (I should)

about 60 GB for Ubuntu 7.04
and
100GB for Windows XP
or something around that.... right now i only have less than 10GB for windows! I can't install a *&&^ thing!!!! 

All i want to do is split my hard drive in two : windows and ubuntu. NOT have all these usless partitions sitting around taking up most of my hard drive, and then NOT BEING ABLE TO REMOVE THEM.  Just please, tell me how to simply do this. All i want , i repeat is half my hard drive windows and half ubuntu! not 9GB windows and the rest ubuntu!
ok first of all, you don't need to get upset and start yelling (using capital letters). I am here trying to help you. These so called "useless partition" are there because you decided to do this this way originally instead of just using feisty to overwrite edgy so we have to deal with this. So, take a deep breath and we'll get you through this.
You'll need to figure out what's on your /dev/hda3 partition. it says there's 4 gb of data so whatever is there move it over to /dev/hda6 within your /home/username folder. if you don't think it's anything useful than go ahead and delete the partition without seeing what it was.

 I have already told you where feisty is at, looking at the mount point of   /    it's on /dev/hda6. the only 3 partitions that you'll need for sure are /dev/hda1 (windows), /dev/hda4 (this is an extended partition), /dev/hda6 (root for feisty) and /dev/hda7 (feisty swap space). hda5 was swap for edgy I am guessing, you'll need to use swapoff -a, this will parse /etc/fstab and unmount all swap partitions. although according to the picture it isn't locked so I am not sure why you couldn't remove it before. BUT don't remove /dev/hda7 as that's swap for feisty. Once you remove the partitions, like I said, I would strongly suggest "growing" windows larger by using a windows tool like partition magic or something similar. I don't think windows disk management can even grow partitions. you won't be able to add the 11gb that's within the extended partition to /dev/hda1 because they aren't next to each other. we can talk about what to do with that 11gb later. let me know how it goes. good luck

---

### Post by {A}Poly on 2007-08-16
> **dannyboy79 said:**
> ok first of all, you don't need to get upset and start yelling (using capital letters). I am here trying to help you. These so called "useless partition" are there because you decided to do this this way originally instead of just using feisty to overwrite edgy so we have to deal with this. So, take a deep breath and we'll get you through this.
You'll need to figure out what's on your /dev/hda3 partition. it says there's 4 gb of data so whatever is there move it over to /dev/hda6 within your /home/username folder. if you don't think it's anything useful than go ahead and delete the partition without seeing what it was.

 I have already told you where feisty is at, looking at the mount point of   /    it's on /dev/hda6. the only 3 partitions that you'll need for sure are /dev/hda1 (windows), /dev/hda4 (this is an extended partition), /dev/hda6 (root for feisty) and /dev/hda7 (feisty swap space). hda5 was swap for edgy I am guessing, you'll need to use swapoff -a, this will parse /etc/fstab and unmount all swap partitions. although according to the picture it isn't locked so I am not sure why you couldn't remove it before. BUT don't remove /dev/hda7 as that's swap for feisty. Once you remove the partitions, like I said, I would strongly suggest "growing" windows larger by using a windows tool like partition magic or something similar. I don't think windows disk management can even grow partitions. you won't be able to add the 11gb that's within the extended partition to /dev/hda1 because they aren't next to each other. we can talk about what to do with that 11gb later. let me know how it goes. good luck


I can't delete or move any partitions. I can't resize or anything. The only one i can, says i have to unmount?

---

### Post by dannyboy79 on 2007-08-16
if you read my posts, you'll see that I have told you that you need to ensure that the partitions are NOT mounted by using the mout command. If they aren't mounted and you're still having this problem than I believe this is bug that I thought I read about. Gparted is mounting the partiitons for some reason. If you're using gparted from within feisty, then go into System, Prefs, Removable Media and uncheck the box that tells it to mount removable media. That may help , if it doesn't and it still telling you haev to unmount and despite your efforts it WAS unmounted before you started gparted than I would suggest booting to the gparted livecd, make sure your bios is booting first to  a cd and not your hard drive OR you can always try to hit F8 which may bring up a boot menu, then chose it to boot to the cd. also, you would have had to create the cd using the create from image burning option so that it didn't just burn the iso file as a file, it actually needed to extract the iso's contents on to the cd otherwise it won't work. As another has already suggested, make a backup of everything important before doing this just in case.

---

### Post by {A}Poly on 2007-08-16
> **dannyboy79 said:**
> if you read my posts, you'll see that I have told you that you need to ensure that the partitions are NOT mounted by using the mout command. If they aren't mounted and you're still having this problem than I believe this is bug that I thought I read about. Gparted is mounting the partiitons for some reason. If you're using gparted from within feisty, then go into System, Prefs, Removable Media and uncheck the box that tells it to mount removable media. That may help , if it doesn't and it still telling you haev to unmount and despite your efforts it WAS unmounted before you started gparted than I would suggest booting to the gparted livecd, make sure your bios is booting first to  a cd and not your hard drive OR you can always try to hit F8 which may bring up a boot menu, then chose it to boot to the cd. also, you would have had to create the cd using the create from image burning option so that it didn't just burn the iso file as a file, it actually needed to extract the iso's contents on to the cd otherwise it won't work. As another has already suggested, make a backup of everything important before doing this just in case.

sorry

what's the command?

---

### Post by dannyboy79 on 2007-08-16
this is the number one most frustrating thing about helping people. I spend my time to post a long explanatory help thread and then it doesn't even get read by the person asking for help because they just want a quick fix and don't want to spend the time to read thoroughly. Please read post #6 and you'll have your answer. Please try all the things I have posted more than once and if you still are having problems let us know. You need to try to help youself a little  and by not reading carefully you make it hard for people to want to continue to try and  help you.

---

### Post by {A}Poly on 2007-08-16
> **dannyboy79 said:**
> this is the number one most frustrating thing about helping people. I spend my time to post a long explanatory help thread and then it doesn't even get read by the person asking for help because they just want a quick fix and don't want to spend the time to read thoroughly. Please read post #6 and you'll have your answer. Please try all the things I have posted more than once and if you still are having problems let us know. You need to try to help youself a little  and by not reading carefully you make it hard for people to want to continue to try and  help you.

yes I read that 2 times, It shows how to **see **what is mounted. But not **how to un mount.** That's what I need help with. Thanks anyways though.

---

### Post by dannyboy79 on 2007-08-16
ok, you didn't say that. The command is 
sudo umount /dev/hda5
that's just an example, use whichever partition you want to unmount. you'll only be able to unmount a partition that isnt being used. you won't be able to unmount swap, first you have to swapoff -a, that should turn off swap space but then you still may have to unmount it but I am not sure as I have never used swapoff -a, or needed to unmount my swap space.

---

### Post by {A}Poly on 2007-08-16
thanks a lot. I have been able to get a lot of space. This is what it now looks like:
(I have deleted hda3 and some other stuff. only thing left that's not ubuntu fiesty or windows is hda5 which i can't manage to unmount. even with the command It didn't work, the same error occurs. But meh, if I end up not being able to remove hda5. No biggy it's only 1.26 GB which is not much.) 

[http://img374.imageshack.us/img374/7460/gparted002kd2.png]("http://img374.imageshack.us/img374/7460/gparted002kd2.png")
**CLICK THE LINK TO SEE**


So i guess I need to resize the NTFS on windows eh? I forgot but... i googled it and found [http://support.microsoft.com/kb/255867/]("http://support.microsoft.com/kb/255867/")
that. So I'll just use that.

thanks

---

### Post by StephUb on 2007-08-16
Hi,

If i remember well fdisk, it's running under DOS, and is formating the disk at the same time... which mean you are gonna loose all window when you try to resize the window partition.
Second, i think to remember that fdisk can't manage large disk but i am not that sure about that.

I would use GParted to resize the windows partition.
If I understand well, you running G parted from festy so without mounting the windows partition, you should have to partition locked because used : Ext3/feisty and the feisty swap.

First unmount this damn window partition and resize it with Gparted...
If you want to , remove the swap which is unlock...

For resizing the feisty partition, boot on the Gparted CD and resize it...

---

### Post by dannyboy79 on 2007-08-16
i have had bad experience using gparted livecd to create a ntfs partition but i can't speak for actually resizing one. Come to think about it, it may have been partimage that has ntfs writing still in a beta state, so maybe the partition that was created by gparted was fine, it was just the partimage writing the image back onto the ntfs filesystem. None the less I would back up your data no matter what just in case. Also, to the best of my knowledge fdisk doesn't create partitions over 32gb in size and I am not aware of it's resizing capabilities.
Even though /dev/hda5 shows not locked, I am guessing that yoiu have to use swapoff -a to get it to release the swap space before you can delete /dev/hda5. good luck

Also, before you go any further, you may want to boot up windows and ensure that everythign is still ok. Sometimes changes to partition tables like this can cause windows  to act weird.

---

### Post by StephUb on 2007-08-17
Fdisk does NOT resize, it will delete the partition and create a new one, so you lost the content of this partition.

Go with Gparted (GUI) or with a $ one like partition magic..

---

### Post by bodhi.zazen on 2007-08-17
> **StephUb said:**
> Fdisk does NOT resize, it will delete the partition and create a new one, so you lost the content of this partition.

Go with Gparted (GUI) or with a $ one like partition magic..

Well fdisk does not format the partition so if you restore the partition table (without reformatting) you will not have data loss :)

saved my @#$ more then once ;)

---

### Post by ntu on 2007-11-06
> **dannyboy79 said:**
> You can also ensure a partition is NOT mounted by entering the command mount at the command line.
here's what my "mount" command shows:
/dev/hdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
tmpfs on /dev/shm type tmpfs (ro)
/dev/hdc1 on /boot type ext3 (rw)
/dev/hdc4 on /home type ext3 (rw)


Does this line:

/dev/hdc2 on / type ext3 (rw,errors=remount-ro)

mean that /dev/hdc2 is mounted or unmounted? If mounted how does one unmount it?

With best wishes to everyone,

---

