---
title: "Need Help With Dual Booting Vista And Ubuntu - vista already installed"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by mitchbeast on 2007-06-24
Im Tryin to install ubuntu as a second OS alongside Vista. 

The ubuntu 7.04 disc doesnt ever boot when my computer starts up and i hav burned the files to the disc and its not a CD with an ISO file on it , it has all the files and folders instead. i cant workout why it wont boot. 

Please help. Thanks :D

---

### Post by Ziox on 2007-06-24
you should probably try to burn it to another cd.

however, the problem could be with Vista.  I have heard that certain versions of Vista has a special feature that could prevent hackers (normal people) to access the hard drive, including but not limited to installing another OS.

---

### Post by mattg89 on 2007-06-24
It sounds like you need to change the boot order. When your PC boots up does it should say something like "Press Del to Enter Setup". Do so. Change the boot order so that your pc boots from CD before Hard Drive.

---

### Post by Ziox on 2007-06-24
I think I over-complicate things sometime.  Try mattg89's advice first

---

### Post by logos34 on 2007-06-24
> i hav burned the files to the disc and its not a CD with an ISO file on it , it has all the files and folders instead. i cant workout why it wont boot.

You need to burn the iso as an IMAGE to the cd.  
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then do as mattg89 suggested and set the BIOS to boot the cdrom first.

Good luck and have fun with Ubuntu!

---

### Post by mitchbeast on 2007-06-24
ok well firstly, i made a partiton on my hard drive size: 10GB and its type is FAT32 so linux can see it. i booted linux from the startup and i get to the install screen. i follow the steps till i get to the part where you choose the space to install it to. there are no partitions there for me to install 2 even though on vista there are as i created it. im wondering whether i have to make it have a swap memory of 256mb as it says that on the ubuntu setup screen.

if i make the 256mb swap part on the 10gb partition, will ubuntu install or have i still got a few things to do ?

please write back. **_Thanks :D**_

---

### Post by logos34 on 2007-06-24
no, you need to install linux / (root) on an ext3 or reiserfs and make a separate swap of 256mb+ on it's own partition.  Can you reformat the 10 gigs as ext3, or can you free up more space for root?  Windows can read and write to ext2/3 with fs-driver and linux can natively read NTFS windows partition; you can add write capability with ntfs-3g driver.

---

### Post by mitchbeast on 2007-06-24
Youve lost me a bit there sorry. i have a 250GB hard drive. when i go to the 10GB partition for linux if i right click it says : Format and the other options. when i press format i can change the type back to NTFS, underneath it says: Allocation unit size: what shall i put it as?

Also Theres a tick box saying quick format. i need more of an easier step to follow sorry. if i need to create a new partition from scratch, is there any chance i can put that 10GB back on to my main hard drive? instaed of it being a seperate one? Thanks

---

### Post by logos34 on 2007-06-24
> **mitchbeast said:**
> Youve lost me a bit there sorry. i have a 250GB hard drive. when i go to the 10GB partition for linux if i right click it says : Format and the other options. when i press format i can change the type back to NTFS, underneath it says: Allocation unit size: what shall i put it as?
you need to make it ext3, and put the full amount, 10gb.  (not sure about the quick format option--I thought that was just for ntfs).  Then you'll need to create the swap.  Just don't click any boxes to 'format' your big vista partition!

 if i need to create a new partition from scratch, is there any chance i can put that 10GB back on to my main hard drive? instead of it being a seperate one? Thanks

Not sure what you mean.  You can expand vista partition back to reclaim the 10gb you lopped off for linux, if that's what you're asking.  (you can even do it from within vista.  it has a feature for that unlike xp).

edit: if guided partitioning is not working as it should try the 'manually edit partition table' option.  It's not that much more difficult.

---

### Post by mitchbeast on 2007-06-24
well i got rid of that 10GB partiton and started a new 1....... i come to set it up and all the options im allowed to do are:

Select my allocation unit size: i put it higher than 256mb

choose what type: NTFS or FAT32: i chose NTFS as you said before..

and a tick box which allows file compresison but i did not tick it. 

