---
title: "lucid - how to access OS X partition?"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by rabidcentipede on 2010-05-04
Okay, so I have installed 10.04 on my MacBook Pro 6,2, and am trying to access some files stored in my User directory on the OS X partition of the laptop. I get a permission-denied error, but I figured this was a similar issue to the one mentioned in the stickied "How to Install Ubuntu 9.04 on Intel-Based Macs" thread.

However, the suggest fix,
```
sudo usermod -u 501 -g 20 richard
```doesn't exactly work for me. I tried this, but found myself suddenly logged out of my main account. On the log-in screen, only my second account showed up. Luckily, I was able to log into that, and re-usermod my main account back to it's original userid number.

I am guessing that my strange error had to do with the abnormal (for ubuntu, at least) userid?

How else can I get around the fact that OS X protects the User directories of its users? I want to be able to access my files!

Thanks for the help, sorry if this is a noob question.

---

### Post by linuxopjemac on 2010-05-05
[http://www.australianguy.com/2010/05/change-ubuntu-uid-to-501-for-os-x-file-access-simplified/](http://www.australianguy.com/2010/05/change-ubuntu-uid-to-501-for-os-x-file-access-simplified/)

---

### Post by rabidcentipede on 2010-05-05
> [http://www.australianguy.com/2010/05/change-ubuntu-uid-to-501-for-os-x-file-access-simplified/](http://www.australianguy.com/2010/05/change-ubuntu-uid-to-501-for-os-x-file-access-simplified/)


this **does not work** on 10.04. As I said in my original post, when I changed the userid to 501, the account ceased to show up on the log-in menu. 

Does ubuntu have some setting somewhere that determines which uid's are "accounts" that people can log in to? Would it be possible to add 501 to that list?

---

### Post by paulinchen on 2010-05-05
Thats what is written is in linuxobjemacs link.
 You have to lower the UID and the GID_MIN. Thats exactly what I've done on my mbp 5.5 and it works for me. I changed the GID of the dailout group from 20 to 99 and than changed the user-group to staff and set the ID to 20.
I think you should have the same username on both systems as well.
Ah ... and  everywhere in the mac.linux.be instructions you have to change the GID from 501 to 20 ...
maybe you would like to automount the partition? Put something like that in the /etc/fstab

/dev/sda2    /media (or mnt)/mac    hfsplus auto,user,rw    0    0

I think for the drive being writable it has to be a non Journaled hfs+

But by the way, if you just want  access to a few files, its easier just to open the folder as root....

---

### Post by rabidcentipede on 2010-05-05
Ahh sorry, I see the problem now. I hadn't changed the GID to 20, and was getting some strange problems.

Thanks everyone for the help! Sorry for the trouble!

---

### Post by paulinchen on 2010-05-06
You're welcome. I had exactly the same issue, first time tried to make this two systems become more or less one, so I'm glad to share my experiences, so make other ones life easier...

If you ever have another question, feel free to ask, you're talking to a pro in dualboot ;)

---

### Post by rabidcentipede on 2010-05-07
Okay, I've done some reading about r/w capabilities in HFS+ journaled filesystem - apparently reading is fine, but writing doesn't work because of the journaling.

What would be your best suggestion to get around this? I'm probably going to have some sort of shared storage that they can both read/write to, but there are still some times when it'd be really convenient to just be able to write from ubuntu to the os x partition.

Apparently it's possible to disable the journaling in OS X through the disk utility, but I've heard that this may be a bad idea. What are the major downsides to it?

---

### Post by paulinchen on 2010-05-08
Thats what I did:

-split my hfs+ Macintosh HD partition into two
- made the second one non-journaled
- copy (NOT move) the entire OSX homefolder to this second partition
- set the home directory for the user to the new partitions home
- reboot to ubuntu
- change the directories of /Downloads/Documents/Music/Video ... to the one on the osx home ( you can do this easy via ubuntutweak)
- make the /etc/fstab entry for the new partition (I prefer /mnt cause you than will not see the partition as an other drive)
- reboot to ubuntu and to osx
- if everything works you can delete the old osx home, which should now look like a normal folder instead of the home icon

This would make it very comfortable switching between the two systems, cause everything is all the time in its right place.
Maybe you would like to install weave sync addon for firefox, to keep your browser synced between both

---

### Post by untmdsprt on 2010-05-09
> **paulinchen said:**
> Thats what I did:

-split my hfs+ Macintosh HD partition into two
- made the second one non-journaled
- copy (NOT move) the entire OSX homefolder to this second partition
- set the home directory for the user to the new partitions home
- reboot to ubuntu
- change the directories of /Downloads/Documents/Music/Video ... to the one on the osx home ( you can do this easy via ubuntutweak)
- make the /etc/fstab entry for the new partition (I prefer /mnt cause you than will not see the partition as an other drive)
- reboot to ubuntu and to osx
- if everything works you can delete the old osx home, which should now look like a normal folder instead of the home icon

Hello, could you expand on these instructions so that other newbies know what you're talking about? Also what size partition can you safely make for OS X and Ubuntu since all user files will be put on a 2nd partition? I'm assuming that the system file, and all applications will be put on one partition, so it shouldn't take that much space.

My Macbook has a 120GB drive, and I'd like to split it into 20GB Mac, 20GB Ubuntu, and then 80GB for my files. Is this feasible or should I adjust the amounts so the Mac and Ubuntu can comfortably run?

FYI, for the Mac side, I mainly use my TV tuner, iTunes, iCal, Openoffice and it seems to have better support for Japanese input.

For the Ubuntu side I plan to install the "Studio" version with all apps that come with it. For future reference, if Ubuntu suits my needs on my Macbook, I may decide to build a PC and put Ubuntu as the only OS on it.

Thanks!

---

### Post by paulinchen on 2010-05-10
there are many threads in this forum who describe this process really good so you can follow them step by step. So I don't think there is a need in post it another time.
If you're think I'm wrong or you need help with a special part I'm here to help.

So let's come to one of those special parts:
You don't have completely the same home partition in OSX and Ubuntu, means that your config files (means every directory/file with a dot in front, thats in your home directory in ubuntu) need to be stored on an ext partition.
For me the conclusion was to made 4 partitions. First one with the OSX System, that should be between 20 and 30 Gb and hfs+ journaled. Another hfs+ partition for sharing the home directories (unjournaled and with the most space on your drive)
Third an ext4 partition 20gb for the ubuntu system, and at least a partition of your home directory (ext4, should be about 30gb)

This all depends as a matter of fact on your personal usage of the two operating systems, but in your case it should be something like 20/50/20/30gb.
As I said its just a estimation, but shouldn't be a problem to change the partitions afterwards with gparted or the parted magic live-cd if you're just running out of space somewhere.

---

### Post by untmdsprt on 2010-05-11
Actually I'd say give more than 20GB to the OS X boot partition. 30 - 40GB should be a safer amount for whatever applications a person may need. As soon as I back up everything, empty the trash, etc. I will probably use Gparted to adjust the partitions.

It would be nice if Ubuntu would install on an external drive so all this wouldn't have to be done.

---

### Post by Zookalicious on 2010-05-11
> **rabidcentipede said:**
> Ahh sorry, I see the problem now. I hadn't changed the GID to 20, and was getting some strange problems.

Thanks everyone for the help! Sorry for the trouble!

Could someone please explain how to do this? I'm currently following the guide at [http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95) but am not sure what I need to change so that it will work on 10.04

Any help is greatly appreciated!

---

### Post by DagMan on 2010-05-28
> **paulinchen said:**
> Thats what is written is in linuxobjemacs link.
 You have to lower the UID and the GID_MIN. Thats exactly what I've done on my mbp 5.5 and it works for me. I changed the GID of the dailout group from 20 to 99<snip>
There is of course the link in the bottom of linuxobjemacs's site that references the original source, which he plajorized word for word rather than using it under a "Fair Use" condition that would have been acceptable.
Getting away from that slightly, I've updated my page based upon the pointing out the need to change the dialout group ID. Thanks.  It's solved an annoying issue for me.

---

### Post by linuxopjemac on 2010-05-29
I think that it's much easier to find info on the web, when it's concentrated on one spot. I try to collect all such data form people's blogs. I always make a reference to the original article, to honor those who wrote it.

---

### Post by DagMan on 2010-05-29
You can't copy and paste an entire article.  Its not lawful.  If you link to it and that's it, that's fine.  If you take a peice of it, provide a link, and then add something, then that's fine.  If you GET PERMISSION then that's fine.

Its irritating that you'd try to justify it since I haven't even asked you to take it down, but if you want to make an issue with me, I can force you to.  Depending upon the country you live in, it may be as simple as contacting your webhost.  
If it was as simple as what you say then I'd just rip off your site, this site, and that site over there. You've already almost entirely ripped off from other people, so why shouldn't I do it too?  Because its theft and its illegal.  Would you like to contribute money to my web hosting and registration expenses?  Thought not.

Almost everything on your site that I highlighted and hit "search google for" brought me back to ubuntuforums.org, for instance.  I have no idea what the policy is at this site, but the policy of my site is that I put work... unique work, into what I publish, and that while I enjoy it, I have to justify the cost of domain registration and webspace.  I also have to be accountable if someone slaps me with legal consequences.  
Are you sure you really want to continue the attempt at justifying it when I'm not even asking you to remove it?  While you think you're being generous by putting things in one spot, you're not.  You're stealing and I'm being generous by throwing up my hand and saying "oh well, do I want to bother?".

I dare you to take issue, now, though, because I will bother for principles sakes.
You've been a copy and paste plagiarizer.  That's the bottom line.  Don't argue with it or there will be consequences.  Also, next time you'll need to ask for permission if you intend to use my content in such a manner.  I noticed just now that you've already updated your article ripping off the changes I made less than a day ago, and even managed to change irrelevant details that I threw in, like changing the name "John" to "Jacob".  Another copy and paste.  When can I expect payment toward the expenses involved with my site?

---

### Post by Sef on 2010-05-29
1. Locked this thread as the OP's problem has been solved.

2. Changed disputed link to original source as the original is not under a creative commons license.

---

