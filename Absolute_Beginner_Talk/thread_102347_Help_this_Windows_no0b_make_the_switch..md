---
title: "Help this Windows no0b make the switch."
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Pod_Man on 2005-12-11
Hey folks, its my first post here at ubuntu forums. So heres the twisted path that led me to this point...
About two years ago I was mad because my dad wouldnt buy a new computer, so i started earning money to buy my own. This let to me consulting the technology guy where my mom works, who informed me that some people acutually build their own computers...i was instantly intrigued. i had been building legos and other things all my life, so it was a natural fit. i began buying parts, but with little or no income it took me a while. about a year ago i was up and running on my own homebuilt pc and i was in heaven. i cruised along for another 10 months till i found a website called [www.pimprig.com]("http://www.pimprig.com") It is a great hardware review site with an even greater community. if any of you guys are hardware nuts like me, check it out and tell 'um Pod_Man sent you. but anyway...when i started to delve even deeper into computers, i really began to use mine all the time. i installed new programs, tweeked and overclocked to my hearts content. it was thursday of last week when i was going to do my semi annual windows reformat, just to keep my installation clean. Long story short, i got so fed up with windows that i vowed that i would find something better. i hit up my dads computer and headed over to pimprig and asked which linux distro would be best for a begginer, and ubuntu was the overwhelming choice. so i downloaded the iso, burned the image, and here i am. so now that thats over, i have some burning questions...
1. i have 30 gb of mp3s stranded on an nfts (?) hard drive, although it has no installation of windows on it. i want it back. soon.
2. i spent $220 on two western digital raptor hdds to put them in raid, and i intend to get my moneys worth. i have a cheapy raid card with the standard silicon image chipset. how do i set up the raid so i can actuall put ubuntu on the raid drives? where in the setup can i install my raid drivers? is this possible?
3. i use two crts in a dual head set up. right now they are mirroring each other, i want to extend my destop over both, like i had in windows. how would i go about doing that? (note: one thing i have done is enabled the universe, is there an app that would do it?)
I think thats all the questions i have for now, but im sure there will be others. any help here would be greatly appriciated. So far im lovin linux and i really dont want to go back to windows, so help me make the switch! :D

---

### Post by matthewv on 2005-12-11
So you have installed ubuntu already, or you are going too??? Regards to question 1, see [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions) . You can just copy them over. The other two are possible, but you'll have to get somebody else to help there,, i wouldn't know (never done it)

---

### Post by Pod_Man on 2005-12-11
yes, i have installed ubuntu. Thanks for the help with 1, but it didnt work. i followed the instructions, changed the command to mount to have an accurate device name (sda as opposed to hda) but it says "cant mount drive, device already mounted or media/windows busy" anybody else help me out? oh if you have google talk im [email]andrew.zager@gmail.com[/email] if somebody wants to walk me through this...

---

### Post by yapsuper on 2005-12-11
In terms of 1, here's what I think. I would place your files on a windows computer for a short time. Then format your disk to fat32, this way both windows and linux can read the disk.

---

### Post by Pod_Man on 2005-12-11
windows does not format fat32, at least on a drive big enough to hold my mp3s

---

### Post by TeeAhr1 on 2005-12-12
[QUOTE=Pod_Man]windows does not format fat32, at least on a drive big enough to hold my mp3s[/QUOTE]
If I recall correctly, you can use the install CD as a standalone partitioning tool *(but read the disclaimer at the bottom!)*  Use the XP defragger first, always a good idea when you're partitioning.  Determine how much "shared data" space is going to be required, restart, and boot the Ubuntu installation CD.  Go through the steps, resize your NTSF partition and use that free space to make a new FAT32 partition.  When you're finished partitioning back all the way out of the installer **(DO NOT JUST RESTART)**.

This is just the general rundown, if you want a more thorough explanation, [here]("http://users.bigpond.net.au/hermanzone/") is a complete walkthrough.  It goes all the way through the installation, but you can simply follow the steps to the end of the partitioning process then back all the way out, and reboot to Grub.

**Important:** I think this is accurate, but have not done it myself!  Can someone else please confirm that this okay and will not harm your system?

---

### Post by matthewv on 2005-12-12
Easiest way to partition is to use gparted from the ubuntu live cd... but i wonder why your drive won't mount... sda is usually scsi drives or usb drives, ide hard drives will use hda, or hdb, etc..

---

### Post by carlosqueso on 2005-12-12
[QUOTE=Pod_Man]yes, i have installed ubuntu. Thanks for the help with 1, but it didnt work. i followed the instructions, changed the command to mount to have an accurate device name (sda as opposed to hda) but it says "cant mount drive, device already mounted or media/windows busy" anybody else help me out? oh if you have google talk im [email]andrew.zager@gmail.com[/email] if somebody wants to walk me through this...[/QUOTE]


Can you post your /etc/fstab here?  Just type 

```
sudo gedit /etc/fstab
``` in a terminal.  I had a similar problem, and it was because the drive was mounted in the wrong place (highly annoying, but more my fault than anything else ;-))

