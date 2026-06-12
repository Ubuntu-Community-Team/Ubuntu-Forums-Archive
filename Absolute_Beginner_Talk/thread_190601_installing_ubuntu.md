---
title: "installing ubuntu"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-06
I have read the installation help topics : [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
and now I am very very confused
I want ubuntu run with winxp
if I understood right I should resize my winxp partition , make it smaller
and install ubuntu there but it's just 7 gb and I want more for ubuntu

I have :
c: winxp 7.8 gb/ntfs - almost no free space
d: 68 gb /ntfs
g: 78 gb /ntfs
h: 70 gb /ntfs

and - can I convert winxp partition to fat32 without harming winxp
or I don't have to convert my winxp partition ?

how should I install ubuntu ???
tanx ahead.

p.s
I am talking of ubuntu 6.06

---

### Post by kb3hkg on 2006-06-06
you can leave xp as ntfs, just defrag and then shrink the partition, fat32 is easiest to use for any drives u want to share files between the 2 on, and you can install ubuntu by shrinking one of those other partitions if you like, as long as the bootloader is setup properly which should not be a problem

---

### Post by oldmanstan on 2006-06-06
you should be able to install ubuntu on d,e or f

it doesn't have to be installed on the first hard disk or on the same one windows is installed on, that will save you the trouble of repartitioning and such since you can just take one of your pre existing partitions/drives and use it for ubuntu

---

### Post by MaximB on 2006-06-06
tanx  BUT I don't understand why should I shrink the winxp partition and how to do this ?

---

### Post by kb3hkg on 2006-06-06
You only need to do that if you are installing ubuntu there. As for how to do this, it requires the use of a program. If you want to do it from windows the common choice is Partition Magic. From linux possibly from live cd using Gparted for gui, or if you prefer fdisk or cfdisk on command line. For shrinking a partition gui is usually easier, and make sure you defrag it first.

---

### Post by aysiu on 2006-06-06
Forget about the shrinking--just install on D:, G:, or H:.

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html) should help you with that. Make sure you select **Manually edit the partition table**.

---

### Post by Kobalt on 2006-06-06
Install Ubuntu on D: G: or H: , just like aysiu or oldmanstan suggested, it'll be much easier... Plus 7gb is already a bit small for winxp, if you shrink it then.. :(

---

### Post by kb3hkg on 2006-06-06
I agree, but it looked like they were also ntfl formatted according to his first post, so something still needs to be done to create space.

---

### Post by catlett on 2006-06-06
[QUOTE=kb3hkg]I agree, but it looked like they were also ntfl formatted according to his first post, so something still needs to be done to create space.[/QUOTE]
Yes it will be done. The whole drive will be given to ubuntu i.e. 68gb. There is no room on C, it is only 7.8gb.

Just choose "manually edit the partition table" then select one of the 3 other drives. They will be listed. Then you should be able to select "automatically partition the drive". The Ubuntu installer will reformat and partition the drive to the required filesystem and size partitions.
Follow Aysiu's link. It is more up to date. If you get confused abort the install and post. One of us can walk you through pre-partitioning your hard drive before the install but you shouldn't have a problem with Aysiu's guide and choosing d,e or f and automatic partitoning. Good luck.

---

### Post by MaximB on 2006-06-06
thanx guys - but if I select "automatically partition the drive"
1.would I get the chose wich file system I use ?
2.would it format the hole data on the drive so I would never restore it ?
3.I thought about setting XFS or JFS instead of ext3 - has anyone used it or reccomend it ?

---

