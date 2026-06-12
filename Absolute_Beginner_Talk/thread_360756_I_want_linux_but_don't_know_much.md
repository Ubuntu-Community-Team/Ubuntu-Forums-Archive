---
title: "I want linux but don't know much"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-02-13
I guess this Absolute Beginner should be the place for me. 

I've been reading up on digg and saw a lot about ubuntu and never heard of it. I found out that it's linux. Vista came out, it has DRM, I hate it and soaks up way too much RAM for what I want to use it for. Especially when I saw Beryl with unbuntu and I decided I had to have it. I heard that ubuntu is easy to install but I don't know how about doing it or which hard drive. Here's my situation/set up:

3 hard drives: C is a 40gb with 6.6gb free NTFS file type. D is another 40gb with 5.81gb free Fat32 File type. E is a 150/160fb hard drive (i guess 10gb is partitioned) with 90gb free.

C contains my windows install and basic programs: firefox, instant messengers, and other generic applications and some games.

D contains a little more than half of music (mp3's) and all my downloads and drivers for the applications for the C drive. 

E contains some games (that mostly don't work - torrented) and all my videos.

I don't know what system file types are supported by Linux so I don't know which hard drive I should put it on. I was thinking about E just because it's big but I heard linux doesn't have ntfs support, i may have misread something though. Secondly, I can't lose hardly any functionality by switching to Linux. This means I must be able to do the things I do most with my computer, which should be easy because of open office and gimp. I must be able to use my D drive to read all the mp3's and hopefully m4a's and AAC's. If not the m4a's and aac's, i should be fine. I also need to use a torrent client with linux preferably Azureus. Games to me arent' that important to me so I was going to run a dual boot for games until I get independent from Windows. Another problem that rises is movies and windows media video and quicktime. I heard that you can't get it so how so you watch the videos on the internet and other movies I may have? All these codecs I have to get kinda scares me.

I'm sorry for the long winded post but I just don't know any better.

---

### Post by lamalex on 2007-02-13
Put it onto your E with the 90gb free. You dont need all 90 gigs but ubuntu will let you partition  it when you install it. Ubuntu 'does not' have NTFS support fully but there are some things you can do to get it to work, but you'll want to use the ext3 file system when you install it. The install is very simple and yes you will be able to play your mp3s, AACs, and every other audio format you could ever want. Azereus works with ubuntu, it's what I use and is really easy to install. Video isn't as scary as it sounds and when Feisty (the next ubuntu release in april) is fully released it'll be easy to get new codecs. Best thing to do >> download the iso and try it! WHen you burn boot to the iso it boots to a "live version," so you can play with it without installing. If you decide to install it, and something doesn't work, post on the forums. There is always someone who can help. Linux and ubuntu are great things. Definitely try it, I did, and I love it.

---

### Post by Bachstelze on 2007-02-13
When you say you have 90 GB free space on your third drive, it it _really_ free space (i.e. not allocate dto any partition) or free space on a partition ? In the first case, installing Ubuntu will be a breeze, you'll just need to launch the installer, create Linux partitions for Ubuntu in the free space, let the installer run and you're done. In the second cas, it will also be a breeze, you'll just need to resize the existing partition beforehand.

For your other questions, Ubuntu can very well read mp3's but I don't know about the others. Since your seocnd drive is formatted as FAT32, you'll be able to read and write to it from Ubuntu without any problems. For torrents, Azureus is available for Linux too, but it is IMO very bat, there are much better torrent clients out there. Finalyy, for Windows Media and QuickTime files, they may or may not work and it's very difficult to find out why since these are closed formats.

Hope that helps :)

---

### Post by Yellowbelly on 2007-02-13
Yes that helps out a bunch, thanks. Yes my third drive is all free space to use, but what do you suggest I set the partition at and can it be changed later if I want more space?

---

### Post by annda on 2007-02-13
if you have 90 GB free and unpartitioned, i would suggest using 40-50 GB for ubuntu, and maybe partitioning the rest as a sort of data-exchange partition - either as fat32 or ext3 (there is a very good open source driver for windows, you can find it here).

and yes, it's possible to resize the partitions later.

---

### Post by Yellowbelly on 2007-02-13
> **Iamalex said:**
> Put it onto your E with the 90gb free. You dont need all 90 gigs but ubuntu will let you partition  it when you install it. Ubuntu 'does not' have NTFS support fully but there are some things you can do to get it to work, but you'll want to use the ext3 file system when you install it. The install is very simple and yes you will be able to play your mp3s, AACs, and every other audio format you could ever want. Azereus works with ubuntu, it's what I use and is really easy to install. Video isn't as scary as it sounds and when Feisty (the next ubuntu release in april) is fully released it'll be easy to get new codecs. Best thing to do >> download the iso and try it! WHen you burn boot to the iso it boots to a "live version," so you can play with it without installing. If you decide to install it, and something doesn't work, post on the forums. There is always someone who can help. Linux and ubuntu are great things. Definitely try it, I did, and I love it.


Ok I'm a newb at booting live cd's too apparently. I downloaded and burned the ISO on a disk using Alcohol 120% but I can't get my comp to read the disk, it just goes straight to windows. I went into my bios I tried to move the cd drive up on the priority read list but I don't think it worked. I saw a setting for a boot OS/2 which I guess is second Operating system or something. It was disabled. Should I enable it or am I or did I do something wrong?

---

### Post by freebeer on 2007-02-13
Did you burn the image as an ISO?  It's a special setting in the burner software.  That's the most common cause.

Double check your bios to make sure that your first boot device is the CD-ROM.  Make sure you save the changes.

Ignore the OS/2 setting.  Leave it as it is.  FYI, OS/2 is the name of a particular operating system promoted by IBM which had a certain following in the late '80s and early 90's.

---

### Post by ramjet_1953 on 2007-02-13
Did you burn it as an iso image, or just make a data CD?

It MUST be burnt as an iso image.

Regards,
Roger :cool:

---

### Post by Yellowbelly on 2007-02-14
Hi. I'm posting this in Ubuntu. I like it. Yeah I got it to work. Changing the drive order was the trick. Thanks everyone. I'll try this for some time and then install it. What do you recommend for acquiring all the codecs and how do I set up a partition?

---

### Post by kittyhawk63 on 2007-02-14
Yellybelly,
If you don't get a lot of replies, come back tomorrow when more people are online. More than half of America is asleep. I wish I could answer your questions. I know that I partitioned when I installed my CD Live disk. It gave me this option. Good luck in resolving your issue.

---

### Post by ramjet_1953 on 2007-02-14
If you use the liveCD, it has the option to either use all of the drive, or to partition it the way that you want. Just follow the prompts. Just the same, always back-up before changing partitions. Just as important is that if you are re-sizing an existing Windows partition, you MUST defragment it first. You have been warned.

For all of the codec and fun stuff, just dowload Automatix2. It is the best way to get all of the goodies painlessly.

Regards,
Roger :cool:

---

### Post by Yellowbelly on 2007-02-14
So I have to defrag my 160gig HD to partition it and put Ubuntu on it, correct? And are you saying back up windows before doing all this, I don't really know how to do that. Also, I noticed that OpenOffice word doesn't have the font Times New Roman which is required in most university classes. Is the default one just a renamed version (because it looks a little different;maybe it could pass) or can I download the actual font?

---

### Post by Maestro23 on 2007-02-14
> **Yellowbelly said:**
> So I have to defrag my 160gig HD to partition it and put Ubuntu on it, correct? And are you saying back up windows before doing all this, I don't really know how to do that. [COLOR="Red"]Also, I noticed that OpenOffice word doesn't have the font Times New Roman which is required in most university classes. Is the default one just a renamed version (because it looks a little different;maybe it could pass) or can I download the actual font?[/COLOR]

You can install the MS TrueType fonts for OpenOffice to use.

---

### Post by Yellowbelly on 2007-02-15
ok I just defraged my E big drive which ubuntu is going on. I think i'm ready for install but just in case I forgot anything, is there anything else I need to do or am I good to go?

ps. and just in case this doesn't work out, it is reversible right?

---

### Post by Yellowbelly on 2007-02-15
ok i just tried to install and everythings fine till I get to partition. I can only use 58 gb mininum when I only want to use about 40-50. I think it wants to overwrite my current harddrive so how do I use the gpartition thing correctly?

---

### Post by ndefontenay on 2007-02-15
Hi.

I would suggest 2 things to get your codecs:

1) Get Automatix2. It's an installer with a repository of lots of applications. Including googleearth, and codecs to read avi files and stuff like that.

2) Read this thread. It might help:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck with your codec installation. It's not hard.

---

### Post by Yellowbelly on 2007-02-15
thanks I got that but does anyone know how to partition my harddrive that won't erase it?

---