i dont have a clue how to make it EXT2 or EXT3 so linux can view it, or, make a swap..i just dont seem to ever get those options. sorry if im maing you explain this more thouroughly than you expected.


Thanks Again :)

---

### Post by logos34 on 2007-06-24
Take a look at this:

[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by logos34 on 2007-06-24
Here's my favorite illustrated install guide with screenshots:
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by mitchbeast on 2007-06-24
I read those... but the thing is when it gets to the partition part ([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) : this  folllows my installation steps better than the 1st link) there are no drives or options to select. i dont know how to make an ext2 readable partition or the swap 256mb+. maybe you could telll me the command lines or a step guide on how to. thanks

---

### Post by fumduck on 2007-06-24
maybe this will help??

[http://apcmag.com/dualboo]("http://apcmag.com/dualboo")

Good luck

---

### Post by logos34 on 2007-06-24
I'm most familiar with the manual method (haven't done a guided in quite a while).  So try this:

When you get the 'prepare disk space' choose manual. I believe the next screen will bring up the gparted partition screen with your main vista paritition listed and any other partition your created, as well as leftover unallocated space.  You need to make an EXT3 and swap partition, so if it's easier to just delete any partition you just created, do so, but don't touch the vista partition.  It may want to write this to disk (can't recall if this comes before or after the next step).  Then from the menu choose 'new' and create the ext3 parition out of that raw space.  Us the full amount MINUS the rough size of the swap (256mb).  Then create a 'new' swap space on the remaining space.  Then you have to specify the mount points for each.  The ext3 will be '/', and the swap '/swap'.   
Make sure ONLY the '(re)format' boxes for / and /swap are ticked.

---

### Post by logos34 on 2007-06-24
> maybe this will help??

[http://apcmag.com/dualboo](http://apcmag.com/dualboo)

says 'page not found'

---

### Post by bigken on 2007-06-24
try creating the partitions with the gparted liveCD download it from my signature

---

### Post by Dennis the Menace on 2007-06-24
> **logos34 said:**
> says 'page not found'

There's a T missing off the end of the link, should be boot.I think.

---

### Post by mitchbeast on 2007-06-25
i have a 20GB unallocated partition waiting for linux at the moment. i run linux...press install... the first step is choose my location, then i choose keyboard, then i get to the prepare disc space...([http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)) on that link there are 3 options.. i only get 1 option and thats manual. then theres nothing i can do :S but i followed the steps from that link way before you guys told me and i got stopped at this point. even though i have a 20gb partition which is left unallocated for Linux. anyway when i choose the option: manual i press continue... the next step is just a blank box with column headings such as:

Device           Type

etc

but there are no drives to install to. Linux isnt seeing my vista partition or my 20GB unallocated partiton.

sorrry if i seem dumb to you guys :(

thanks

---

### Post by AriciU on 2007-06-25
What partition manager did you use? Is the 20GB partition of Linux EXT2/EXT3 type?

---

### Post by mitchbeast on 2007-06-25
I used vista's disk manager partitioner. it just took 20GB off my vista partition and now its in no format so its ready to be tunred into EXT2/3. i just dont know how

---

### Post by AriciU on 2007-06-25
Heh. I though you used a dedicated partition manager like pqmagic & co but i remembered there aren't many that work on Vista.

Anyway, insert the Ubuntu LiveCD, boot from it, don't click Install and go to System / Administration / Gnome Partition Editor.

Then chose your harddrive where your partition resides and you will see an empty 20GB partition. Right click it and resize it in 3 other partitions:

1. 19GB
2. 500Mb
3. 500Mb

Then right click each one of them and hit Format to ->

1. Linux EXT2
2. Linux EXT2
3. Linux Swap

Then hit install, select your keyboard and stuff, then when you get to partitions select Manual. Wait for it to load up and it will find all your partitions. Set them as:

1. "/" (19gb linux ext2.. without the " " of course)
2. "/boot (500mb linux ext2)
3. swap (this one should be autoset)

---

### Post by mitchbeast on 2007-06-25
ok ill do that :D sounds like its going to work to me... 

1) because i feel so noob now remembering i did see that gnome partitioner when i went searching around linux :( man i feel dum. hehe

2) it seems like the only option left that feels as though its goin to work...

thanks a lot ill let you know in a sec if it works :D

---

### Post by AriciU on 2007-06-25
I've edited my post above... hope you read the edited version otherwise it won't work without a swap partition :P

---

### Post by neo.patrix on 2007-06-25
what is the size of ur RAM ? normally it is advisable to have size of your swap same as size of ur RAM.

---

### Post by mitchbeast on 2007-06-25
ok i went on the GNOME partition editor and this is what happend...nothing! there where no hard drives detected at all! i left the 20gb unallocated so it was in no format...Linux didnt detect it.

So then i decided to make it FAT32 because GNOME says it can see it but still it cant see the 20GB partition.
when i format it to FAT32 does the allocation unit size have to be a significant vaule? or can it just be left as "defeault" as it is now?

Theres something im not doing right...but i dont have a lcue what it is because i folllowed 3 different peoples steps :(

RAM is 1GB pretty small i know :P

thanks

---

### Post by logos34 on 2007-06-25
'1gb ram pretty small' -- that's plenty for linux (but not for vsta)...So you should just make your swap (if you get to that point!) around the same.

This is pretty odd...The only thing I can think of is get the Gparted live cd and see if it will detect the partitions correctly (the live cd version is the industrial strength bversion of the one that's on the ubuntu live cd.

---

### Post by bigken on 2007-06-25
have you tired the gparted liveCD ?

---

### Post by mitchbeast on 2007-06-25
would you mind poting me a link to a Gparted download? is it just the same as Ubuntu? will the desktop and all the icons and that be the same as Ubuntu or will they be different?

---

### Post by mitchbeast on 2007-06-25
ive got a link now BTW. the ISO is only 48.5MB though... is that the right size for an OS?

---

### Post by logos34 on 2007-06-25
yeah that's correct size (it's a utlilty cd not OS)

---

### Post by bigken on 2007-06-25
> **mitchbeast said:**
> would you mind poting me a link to a Gparted download? is it just the same as Ubuntu? will the desktop and all the icons and that be the same as Ubuntu or will they be different?


its in my signature

---

### Post by AriciU on 2007-06-25
If you can't do it with gparted try a windows based solution like Partition Magic or Paragon Partition Manager. I use paragon but i don't know if it works on Vista.

---

### Post by mitchbeast on 2007-06-25
so do i BURN this iso to a disc then insert it when linux is Booted to the desktop and then do it myslef from there? or do i boot the disc from my computer start up like with the ubuntu boot disc?

---

### Post by kd5aw on 2007-06-25
The best way I find to install dual boot, is to install windows first. Using 2 seperate drives is prefered. After Windows installation is complete make sure the drive 's jumper is jumped to slave. To install Ubuntu, set the second drive as "Master". Insert cd and follow prompts. When you come to the disk choice part, make sure that (hd1a is chosen. I used this method to install a dual boot system yesterday.
Good luck

---

### Post by tgbrowning on 2007-06-25
The source of confusion might be what partitioning program you're using and *where*.  

If you're doing the partitioning from within Vista, don't sweat what the format type it. At all. I don't think Vista gives you the option of formating a partition as ext2/3. I'm pretty sure Partition Magic does, but it's not necessary to use Partition Magic, because you can change the structure during the install for Ubuntu.  Heck, you can even leave it unformated entirely.

Run the install and when you get to the part whereyou do the partitioning, do a manual partition.  There, you can tell it to make the partition you have set aside for Ubuntu what you like, ext2 or ext3. 

Do NOT use NTSF. Ubuntu can read it okay, so you will have access to the files in the Vista partition, but they are read only. You can't write to that partition at all.

Also, Quick Format can only be done on a partition that has already been set up. All it does is rewrite the root directory description so the links to individual files and folders disappear. Any data that's out on the drive is untouch -- until it gets overwritten by newer files and folders.

Hope this helps.

Browning>>>

---

### Post by logos34 on 2007-06-25
> **mitchbeast said:**
> so do i BURN this iso to a disc

yes, burn the downloaded iso as an image, just like you did the ubuntu install cd.

> or do i boot the disc from my computer start up like with the ubuntu boot disc?

Yes. 

[Bu you've probably already figured all this out since your last post].

---

### Post by mitchbeast on 2007-06-25
My 20GB partition is type FAT32....


i booted Gpartition...and what a suprise there were no partitions whatsoever that it picked up.. there was nothing for me 2 do 





GRRRRRRRRRR

please i need help its unfair this linux buisness isnt working:(

---

### Post by AriciU on 2007-06-25
Partition Magic or Paragon Partition Manager are your friends if they work on Vista... Search for some other Vista partition utility if they don't.

---

### Post by logos34 on 2007-06-25
> **mitchbeast said:**
> My 20GB partition is type FAT32....


i booted Gpartition...and what a suprise there were no partitions whatsoever that it picked up.. there was nothing for me 2 do 





GRRRRRRRRRR

please i need help its unfair this linux buisness isnt working:(

So, what if you click on 'Gparted' in the menu (top left), then hit 'Refresh', anything?  Or the right side of the toolbar there is also a drop down menu for devices, is there anything listed there or is everything grayed out?

Maybe you wll have to try a partitioner that's more vista friendly

---

### Post by mitchbeast on 2007-06-25
i already did the refresh thing... i do try a few things out but nothing seems to work its dawning on me that im not going to ever install linux.... :(

could you tell me a more vista friendly partitioner? 

thanks m8

---

### Post by logos34 on 2007-06-25
try deleting that 20gb fat32 partition using vista.  Then boot back into gparted cd and see if it recognizes vista and you can add new ext3 and swap partitions on the empty space. Other than that you could try suggestions in post #39.

---

### Post by bigken on 2007-06-25
somethings not working not sure if its linux 

there is another way you can try ubuntu use vmware for windows if you like like it enough you might consider ditching windows ;)

im sure it vista stopping you formatting the drive :(

---

### Post by tgbrowning on 2007-06-25
> **mitchbeast said:**
> i already did the refresh thing... i do try a few things out but nothing seems to work its dawning on me that im not going to ever install linux.... :(

could you tell me a more vista friendly partitioner? 

thanks m8

Grab a beer or some really ugly and old coffee and sit back for a second.  

IF you've gotten a partition set up already for ubuntu, you don't have to do anything more with Windows. In point of fact, [COLOR="Blue"]You do not have to do anything with Windows to get a dual boot set up for Windows and Ubuntu[/COLOR]

It can all be done from the install if you follow the directions of the install and don't panic.  Or if you're like me, get pissed off and start swearing.

IF you're on line and have access to yahoo messenger, see if I'm on line and ring me. I can walk you through it and answer any questions you might have before you start anything major.

look for [email]tgbrowning@yahoo.com[/email].

Give me ten or fifteen minutes because I might be at another computer.

The manual partitioning in the installation works fine even if it is a bit cryptic. If you had a problem understanding what exactly you did have (according to ubuntu) be advised it is cryptic -- there's nothing wrong with you.  

Browning>>>

---

### Post by mitchbeast on 2007-07-30
sorry i havnt been talkin guys :( i kinda got annoyed and left it for a bit... i dumped vista...decided it was limiting some of the things i could do on xp so i decided to go back to windows xp....
 and guess what..
i got partition magic registered version, created a 50gb partion in EXT2 type expecially for linux as the program stated it. restarted and followed instructions till all was finished,,,
i then went and put the ubuntu disc in, got onto ubuntu and back where i was again with vista...

AND STILL DIDNT WORK!

100% definete there was a partition EXT2 type waiting for linux but the installation doesnt see it neither does the GNOME partition editor!

i when on the command terminal and tryed a few things but still no luck!

i think its my HardDrive Which doesnt work with linux, not a software error

theres no other thing i can think of, unless u guys can :)

and by the way browning thanks for your advice and hel:) 

i dont have yahoo, sorry

any help appreciated 

thanks and sorry for being away for a fair amount of time :(

---

