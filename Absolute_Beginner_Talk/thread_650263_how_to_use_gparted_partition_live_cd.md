---
title: "how to use gparted: partition live cd?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by shucks on 2007-12-26
Can someone give me step by step instructions on how to use my gparted live cd in order to be able to either 

- dual boot my laptop with linux and xp
- or change it to only xp 

(i have a xp cd too, but it doesn't recognize harddisk probably because i need to partition it)

Currently I only have linux ubuntu installed. I had mistakenly erased my vista when installing linux, so now I'm trying to get windows xp back at least.

Please, help. Thank you

---

### Post by kpkeerthi on 2007-12-26
See the section **Creating a new partition** in [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by shafin on 2007-12-26
in GpartED, select the linux drive, select resize and take out spaces for your vista drive.If you have a seperate drive for vista,you'll just need to move any data from that to the linux partition.Then boot from xp installation CD,in the first case,you'll have unpartitioned space and in the second case,you'll have a linux drive,if you have a linux drive,format it,r create and format a drive from the unpartitioned space.

Case 1: Dual booting:After booting,you'll see only xp,but no lubuntu.To fix it,Boot form Linux live CD.mount your primary partition in the terminal type  **sudo grub-install /dev/hda **It should be **/dev/sda **if you have a SCSI HDD a better guide can be found [here]("http://www.daniweb.com/blogs/entry708.html") on GRUB.Or you can simply re install ubuntu,if you have not customized your installation.

Case 2: XP only:If you need to use xp only,boot from ubuntu live CD, select the data you want to get from the ubuntu partition,and move them to xp partition.Afterwards,use xp disk manager form control panel>administrative tools to erase/resize/merge and format your ubuntu and swap disk.

---

### Post by shafin on 2007-12-26
oh,and another How toon GRUB restoring:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by shucks on 2007-12-26
ok so I tried using the cd to see what happens and this is what I got:

Partition ||||||||Filesystem ||||||Size ||||||||||Used |||||||Unused ||||Flags
/dev/sds1 ____ext3 __________71.45gb____7.73gb____63.71gb___boot
~/dev/sda2 __extended ______3.08gb
  /dev/sda5 __linux-swap _____3.08gb

(I tried to arrange it neatly into colums but uh..yea)

Formats: ext2,ext3,fat16,fat32,nfs,nfs+,jfs,linux-swap,ntfs,reiser4,reiserfs,ufs,xfs

So I'm guessing the 71.45gb is the total amount of hard drive space on my laptop. linux is only 3.08, so..

I can resize linux? but its already so small or it looks small at least...not sure what to do..

What I want is about is either to have 40gb for xp and the rest for linux or, only xp. I'm leaning towards only xp now.

---

### Post by shafin on 2007-12-26
No,the linux-swap is the swap drive,equal to the cache file in windows.

You need to resize this drive,its the linux drive:
/dev/sds1 ____ext3 __________71.45gb____7.73gb____63.71gb___boot

as it has 63 GB free,you can get your drive or drives out of it,just follow the procedure,if you have any problems,ask again

---

### Post by zvacet on 2007-12-26
It looks like you installed Ubuntu on one partition and you don´t have separate home partition,so everything you have (data,personal files) is on that partition.You have just **7.73gb unused space** wich is not enough.First of all [backup your data](http://www.psychocats.net/ubuntu/backup) and after that you can make [separate home partition](http://www.psychocats.net/ubuntu/separatehome).After all this you will have free space for Windows.After Windows install you will need to reinstall [grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub).

---

### Post by shafin on 2007-12-26
He used 7 GB,has 63 GB free :)

---

### Post by zvacet on 2007-12-26
Yes,my mistake and overlook.In that case even better.

---

### Post by shucks on 2007-12-26
ok so now ext3 which is the linux one is shrunk to about 10gb. I created a new one ext2 which is going to be the windows one and its all the rest, 61.68gb

But when I tried to put in my windows xp cd after reboot it said that it couldn't find the harddrive. What do I need to do now?? :(

heres a picture
[IMG]http://img.photobucket.com/albums/v509/blacangkshiet2/Screenshot--dev-sda-GParted.png[/IMG]

edit - changed ext2 on new to ext3 and i followed how to make a new home partition on the link that one of you guys showed me

---

