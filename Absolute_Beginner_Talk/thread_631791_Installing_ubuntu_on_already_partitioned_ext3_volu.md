---
title: "Installing ubuntu on already partitioned ext3 volume"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by adam212 on 2007-12-04
So i read the threads but it seems the Ubuntu setup is detecting their 2 separate ext3 partitions but in my case all the setup detects is the whole disk drive which is 250gb but my drive is split into 

c: windows os
d:downloads and other stuff
j:Recovery drive
f:empty ext3 partition (25gb)

so do i need two ext3 partition, one for root and the other for swap to make the setup detect the ext3 partitions or what. Why wont the setup detect the existing ext3 partitions. Hell it detects ntfs but not ext3, wtf. 

So i guess my quesiton is.

How do i install Ubuntu in already partitioned ext3 volume which i created and formatted using acronis disk director.

Btw the mouse doesn't work after the live cd boots up(only god knows why). Any idea how to fix it. I can manage without a mouse using keyboard but my main concern is installing the damn os.

Thanks.

---

### Post by gazj on 2007-12-04
firstly i would just leave the 25gig as empty space and let ubuntu create the partitions it needs

secondly it won't need two ext3 partitions, it will need one linux partition that is formatted as ext3 and one swap partition that you do not format at all.  (but i really would let ubuntu do the partitioning with the available free space, but hey it's you machine :D)