### Post by catlett on 2006-06-06
The easiest way to have the most control is to pre-partition your drive. I like gparted live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I like it because it is a small download, 30mb and it runs from a live cd. You start your computer with the disc in the drive and you boot into a setup that starts gparted.
All your drives will be available.The best part is because it is a live cd your hard drive isn't mounted and you can make changes to the drive right then. Most applications run from your OS and you have to reboot for the changes to happen.
Pick a drive and make the partitions you want. For Ubuntu you should make 3 partitions. 1 for root, 1 for swap and 1 for home.
All your other drives will be mounted as data files. If you keep them ntfs you will be able to read from them but not write. What I would do is take one drive and make the 3 ubuntu parttions plus a fat32 partition for data. Ubuntu and windows can read and write to it so you can share the data on it.
This would be my partitiong. I would choose D and divide the 68gb like this.
```
/                    7.5gb    ext3
swap                 500mb    swap
home                 20gb     ext3
/hda6                40gb     fat32
```
This is how I would go about it. Put the gparted disk in and boot. When you get into gparted choose drive d which will be labeled /dev/hda2.
Click on the drive and choose "delete". This gives you a blank start. Click on the drive and choose "new". A bar graph will come up with your drive. Click on the right side of the bar and drag it over until it says 7.5gb. There should be no data before it and 60.5gb after it. Make this partition a primary ext3 partition. (I'm assuming you have one hard drive and it is partitioned into 3 already so the next ones have to be "logical" partitions.)
Now we have to make an extended partition. Click on the drive. Right click again to get the menu and choose "new". Don't move the bar, you want to select the remaining space. Then go to the boxes and select from the top box "extended" partition. That's it. Choose add and go to the next one.
Click the graph,choose new, drag from right to left until you have 500mb. Then choose in the lower box "linux-swap". From here on out you don't choose primary or extended or logical. They are automatically logical partitions.
Hit add to finish swap and click on the graph again. Drag from right to left until you are at 20gb. Choose ext3 and hit add.
Click on the graph,choose new and don't move the bar. Your going to make the remainder fat32. Pick fat32 and hit add.
Now go up to the top and hit "apply". Let it do its thing. When it is done reboot.
When you go to install all the partitions will be listed. The only ones you have to do something to are the 7.5gb, 500mb and the 20gb. The other parttions are going to be automatically mounted.
Choose to manually edit the partition table when you get to partitioning. There will be a page with all your partitions listed and drop down menus in front of them. In front of the 7.5gb choose "/" (/ is the label for root). In front of the 500mb choose "swap". In front of the 20gb choose home. In the circle after /, swap and home check them off. Don't check off the circles after any other drive. The circles are listed under "format?". This means format those partitions. You want /,swap and home formated but nothing else.
Your fat32 data should be labeled hda6. It may not depending on the other drives but it will be the only one that is fat32. Just remember the label before the fat32 partitioon.
When the install runs you will have a /,swap, and home formatted for linux. You will have 3 drives formatted ntfs that will be mounted by ubuntu but you won't be able to write to them only read. And finally you will have a 40gb fat32 that ubuntu can read and write to as well as windows.

This is just how I would do it. You can google jfs and xfs for more info I don't know how they interact with the ubuntu system.

---

### Post by kb3hkg on 2006-06-06
I can only answer #2, repartitioning a drive does format the hole drive, so there would be no restoration from this

---

### Post by MaximB on 2006-06-07
thanx again 4 helping me but tell me plz what are the roles of the partitions
/
swap
home
/hda6
?
and I have 2 hard disks :
1 - c , d
2 - e ,h
does it changes anything about your explanations ?

and kb3hkg - I mean by changing a partition from ntfs to fat32 or to ext3
is the data deleted ?
cuz if you change fat32 to ntfs it doesn't delete the data

thanx again

---

### Post by kb3hkg on 2006-06-07
/ is your main booting drive
swap is like virtual memory
home doesn't have to be seperate
/hda6 would be just another drive

having two disks doesn't matter, just repartition the area you want to use as we have already covered

when switching to ext3 data would be deleted

---

### Post by MaximB on 2006-06-07
1.I have 1gb of ram - why do I need the swap then ?
2.and were does the installation files go to ? and the programs and the updated/upgrades ? - to home ?

if I understood you right I need to delete partition G that lies on hard disk 2
and create 3 partitions instead
3.the first one would be the boot paritition - how much gb I shel put to it ?
4.the second would be swap - I thought about putting 2 gb to it
5.the 3 one would be home - how much gb do you reccomend putting to it ?
I have 78gb total in partition G
but I have partition H too
I want to leave partition D alone or convert it to fat32
6.if I convert from ntfs to fat32 - does it delete the date ?

---

### Post by MaximB on 2006-06-07
really thank you all for helping me so far
but I have afew more minor questions and if I won't pose a reply my questions would be forgotten
so please help me with the questions above

p.s
you are so quick - after an hour my pose "jumped" a list.

---

### Post by MaximB on 2006-06-07
I HATE doing this...please help me
it's simple questions for linux users

---

### Post by carlosqueso on 2006-06-07
1. I'm not sure, I've never had that much ram, but it may be a good idea just in case you do something memory-intensive
2-3.root (the /) should have 4-5 GB (others may say more) because this is where all of the programs that you install and the operating system (as well as everything BUT stuff that goes in /home) will go.  Mine is 13GB, but only because I had a 13GB drive that I couldn't be bothered to partition.
4.  2GB should be fine for swap....any more would just be wasteful.
5. /home is where all of your files will go.  It is the only one that you will be able to edit without using sudo.  This will be the partition in which you want to put all of your files, so use as much as you think you'll need for files.  I have a 140GB partition dedicated to /home on my file server, but it's specifically a dumping ground. 

As for your last question, I couldn't help you. Sorry.

---

### Post by MaximB on 2006-06-07
tanx again
does the home partition have to be ext3 or linux system or I could format it as fat32 and share it with winxp ?

---

### Post by catlett on 2006-06-07
You don't need a seperate boot. Just make a / (root), a swap and a home. Home doesn't have to be on a seperate partition but it should. If home is seperate you can reinstall the operating system without touching your data.
Home has to be ext3. The hda6 is the FAT32 partition. You should have a fat32 so windows and linux can share data. Linux is unstable writing to ntfs and windows can right to ext3 but thetre are some quirks.
It is even easier to partition now that you have seperate hard drives. Just chose an entire hard drive for partitioning and divide it into 4 partitions. A / (root) partition. Tjhis is where the filesystem goes or the base installation. Swap is the virtual memory, like the swap file in windows. Avctually with 1gb you won't even touch it if you don't video edit or anything like that. Home is for your personal data. This is li,me "my documents". All your personal stuff goes there. Last is just a regular partition but formatted to FAT32 so linux and windows can share data.
So use gparted to do your partitionintg. Choose an entire hard drive to format. Then make these parttions.
```
/               7gb       ext3
swap            512mb    swap
home            20gb     ext3
data            40gb      FAT32     (I called this /dev/hda6 before because that should be what the partitoner will label it. The point I was trying to make was that you don't have to do anything to it when you imnstall. Let the indstall label it and mount it. the 40+ means whatever is left make it part of the fat32 partition)
```


Just run the install and manually edit the partition table. When you get to the partitioner make these partitions /, swap and home like I have here. There is a link in my signature with a good guide.

---

### Post by carlosqueso on 2006-06-07
[QUOTE=MAXDDARK]tanx again
does the home partition have to be ext3 or linux system or I could format it as fat32 and share it with winxp ?[/QUOTE]

You probably don't want to do that, but you can do what catlett said and have a small ext3 home partition with a larger, FAT32 formatted partition. That'd probably work best for you.

---

### Post by catlett on 2006-06-07
Sorry to leave you hanging a bit. On the weekend I'm around all the time but during the week I work. The last post I snuck in at work when I stopped back at the shop between jobs.
The main reason for this post is to reply to this question .> if I convert from ntfs to fat32 - does it delete the date ?
YES IT WILL. You will loose any data you have on the ntfs when you format. Since you have alot of space just choose one of your hard drives to partition. The 78gb will be plenty.
You only need a 5gb for / "root". This is where the system files go. Mine is only filled up to 3.5gb. I said 7gb because you have alot of room. This has to be ext3 or ext2 (or reiserfs, xfs,jfs but don't concern yourself with that just know you don't want fat)
Swap is virtual memory like the swap file in windows. The rule of thumb is twice your ram i.e. 256mb ram = 512mb swap. But linux is not resource intensive. Unless you are using your system for something that requires a ton of ram you don't even need any but I put 500mb just for the sake of having a swap to mount. 
Home is for your personal files. It needs to be a good size but you can store data to your other drives as well. 20gb is plenty and it needs to be ext3 (just use ext3 for linux filesystems. it keeps it simple and it works well)
"Data" . This partition can be labeled anything. It should be the remainder of your 78gb drive, which would make it around 50+gb. Make this partition FAT32 so linux and windows can share the data. It is plenty of space to share with. I wouldn't recommend more because ntfs is a better filesystem in windows and ext3 is a better filesystem in linux. I wouldn't allocate too much to fat32 because it isn't efficient to do.


Just use "gparted" from the live cd. There will be a drop down menu in the right hand corner that will let you select the 78gb drive for partitioning. The first step is to delete the drive. Then make you partitions. You don't have to worry about the "extended" partition since you have the whole drive. You can have 4 primary partitions on a hard drive, so all the partitions can be primary.
Just start with / "root". Make that first so it is up front. Make it a 7gb ext3 partition.
Next make a 500mb swap which will be formatted as linux-swap.
Make the home partiton. 20gb ext3 partition.
Make the rest a fat32 partition.
Make sure you "apply" all the changes.
Reboot and put in the ubuntu install disc. Go to "manually edit the partition table". Select the partitions you just made and label them /, swap and home from the drop down menu in front of them. Check off the circle next to them that has the heading "format?". DO NOT check off "format?" on any other partition. Don't rename any partition. All the other drives and partitions will be mounted by ubuntu. They will be icons on your desktop after install and you will have access to them.

---

