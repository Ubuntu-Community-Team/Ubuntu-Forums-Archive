---
title: "best partition size"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by pohlipit on 2007-04-07
Hi Everyone,

after experiementing with Ubuntu on a 2nd hard drive on my T43 (actually I swapped the HD with my Windows one) I found it amazing. I now bought a new 120GB drive and would like to know your suggestions on the best GB size for the partitions. 
I want to install it this way:

1: Windows XP
2: ext3 partition for shared data
3: /home partition
4: Ubuntu (will go for feisty)
5: swap

Any recommendations what sizes I should allocate for the partitions.

Thanks,
  Pete

---

### Post by kvarley on 2007-04-07
All you would probably need is enough for each of the operating systems, I would recommend 20GB for Windows XP and 10GB for Ubuntu.

---

### Post by laidback on 2007-04-07
I haven't found that I need huge partitions, but I guess it depends on what you do.
My main extra use is for backup space, you shouldn't forget that, and on a different drive.
I run 6.06 happily on a 10Gb hdd with backup elsewhere.
Ubuntu uses a few Gb, say 4-5 with space to spare.
Swap is said to be best at approx half your ram with a max of 512.
If you leave space on your hdd that is unused you can always go bacl later with Gparted and alter the size allocated.

---

### Post by siciliancasanova on 2007-04-07
I have a 200gb harddrive and have it set up with 90gb for windows xp (web development) and 78gb for my ext3 (music and video and such with ubuntu) with 2gb for my swap (have 1gb ram)

---

### Post by pohlipit on 2007-04-07
> **siciliancasanova said:**
> I have a 200gb harddrive and have it set up with 90gb for windows xp (web development) and 78gb for my ext3 (music and video and such with ubuntu) with 2gb for my swap (have 1gb ram)
Hi Sicilian,

so you are using one partition for Ubuntu together with the data files? Or are you having one ext3 and another one for the OS?
Not sure what is better.

Cheers,
 P!

---

### Post by Hieronymus on 2007-04-07
> **pohlipit said:**
> Hi Everyone,

after experiementing with Ubuntu on a 2nd hard drive on my T43 (actually I swapped the HD with my Windows one) I found it amazing. I now bought a new 120GB drive and would like to know your suggestions on the best GB size for the partitions. 
I want to install it this way:

1: Windows XP
2: ext3 partition for shared data
3: /home partition
4: Ubuntu (will go for feisty)
5: swap

Any recommendations what sizes I should allocate for the partitions.

Thanks,
  Pete

I would do it like this:
[LIST=1]
[*]20 Gb for windows
[*]70+ for shared data, but if you do still use windows make it not ext3 but fat or ntfs so you can acces the disk from both os.
[*]5 Gb for home (I don't put my docs nor downloads in home, I use a seperate disk, in your case the shared data disk I presume. Thats why home can be small)
[*]20 Gb ubuntu
[*]2x your memory size for swap (so if you have 1024 mb of mem then a 2048 Mb swap)[/LIST]Jeroen

---

### Post by pohlipit on 2007-04-09
Thanks everyone for your help. I managed to install with 4 partitions:
- 25GB Windows
- 70GB data (as /home)
- 20GB Linux
- 2GB Swap

Works like a charm and should I ever have to go back to Windows it's just a startup-manager click away.. though hope I won't have to do it too often.

Cheers,
 P

---

### Post by Inxsible on 2007-04-09
Novice question,

but what exactly is a swap drive used for?

Also it was mentioned that its better to have a FAT or NTFS drive so it can be accessed by both OS. but there are drivers which can access an EXT3 drive in Windows called EXT2IFS
[HTML]http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm[/HTML]
and
EXT2FSD [HTML]http://ext2fsd.sourceforge.net/#ext2fsd[/HTML]

So would it be better to have an NTFS or FAT drive or an EXT3 drive ?
Does one have an advantage over the other?

---

### Post by robenroute on 2007-04-09
Hi there,

You might want to give [this]("http://ubuntuforums.org/showthread.php?t=282018") thread an oggle; there's loads of useful info in there.

---

### Post by robenroute on 2007-04-09
> **Inxsible said:**
> Novice question,

but what exactly is a swap drive used for?

Also it was mentioned that its better to have a FAT or NTFS drive so it can be accessed by both OS. but there are drivers which can access an EXT3 drive in Windows called EXT2IFS
[HTML]http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm[/HTML]
and
EXT2FSD [HTML]http://ext2fsd.sourceforge.net/#ext2fsd[/HTML]

So would it be better to have an NTFS or FAT drive or an EXT3 drive ?
Does one have an advantage over the other?

FAT systems have no file permission functionality, which often leads to practical issues when sharing such partitions between Linux and Windows. the new NTFS-3g driver for Linux offers both read and write functionality on NTFS file system partitions. Like you said, there are also Windows solutions for accessing Linux (ext2/3) partitions. I suppose it all depends on what you use most often. If you're a Linux person, occasionally firing up your XP installation, I'd stick to ext3 (because of the added safety of journalling). If you're more of a Windows user, stick to NTFS and use the NTFS driver in Linux.

BTW, the swap partition is like an extension of your RAM; it's used by the running system to temporarily park active programs and program-related data when the computer's RAM is insufficient (and thus preventing running out of memory). My system has 1GB of RAM and 2GB of swap space. However, the system seldom uses more than 200MB of the available swap space.

---

### Post by Nythain on 2007-04-09
yeah, id definately leave out fat... the lack of permission functionality and the not yet mentioned 4 gig (i think) max file size limit sucks... i had a fat32 partition till i tried downloading a dvd, that didnt last to long.
as mentioned above... if you boot windows more use ntfs with the appropriate linux driver... if you find yourself using linux more then stick with ext3 with the windows driver. If your anything like me id just go ahead with the ext3, i eventually found myself NOT booting into windows anymore, removing windows... then i had to shuffle a bunch of data off a ntfs partition over to ext3, it sucked... ended horribly... and started anew pure ext3

---