also, are you using some really obscure mouse (i.e bluetooth or something), tell us more we might be able to help, in the meantime to get you out of stook plug in a ps/2 mouse (quick edit, if you have one of course :S didn't want to sound rude)

---

### Post by adam212 on 2007-12-04
Thanks for replying.

Ok so from what i understand is that you want me to let ubuntu create the parititions the way it wants. But that would ruin everything, my c, d and my recovery volumes. All ubuntu setup really sees during installation is /dev/sda which i guess is the whole 250 gig drive not the free space. At that point i chicken out and quit the installation in fear of losing my precious movies and other stuff(by that i dont mean porn :popcorn:). Maybe i didnt understand you clearly. Can you explain more clearly.

The mouse i am using is a simple logitech usb mouse. I do have a ps/2 mouse but cant seem to find it (will try harder now).

---

### Post by gazj on 2007-12-04
if i remember rightly when you go through the installer options you get asked the question when it comes to partitioning

resize and use existing free space, see screenshot below

[http://news.softpedia.com/images/extra/LINUX/small/installinggutsy-small_004.png](http://news.softpedia.com/images/extra/LINUX/small/installinggutsy-small_004.png)

I really do see where you are coming from with your data loss, i would be concerned two with a process i am not familiar with.

Just to note linux/ubuntu does not see drives as letter, your first drive (if it's ide pata or a sata drive)
will be seen as /dev/sda the second drive would be /dev/sdb and so on

then partitions are as follows

first partition (probably has vista on it) will be known as /dev/sda1
a second partition (at a guess has your downloads and porn lol ;)- not sure what order your partitions are)  will be /dev/sda2
and so on (hope this make sense, i know it can take some time to grasp)

ubuntu will ask show you what it's going to do before you click the big OK button a few steps on, as long as it's not going to make any changes to these partitions then you are good to go ahead.

see screenshot

[http://news.softpedia.com/images/extra/LINUX/large/installinggutsy-large_006.png](http://news.softpedia.com/images/extra/LINUX/large/installinggutsy-large_006.png)

(it uses hda rather than sda in your case, don't worry about that, note it gives partition numbers)

really hope this helps you

if you are really worried, backup backup and backup, i would


Let me know ho you get on :) good luck

---

### Post by adam212 on 2007-12-05
I dont even get the option to resize the partition. The two options i get are 

Guided-use [COLOR="Red"]entire disk[/COLOR] <-------------if i understand this correctly, my answer is hell no to this one.

Manual-which just sees the whole disk drive but i guess would result in the same thing in partitioning the whole 250gig disk. 

Thanks.

Sorry if i am not being clear.I am doing my best.

---

### Post by vikram on 2007-12-05
**first of all backup critical data !!!**

using manual you can make your 25GB as one extended partition. this extended partition can be spilt into several logical partitions one for / for swap and suggest one for /home.

this will overwrite your 25 GB ext3 partition.

---

### Post by adam212 on 2007-12-05
But doing that will erase my windows, downloads and recovery volumes. Am i right.

Thanks

---

### Post by vikram on 2007-12-05
> **adam212 said:**
> But doing that will erase my windows, downloads and recovery volumes. Am i right.

Thanks

this will not effect the windows partition. this will only partition and format the 25GB ext partition you mentioned.

---

### Post by adam212 on 2007-12-05
Ok so i took screenshots to help make you understand that the setup wont detect the ext3 partition and it keeps wanting to install the os on the whole disk drive formatting the whole drive. It even warns me when i try to create a new partition table on the drive and the free space available clearly indicates it as a 250gb hard drive.

[[img]http://img2.freeimagehosting.net/uploads/th.37c70ab50e.png[/img]](http://img2.freeimagehosting.net/image.php?37c70ab50e.png)
[[img]http://img2.freeimagehosting.net/uploads/th.a8a7c075cd.png[/img]](http://img2.freeimagehosting.net/image.php?a8a7c075cd.png)
[[img]http://img2.freeimagehosting.net/uploads/th.9b2074aa46.png[/img]](http://img2.freeimagehosting.net/image.php?9b2074aa46.png)

Maybe this will clear up some confusion. Thanks

---

### Post by adam212 on 2007-12-05
You are not gonna belive this. This is the image i took from partition editor. All it sees is the whole disk which it thinks is unallocated free space, no wonder installer is having problems. Just to clarify the disk is not unallocated and i have my windows(ntfs), download (ntfs) and recovery volumes (fat32) there which boot up and work fine from windows. 

[[IMG]http://images6.theimagehosting.com/Screenshot.977.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot.977.png)


How do i make the partition editor detect the partitions? Tried refreshing gparted but it crashes. :(

I also found some other threads which go over the same problem(look at bottom). Any help would be greatly appreciated.

[http://ubuntuforums.org/showthread.php?t=469624](http://ubuntuforums.org/showthread.php?t=469624)

---

### Post by vikram on 2007-12-06
try using fdisk

sudo fdisk /dev/device-name

at the prompt type "p" to get a list of partitions.  see if this tool recognizes existing partitions

[http://linux.about.com/od/ptn_howto/a/hwtptn06t00.htm](http://linux.about.com/od/ptn_howto/a/hwtptn06t00.htm)

---

### Post by gazj on 2007-12-06
I'm really stuck on this one.  Never seen anything like it before.  One last thing i would try presuming you have a quick download speed is to download and burn the ubuntu alternate install cd and try that.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

notice the tick box for the alternative cd on the webpage, it will be a text installer (much like the start of an xp installer) hopefully that will detect your partition setup

It' about the last idea i have, i know it would be nice to do the live cd install, this install method does not look as nice but may get you out of trouble.  Note when finished you have exactly the same setup.

---

### Post by adam212 on 2007-12-06
Nautilus detects all the partitions and mounts them through the gui easily. Its funny that nautilus can recognize it but gparted and installer have trouble. I tried the alternate cd installer which doesn't work. fdisk does recognize the partitions but i am not sure how to use that to install Ubuntu on the ext3 parition.

Thank you both vikram and gazj for replying.

Edit: Here is what i get

/dev/sda1   *           1        3995    32089806    7  HPFS/NTFS
/dev/sda2            3996       30400   212098162+   f  W95 Ext'd (LBA)
/dev/sda5            3996       26009   176827421+   7  HPFS/NTFS
/dev/sda6           27138       30138    24105501   83  Linux
/dev/sda7           30139       30400     2104483+  82  Linux swap / Solaris

---

### Post by gazj on 2007-12-07
I just can't get my head around this one, i presuming your new to linux and i really don't want to see you fall at the first hurdle.

Is there anything unusual about your disk that you know of??

I take it, that it's a sata drive and not scsi.

Have you another hard drive you can put in the pc, there is some trickery would could do if you have another drive.

---

### Post by adam212 on 2007-12-07
To be honest i have been trying to install Ubuntu for about six months. I used wubi first to install ubuntu but it was mighty slow during startup so uninstalled it then i had acpi problems even after i turned it off. Mu computer is about a year old so i figure Ubuntu should be able to handle it after a while. From what i have researched, new computers that have recovery volumes are set up in way by computer manufactures that  confuse gparted. There is a lot of fuss about this on google and i am surprised that they haven't yet dealt with this problem. So if i were to format the whole disk (which i dont want to do) the installer would work fine. Sorry i don't have another drive. How do i check if it is scsi or sata.

Thanks for the help man.

---

### Post by gazj on 2007-12-07
if you don't know what scsi is then it won't be scsi, it's used mainly in servers, but can be used in normal machines as well.  What you suggest sounds likely, it a shame a real shame.  The best thing i can suggest is getting a second hard drive to put ubuntu on (if it's not a laptop) but that costs money which sucks.

Sorry we never got it sorted but we are a community of triers :)

---

