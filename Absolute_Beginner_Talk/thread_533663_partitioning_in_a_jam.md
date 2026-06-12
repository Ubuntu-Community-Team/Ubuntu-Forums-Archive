---
title: "partitioning: in a jam"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by c3genesis on 2007-08-24
okay.  i got some help getting the text boot of ubuntu going and now im going through the boot menus choose language configure keyboard, detect and mount cdrom, load debconf preconfig file, load installer components from cd, detect network hardware, configure the network, detect disks, partition disks;  up to this point i have had only two issues, first of all, configuring the network with dhcp fails, i went to do it manually but i dont know my ip address, can someone tell me how to find this?  Second of all when I get to partitioning my disks, im confused.  I partitioned my hard drive(200gb) into two partitions so that i can still use vista but aparently I didnt format the unoccupied volume.  So a dual boot is a little much to ask for right now, i guess ill have to settle for just getting ubuntu in there and ill try to add vista back later.  but i cant even do that.  not sure that i cant, but im not sure how to.  ive tried every option and each time i get the same response when i go to finish partitioning;  input/output error during read on /dev/sda
ERROR!!!
there are options retry ignore and cancel, after hitting any of these, i get repeats of the same thing followed soon after by a new error saying creation of swap space in partition #5 of scsi1 (0,0,0) (sda) failed.
I have no idea what im doing, i hope someone can help me, i would be eternally grateful.

---

