---
title: "2 last questions b4 dual booting"
date: 2007-10-27
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2007-10-27
1- after i turn off my MB, and tun it back on, what OS is it gona go to by default? what do i hold down to get the option to change what it boots to?

2- i read through the guide a bit more today, and im having some trouble understandin this- 
> *At step 4, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3 (and /dev/sda4 if it exists) from /dev/sda. Create an ext3 partition taking up all but 512MB of the disk and mount it on /, and create a swap partition taking up the remaining 512MB. Click Forward.

that step seems a bit confusing to me. so leme breakit down and see if i can put into words what my problems are. first off, where it tells me to delete something, is that gona be like a folder in a drop down menu? second- where it says create an ext3 partition... how in the world do i do that? is it an option given to me, andthen im supposed to only leave 512 mb HD space left on the partition for it? :confused:

---

### Post by dmber on 2007-10-27
1) i've had better luck with rEFIt than Boot Camp, just because it's a better menu with more configurability.  I've changed mine so that the menu always shows up and it boots to Ubuntu after a 5 second delay.  You can change both which OS it boots to and how long of a delay until it auto-boots.

2) That's one thing I would change about the guide: as far as I understand, your swap has to be as big as your amount of RAM to be able to hibernate.  as far as how to partition, you can either post a screenshot here and we'll tell you exactly what to do with it or someone else can tell you before you do it.  that's as helpful as i can be...i know i can tell you exactly what to do if i see your partition table, but without seeing it, i can't remember exactly off the top of my head what to do.  (take a screenshot is in Applications -> Accessories)

---

### Post by stealthsniper96 on 2007-10-27
> **dmber said:**
> 1) i've had better luck with rEFIt than Boot Camp

are there any guides on here for setting it up with rEFIt?

---

### Post by cyberdork33 on 2007-10-27
> **stealthsniper96 said:**
> are there any guides on here for setting it up with rEFIt?

just set it up normally, then when you boot back into OSX, install rEFIt.  (actually, you can install rEFIt before installing Ubuntu, it won't hurt.

---

### Post by stealthsniper96 on 2007-10-27
> **cyberdork33 said:**
> just set it up normally, then when you boot back into OSX, install rEFIt.  (actually, you can install rEFIt before installing Ubuntu, it won't hurt.

so i just run rEFIt and ill be fine?

---

### Post by cyberdork33 on 2007-10-28
rEFIt will make a menu come up each time you boot so that you can select which OS you want to boot. It will default to OSX, but you can change it to default to a legacy OS, if that is what you want.

---

### Post by stealthsniper96 on 2007-10-28
im not so much talking about booting, as i am setting everything up. so about setting it up, will there be like on screen instructions and what not for me to follow?

---

### Post by cyberdork33 on 2007-10-28
> **stealthsniper96 said:**
> im not so much talking about booting, as i am setting everything up. so about setting it up, will there be like on screen instructions and what not for me to follow?
try downloading it. there are instructions included, but it uses the OSX installer system anyway. (This doesn't work in Leopard, but the included 'manual' instructions work just fine.)

---

### Post by stealthsniper96 on 2007-10-28
ok i just ran the installer. now what do i do?

---

### Post by cyberdork33 on 2007-10-28
> **stealthsniper96 said:**
> ok i just ran the installer. now what do i do?

Nothing. rEFIt is installed. What do you want to do? You keep asking what to do now, but you don't say what it is you want to accomplish? If you are ready to install Ubuntu, burn the install CD, and boot it up.

---

### Post by stealthsniper96 on 2007-10-28
> **cyberdork33 said:**
> Nothing. rEFIt is installed. What do you want to do? You keep asking what to do now, but you don't say what it is you want to accomplish? If you are ready to install Ubuntu, burn the install CD, and boot it up.

yes i want to install ubuntu. so when i go to install it, should i do a normall install or like a partitioned install?

---

### Post by cyberdork33 on 2007-10-28
> **stealthsniper96 said:**
> yes i want to install ubuntu. so when i go to install it, should i do a normall install or like a partitioned install?

You will have to make a partition for Ubuntu. That is a 'normal' install. You can use bootcamp to make a windows partition, then in the installer, tell it to use the windows partition and reformat it. (It will format it to a linux partition like ext3). Then you can proceed as normal.

If you want a swap partition, you would delete the windows partition (in the Ubuntu installer) and tell it to use the free space. It should automatically create a root and a swap space.


You can boot the live cd, and get to the partitioning part so that you can see what you are working with, and then ask further questions, but I really think you should try it out as you are making it seem more difficult than it really is.

---

### Post by stealthsniper96 on 2007-11-02
> **cyberdork33 said:**
>  but I really think you should try it out as you are making it seem more difficult than it really is.

yes, i propably am, so please bear with me. :)  i just got around to runnin the live cd and played around with the installer. i went to the section "prepare disk space" and i got 3 options. guided- use entire space; guided- use free space; and manual. i have about 15gb free and i want 10 for ubuntu. now, im assuming that i need to use the manual option, so will that just show like 80 gb hdd, 15 gb free. andthen ask me how much space i wana partition off for ubuntu? so if i were to say 10gb, would that just use the 10gb, and not touch my mac partition, or if i do this will my whole hd get messed with and ill have to re-install everything? i guess my other option is to try to use the bootcamp 1.2 dmg i downloaded the other day but now that leopard is released im not completely sure itll work. thx for the help. and if it matters, its ubuntu 7.10 im usin here to install.

---

### Post by cyberdork33 on 2007-11-02
> **stealthsniper96 said:**
> yes, i propably am, so please bear with me. :)  i just got around to runnin the live cd and played around with the installer. i went to the section "prepare disk space" and i got 3 options. guided- use entire space; guided- use free space; and manual. i have about 15gb free and i want 10 for ubuntu. now, im assuming that i need to use the manual option, so will that just show like 80 gb hdd, 15 gb free. andthen ask me how much space i wana partition off for ubuntu? so if i were to say 10gb, would that just use the 10gb, and not touch my mac partition, or if i do this will my whole hd get messed with and ill have to re-install everything? i guess my other option is to try to use the bootcamp 1.2 dmg i downloaded the other day but now that leopard is released im not completely sure itll work. thx for the help. and if it matters, its ubuntu 7.10 im usin here to install.
Boootcamp will work if you turn back your system clock ;)