---

### Post by Pod_Man on 2005-12-12
alright. i think i have this mp3 thing figured out. im just gonna install windows on a spare drive i have around here, then borrow my friends external drive which is 80Gb with a FAT32 filesystem. i'll transfer the files over to the external drive and then plug back into ubuntu. (Im almost postive it reads FAT32 right?) so now that that should work...the other problems...just a refresher...
1. want to install ubuntu to a raid0 set up, wont let me. i go into my RAID bios and create a striped set, but the ubuntu partitioner sees it as two separate drives still. suggestions?
2. dual display set up. how do i extend my desktop across both screens/ make it do something besides mirror each other?

---

### Post by Nequeo on 2005-12-12
Pod_Man: Dual monitor set up is dead simple if you have an Nvidia based graphics card with two video outputs. E.g. one analogue and one DVI with an analogue adapter. 

Do you?

If you do, I can help you. I'm running Ubuntu at work across two 17" LCD flatscreens mounted on an adjustable pole. And I couldn't live without it. 

If you've got something else, I can't really help you, as I've only set up dual-screen using Nvidia cards. But Google certainly can!

Cheers,

---

### Post by Pod_Man on 2005-12-13
ive got a radeon 9600XT with a dual head set up, one analog and one digital to analog adaptor. and can sombody help me on the raid issue? i dont want to keep ubuntu installed on this particular disc for long, i want it on the raid set up, so im hesitant to invest anytime customizing this install to fit my needs when im just going to set up a new one.

---

### Post by Pod_Man on 2005-12-13
::Bump::
I'd like to get this RAID thing figured out sooner than later if possible...

---

### Post by bonzodog on 2005-12-13
what kind of Raid?
Ubuntu does raid 1 and 5 with no problems using software emulation. Raid 0 *is* possible but very difficult, and blew my mind and i've been in linux since 1994.
Raid 5 striping is possible, you can set it up in the partitioning tool, though I have never done it myself...

---

### Post by kalos on 2005-12-13
For RAID try this [howto](https://wiki.ubuntu.com/FakeRaidHowto)

Otherwise, I'd love to help with your RAID problem, but I don't think we have enough info. 

So you want a RAID 0 array (multiple drives appear as one)
I'm guessing that Raptor HDDs are SATA. You have a "standard silicon image chipset". What model? [Silicon Image](http://www.siliconimage.com/) lists several SATA controllers. Can you get the model code (SiI 3xxx)? You might see it when you computer starts up.

That should be enough to start, but you can also check out this [google search](http://www.google.com/search?hl=en&q=%22silicon%20image%22%20ubuntu%20raid&btnG=Google+Search) for some answers.

---

### Post by Pod_Man on 2005-12-13
Alright...as far as the RAID goes...yes, im after raid 0. the hdds are sata, and the chipset is silicon image 3112a chipset. the drivers come on a mini cd and i assume id neet to make a floppy to get them installed during set up.

---

### Post by Pod_Man on 2005-12-13
Alright, still looking for a raid solution, but also i have another question. with my creative soudcard i used the cmss technology to play my mp3s over all 5.1 channels, but that doesnt work now. any way to acheive a 2.1 to 5.1 upmix?

::EDIT:: So when i read this thread, i realize i really need some one on one support for fixing all this. do one of you experts out there have google talk? im [email]andrew.zager@gmail.com[/email], please look me up to work through these issures. you dont have to know how to do all of them, any help would be much appreciated

---

### Post by jhnphm on 2005-12-14
RAID0 does not provide any appreciable performance gain unless you do heavy video, and there are data integrity risks. 
[http://www.anandtech.com/storage/showdoc.aspx?i=2101](http://www.anandtech.com/storage/showdoc.aspx?i=2101)
Don't know about sound.

---

### Post by Pod_Man on 2005-12-14
Okay, ive given up on the raid...not worth the slight performance gain. now...i successfully got my music on a FAT32 disk so that all works now :D  the only problem from the first post is the dual head. i have read several how tos (from this site and others) but theres always a part when i get lost and dont know how to do it. again, anybody with googletalk should feel welcome to hit me up to help me get this set up (andrew.zager@gmail.com) info about dual screen...radeon 9600XT, dual head, two identical crts.

---

### Post by jimrz on 2005-12-14
hi there...

did you unmount your ntfs drive before you tried to mount it with a valid name? If not, that is why it did not work. This also applies to getting a FAT 32 win drive to where you can write / save to it.

If that is the problem, do this in Terminal:

Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows
then type:
sudo umount /media/<whatever it is calling your ntfs drive>
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

in gedit change the line for your ntfs drive to read:
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

save, then to re-mount the drive without re-booting type:
sudo mount /media/windows.

This worked for me a little bit back when I had the same issue.

---

### Post by Pod_Man on 2005-12-15
Just a little bump...
so now the only real problem im having with ubuntu is the dual display thing. like i said before, ive looked at several how-to's but i havent been able to make any work. so...Radeon 9600XT, dual crts, desktop spanning. any help?

---