### Post by tszanon on 2007-08-24
> **c3genesis said:**
> configuring the network with dhcp fails, i went to do it manually but i dont know my ip address, can someone tell me how to find this?
Are you using dial-up connection or broadband connection? If it's dial-up, I don't know how to fix it. :(

> **c3genesis said:**
> Second of all when I get to partitioning my disks, im confused.  I partitioned my hard drive(200gb) into two partitions so that i can still use vista but aparently I didnt format the unoccupied volume.  So a dual boot is a little much to ask for right now, i guess ill have to settle for just getting ubuntu in there and ill try to add vista back later.  but i cant even do that.  not sure that i cant, but im not sure how to.  ive tried every option and each time i get the same response when i go to finish partitioning;  input/output error during read on /dev/sda
ERROR!!!
there are options retry ignore and cancel, after hitting any of these, i get repeats of the same thing followed soon after by a new error saying creation of swap space in partition #5 of scsi1 (0,0,0) (sda) failed.
I have no idea what im doing, i hope someone can help me, i would be eternally grateful.
Since the partitioner is trying to create the desired partitions, I think you have done things right. But, since it fails with an error message like that, I think the hard disk may be dying, or the cable connections inside the computer may be loose. Did it work fine under Vista?

---

### Post by c3genesis on 2007-08-24
Yes, partitioning seems to work fine on vista. Im aborted my boot from the live CD and im formatting the free volume with vista. Hopefully that Will solve the problem
Thanks!

---

### Post by c3genesis on 2007-08-24
I have a cable connection(comcast) but i connect wireless

---

### Post by c3genesis on 2007-08-24
Im not sure what else i can do. When ubuntu failed to partition the hard drive i went and did it myself on vista. I put vista un the last available part. I creatèd and formatted a linux ext 3 in the primary slot about 100gb and a linux swap part. In the following slot. The whole thing was successful. I checked it all out then i restarted the còmputer with the text boot live CD and it doesnt recognize the partitions ive created. It still shows only my 200gb toshiba hd. Am i doing something wrong or have i just got the worst luck ever?

---

### Post by c3genesis on 2007-08-24
I meant to mention that the swap space ive creatèd ús 8gb, also i used partition commander to do my parting. Hope this helps. And thanks un advançe for any help at all.

---

### Post by gn2 on 2007-08-24
> **c3genesis said:**
>  i connect wireless

This will probably be why network set-up is failing. 
It is likely that you will have to install a driver for the wireless after installing.

---

### Post by gn2 on 2007-08-24
> **c3genesis said:**
> I meant to mention that the swap space ive creatèd ús 8gb, 

Unlikely it will need to be bigger than 1gb

> **c3genesis said:**
> also i used partition commander to do my parting.

My advice for creating dual-boot systems is to use a partitioning utility to create free space then use the distros own installation partitioning tool to create the necessary partitions in the free space.

I usually use 1gb swap, 7-10gb / , and have a /home partition of whatever size is required/available.

---

### Post by c3genesis on 2007-08-24
Thanks for the advice but the reason i used part commander is bc the distros partitioner wont work. Plus it isnt showing the vista info. So if it was working all i could do is overwrite vista right. Anyways, i still dont know how i can fix the problem with the distros partitioner. Thats the most important problem. Does anyone have any advice they can give me?

---

### Post by gn2 on 2007-08-24
What I mean by free space is unallocated space on the hard drive, not empty unused space within a partition.
.
Use your MS partitioning utility to shrink a partition to leave a blank space on the hard drive.
.
Ubuntu will then be able to install into this blank unallocated space.

---

### Post by c3genesis on 2007-08-24
Okay, i tried your advice with the same results. Maybe im doing something wrong. Bear with me and ill explain exactly what i did.

First i usef ms part to límit the vista part to 60gb and positioned it at the end of the remaining 138.7gb unallocated space. Btw there is a 1.3gb cushion at the beginning of the hd. I assume its recovery but im not sure. It has no label. If i delete this is it posible that it could solve my problem?

After i created more unallocated space with the ms part i went to ubuntus partitioner. The options say guided partition & "scsi1(0,0,0)(sda) 200gb ata toshiba mk20356s"
Under guided part there is
  -use entire disk
  -use entire disk w lvm
  -manual(this just takes me back though)
The 1st option creates two parts 197.3 ext3 and 2.7 swap
The second option takes me straight to the error screen previously mentioned. But every option eventually gives me an error.
Under the hd selection it gives a warning: you have selected an entire device. If you proceed all part.s Will be removed. Create empty part.?
After doing this it gives me 200gb empty space. Where i can create my own ext3 and swap any size or auto partition which is the same as guided but now the space is empty. Everything gives me the same error. Am i doing something wrong? Ill do anything to get ubuntu installed. But it seems like ive tried all the available options. Am i missing something?
Thanks again for any help you can give.

---

### Post by tszanon on 2007-08-25
Ok, so now you have something like this:
1. a partition at the beginning of the disk, that probably is some recovery stuff;
2. it's followed by some unallocated space (disk space where there is no partitions);
3. Vista partition up to the end of the disk.

Now, you have to use the "manual" option, so you can create at least 2 partitions in that unallocated space:
1, EXT3 partition, where the whole Ubuntu system will reside;
2. an Swap partition, that ubuntu will use as swap space.

You will see, after selecting "manual", that the partitioner will show will all of the partitions and unallocated spaces (if I recall correctly, it calls unallocated space as "free"). All you have to do for each new partition is:
1. Select the free space and press enter;
2. create a new partition there. the partitioner asks you the size of the new partition, and the lets you alter some important details, like the filesystem (choose EXT3 for the system partition, choose swap for the other new partition);
3. You must inform the mounting point of the EXT3 partition: it is "/".
4. Besides the type of partition and mounting point (swap has no mounting point), just leave the other options in their default. Select finish.

After finishing, you will see that the new partitions will have the letter "F" next to them (which means that they will be Formatted) and the old partitions (recovery and vista) will have the letter "K" next to them, which means that they won't be formatted, they will be Kept as they are).

Finish partitioning. The partitioner now will show you what is going to be formatted and will ask for confirmation. If it seems to be fine for you (which means: if recovery and vista partitions are not listed), then go ahead.

That's it. :)

---

### Post by c3genesis on 2007-08-25
sorry, i know this is starting to become monotonous but im still getting the same error message(creation of swap space...failed)  i did it exactly as you said to.  I've been working on getting this installed for nearly a week and id be lying if i said i wasnt disappointed.  Is ubuntu worth this much trouble?

---

### Post by c3genesis on 2007-08-25
i deleted that small partition at the beginning of the hd btw didnt do any good.  a tech guy at work said as long as i have the recovery disk, i dont need recovery info in the computer, and it would be okay to delete.

---

### Post by c3genesis on 2007-08-25
ive tried the live cd as well hoping that i could use that instead, but i get an error message saying: failed to start the xserver. ive read many threads about this and most of the time, people are advised to use the command "sudo /etc/init.d/gdm stop"
then "sudo dpkg-reconfigure xserver-sorg"
then "sudo /etc/init.d/gdm start"
when i try the first command however, it says that the command is not recognized. am i mistyping something? have you heard of these commands? i have also been advised to use the second command by itself, but this doesnt help either. i go in and put in vesa or ati or nv, none of them work, then i put in 600x800, 1024x768 and 1280x800 for my screen resolutions and put everything in as default and when i go to restart the xserver it still gives the same error. Maybe someone can help me with this issue instead. ive also tried a command "sudo dpkg-reconfigure -phigh....." and this was also unsuccessful. i have an ati radeon x1200 graphics card, i think that is the issue, something to do with a driver.  i really dont know what else to do, can anyone give me a lead?

---

### Post by tszanon on 2007-08-25
About the partitioner issues: are you installing Dapper (6.06), Edgy (6.10), Feisty (7.04) or Gutsy (7.10, not yet released, shouldn't be used yet)? I'm willing to place here a step-by-step partitioning, if you think it may help. And please, are you using the desktop (live) cd (the one that gives you the graphical installer) or the Alternate CD (text-mode installation)?

About the xserver: are you installing Ubuntu or Kubuntu? gdm stands for Gnome Display Manager, which is used by Ubuntu. In Kubuntu, it should be kdm (that should stand for KDE Display Manager).
```
sudo /etc/init.d/gdm stop
```
This should work in Ubuntu. It stops the display manager.
```
sudo dpkg-reconfigure xserver-sorg
```
This is wrong. It's not sorg, it's xorg. So it should be:
```
sudo dpkg-reconfigure xserver-xorg
```
I don't know exactly what it does, but it reconfigures the xserver.
```
sudo /etc/init.d/gdm start
```
It starts the gdm. Now it should be using the new configuration made by the second statement.

About the ATI graphics card: I never used them, only NVidia. I've seen in the past people complaining about the bad support ATI gives to Linux. It seems that they didn't want to release a good driver for Linux, and didn't want to open-source it. But I don't know how the things are now, so don't take these words as the absolute truth. They are not.

---

### Post by pgar23 on 2007-08-25
start of fresh. Erase all the stuff that you have done thus far.
Satrt with only having Vista. Then restart the install of Ubuntu...
Watch the VIDEO TUTORIAL in my signature on dual booting...very helpful
Once you have Vista and once you start the Ubuntu installation you should only make the SWAP about 1 GB...MAX!
it doesnt need more than this.

---

### Post by pgar23 on 2007-08-25
...and about the ATI graphics card...I had the same type of problem...THERE IS A "STICKY" about installing Ubuntu with ATI cards...chekc it out...its at the top of the Absolute Beginners page under the sticky's there...If you cant find it I recommend using a magnifying glass or some glasses.**poor humor**

but I will be checking back to see how this goes...if you have any more questions just post and someone will answer.

GOOD LUCK

---

### Post by c3genesis on 2007-08-25
Thanks for your help. I was using the /etc/init.d/gdm command on kubuntu so let me try it on ubuntu.  Im using feisty and i have problems with partitioning on. The alternate CD and problems with the xserver on the live CD for both ubuntu and kubuntu. Explaining partitioning would bé a waste of your time though. Ive tried everything and i get the same error each time. Its got something to do with my còmputer. So let me try the etc command on ubuntu live CD when i get home and ill tell tou what happens. And i really do appreciate all the time youre sacrificing to help me.

---

### Post by c3genesis on 2007-08-25
Thanks for the reassurance. Thats really the only thing thats kept me going. Ive come close to quiting several times

---

### Post by pgar23 on 2007-08-25
Dont quit tho. If you quit, what will all this work have been for? Also, when I first installed Ubuntu I had numerous problems...1. Wireless didnt work 2. My network adapter driver wasnt very well supported with linux so I had to read this guys HOWTO and seek additional assistance....but to make a long story short, once I installed and ran Ubuntu I have been using it ever since and haven't reverted back to Windoze(except to watch the occasional movie that i dont want to use under Ubuntu)

---

### Post by c3genesis on 2007-08-25
I actually read that sticky already. I didnt realize it til i had read it again though. The steps didnt work for me the first time. I assume tou have to enter all those commands after youve made it to the gui desktop. I cant get that far. Not in the text mode install or the live CD. That sticky isnt cert detailed either. Maybe they can have someone add to it for noobs like me, lol.

---

### Post by c3genesis on 2007-08-25
I actually read that sticky already. I didnt realize it til i had read it again though. The steps didnt work for me the first time. I assume tou have to enter all those commands after youve made it to the gui desktop. I cant get that far. Not in the text mode install or the live CD. That sticky isnt cert detailed either. Maybe they can have someone add to it for noobs like me, lol.

---

### Post by pgar23 on 2007-08-25
do you have aim or msn? I need to ask you couple things.

---

### Post by c3genesis on 2007-08-26
Okay. I Will give you an example. My hard drive is already partitioned with 60 gigs belonging to vista which is positioned at the end of the hard drive with 140 gigs of unallocated space perceding it. So i go through the steps of setting up ubuntu, then i get to partitioning where i have the options pd guided partitioning, help on partitioning which is no help at all btw, then we have the hd listing for "scsi1 (0,0,0) (sda) - 200gb ATA toshiba mk2035gs" i click this and it warns me "you have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions Will be removed.

Note that you Will be able to undo this operation later if you wish.

Create new empty partition table on this device?"

I click yes where i am presented with the hd listing followed by pri/log 200gb free space.

I click the free space and am given a new window asking how to use the free space: create new part, auto part, or show cylinder/head/sector info. I select create new part, select 30gb, select primary(the other option is logical), select beginning for location(other option is end) it is already set on ext3 mounting at / so i hit done and set up my swap space following the same pattern free space, create part, 2gb, end(ive also tried it st the beginning and everywhere inbetween to change the part #) i enter logical for the type, this seems only to effect the part # but then again i cant see everything it effects can i, lol. Now i change it to use as swap area. Done. My hd listing now shows my hd followed by 
#1 primary 30gb f ext3.    /
#5 logical.   2.     f swap  swap 

now finish and write to disk. It gives me a warning that all previous parts Will be destroyed, i guy proceed. The error: input/output error during read on /dev/sda

ERROR!!!

Retry
Ignore
Cancel

After hitting retry several times i am still in the same spot and the results of cancel are obvious, so i guy ignore which takes me to a new error screen: failed to create swap space: the creation of swap space in part #5 pd scsi1 (0,0,0)(sda) failed.

Continue/go back.

Do you still think itll be easy to fix?

---

### Post by pgar23 on 2007-08-26
STILL AN EASY FIX.

> I select create new part, select 30gb, select primary(the other option is logical), select beginning for location(other option is end) it is already set on ext3 mounting at / so i hit done
Here is where you're going wrong. You will need to turn the "bootflag" ON...this can be done simply by going down to it and press enter...it will do its thing, flash the screen, and return you to the screen you were just seeing b4 you turned it on.

> and set up my swap space following the same pattern free space, create part, 2gb, end
First things first. You should only need about 1GB max for swap, but if you want more this is fine. Second, place the swap near beginning/where ever you put your EXT3 "/" partition. Thirdly, make it primary. This Swap partition will not need the boot flag part. You are correct in changing it to use as SWAP tho.

---

### Post by pgar23 on 2007-08-26
After doing all this...let me know the output.

---

### Post by c3genesis on 2007-08-26
Okay, shockingly enough, i kinda figured it out. I found a back door of sorts. I used a spare external harddrive i have and it worked. It showed the already formatted ntfs space unlike my internal drive, im wondering why though, the only difference is that my external has no os on it, its just used for storage. So does this mean i have a bad sector or a dying hard drive or something? What can cause formatted space from not showing up on the partitioner?

---

### Post by pgar23 on 2007-08-26
To fill in all the blankspace: We discovered that c3genesis had bad sectors in a numerous of places on the HDD. Also is receiving error: [B]"Creation of swap space.....failed" 

[/B]A thread about Bad Sectors: 
[http://ubuntuforums.org/showthread.php?t=462010](http://ubuntuforums.org/showthread.php?t=462010)


A thread about the error:
[http://ubuntuforums.org/showthread.php?t=486934](http://ubuntuforums.org/showthread.php?t=486934)

Hopefully they will help in some way.

report any progress/new results/bad news.

---