you can use the manual partitioning to setup stuff on your own, but you really need a swap partition too.

---

### Post by stealthsniper96 on 2007-11-03
ok, so if i use BC, will ubuntu see that and use just that partition. right now im just tryin to figure out how to get it done w/o messing up anything on my mac partition.

---

### Post by cyberdork33 on 2007-11-03
> **stealthsniper96 said:**
> ok, so if i use BC, will ubuntu see that and use just that partition. right now im just tryin to figure out how to get it done w/o messing up anything on my mac partition.

Use bootcamp to make a partition that is the size you want to have for Ubutnu + 1 GB.

then in the ubuntu live cd, go to System > Administration > Partition Editor

A graphical presentation of the partitions on your hard drive will be shown. You should see a small ~200 MB FAT32 partition at the beginning (This is the EFI partition) and that will be followed by the Mac OSX partition (HFS+). Then you should see the larger FAT32 partition that you just made with bootcamp. click on it and press the delete key. It will now show an empty space. But you still have to click Apply. 

gParted (the application you are using) will 'delete' the windows bootcamp partition you made and leave only non partitioned space. Close gparted after it finishes it's task and start the installer. When you get to the point where you need to select the partitioning (guided, manual, etc) select the use free space option.

---

### Post by stealthsniper96 on 2007-11-03
> **cyberdork33 said:**
> gParted (the application you are using) will 'delete' the windows bootcamp partition you made and leave only non partitioned space. Close gparted after it finishes it's task and start the installer. When you get to the point where you need to select the partitioning (guided, manual, etc) select the use free space option.


that seems easy enough. thanks. but just to double check, that wont mess up my mac partition at all will it?

---

### Post by cyberdork33 on 2007-11-03
> **stealthsniper96 said:**
> that seems easy enough. thanks. but just to double check, that wont mess up my mac partition at all will it?

not unless you select the mac partition and do something to it.

---

### Post by stealthsniper96 on 2007-11-03
problem. ive tried using BC twice now and i get this error message twice. 
[IMG]http://i182.photobucket.com/albums/x269/stealthsniper96/Picture1-4.png[/IMG]

any ideas besides doing what it says?

---

### Post by cyberdork33 on 2007-11-03
did you turn journaling off for any reason?

What is the output of 'diskutil list' in OSX?

---

### Post by stealthsniper96 on 2007-11-03
> **cyberdork33 said:**
> did you turn journaling off for any reason?

not that i know of.

> **cyberdork33 said:**
>  What is the output of 'diskutil list' in OSX?   

/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *74.5 GB  disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       74.1 GB   disk0s2

---

### Post by cyberdork33 on 2007-11-04
Well, that all looks good. A fresh Mac Hard drive. I don't know why you are getting that error. There is another way to resize your partition, but I would trust it since you have some other type of issue it appears. I think the best course of action would be to do what it says unfortunately.

I found some information on the error.
[http://forums.macrumors.com/archive/index.php/t-191729.html](http://forums.macrumors.com/archive/index.php/t-191729.html)

Seems that you might be trying to use too much space.

---

### Post by stealthsniper96 on 2007-11-04
> **cyberdork33 said:**
> Seems that you might be trying to use too much space.

nope that wasnt it. o well, ill just wait till i get leopard and my new hd and try it then

---

### Post by cyberdork33 on 2007-11-04
> **stealthsniper96 said:**
> nope that wasnt it. o well, ill just wait till i get leopard and my new hd and try it then
Well, good luck. Sorry I could not give you any better help.

---

### Post by stealthsniper96 on 2007-11-04
> **cyberdork33 said:**
> Sorry I could not give you any better help.

no problems. :)

---

