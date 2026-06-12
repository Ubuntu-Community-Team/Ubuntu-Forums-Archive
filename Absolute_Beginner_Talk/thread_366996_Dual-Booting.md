---
title: "Dual-Booting"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-02-21
If anything that gets people confused when using Ubuntu is to get it to dual-boot Windows. There are so many dual-booting how-tos out there, but they only make things more complex than they seem. Like, for instance, some of them say to get a System recovery CD.

But, Linux can dual-boot by it's own LIVE CD. You just have to insert the CD, boot the CD, highlight and hit 'Start or install Ubuntu' click the icon 'Install', follow through it's instructions, and resize your Windows partition.

Makes me wonder why bloggers make this too complex.

---

### Post by Sqwishy on 2007-02-21
Because sometimes you might wana make an extra fat32 partition or something so you can share files between windows and linux. Also i don't remember that resizing feature in dapper, is it new?

---

### Post by fjf314 on 2007-02-21
It is in Dapper.  The first time I installed Dapper I was trying to dual-boot to XP.  All I had to do was simply tell it how much space I wanted to take from my NTFS partition to use for Ubuntu and it handled the rest.

---

### Post by mikewhatever on 2007-02-21
I'd say it is not complex, but rather diverse. People seem to like different things and I am sure you too might like some variety in certain aspects of life. A system recovery CD is for recovering the system in case there are problems, such as boot etc. You do not need it for dual booting, but it's a good thing to have, just in case.

---

### Post by st33med on 2007-02-21
No, no. They were using the system recovery CD to format partitions, not for recovering.

---

### Post by mikewhatever on 2007-02-21
Now that you have mentioned it, I happened to have use one for partitions myself, because Ubuntu Alternate CD I used could not resize the partition I wanted it to. The CD I used showed a message indicating there was a problem I had to deal with. After that, all was fine.

---

### Post by kristalsoldier on 2007-02-21
Hi...

As my previous post on another thread says I am really very very new...so please bear with me. I have just begun to use ubuntu using a Live CD. Am on the net. Sound works, touch pad works etc. BTW, I am using a relatively new Sony Vaio laptop (I mention this because while doign some reading on the net, most of what I found were horror stories!).

Anyways, it appears that my machine has NTFS. BTW, it also has Win XP, which I probably need to maintain for my university work. I would like to have the dual boot facility. With Ubuntu running via the DVD drive, on the desktop there is an icon for 'install'. Reading the posts above tells me that if I click it, there is a good chance that Ubuntu will partition my drive and install itself. What precisely does this mean?

Does it mean that when I fire up my machine it offer me a choice to booting up in either mode? Does it also mean that I can read a win xp file while operating within an XP environment? Does it mean that if I write a document in Open Office in Ubuntu mode, I can read the same from XP?

Also - and this is probably not directly related to this topic - but it seems that the touch pad is somewhat sluggish while running ubuntu off the CD. Do things get better if it installed on the hard drive?

Thanks.

---

### Post by fjf314 on 2007-02-21
If you intall Ubuntu, it'll give you quite a few options for where to install the system to.  If you want to keep it simple, you don't have to make any partitions yourself.  Rather, you can have Ubuntu simply take some of the space from the Windows NTFS partition.  It'll break that down into the partitions it needs and format them.

If you do this, the Windows boot loader will be replaced with the GRUB bootloader.  When you turn on your computer, you''ll be presetend with a menu from which you will be able to select Ubuntu or Windows.  If you don't make a choice after a few seconds Ubuntu will load automatically (although this is only the default, it can be changed however you want.)

Also, I've never really used the Live CD, but I've heard many people say that it runs much slower than the OS actually does when you install it, which makes sense.

---

### Post by kristalsoldier on 2007-02-21
Cool! Thanks.

Does that also mean that I can rea documents across platforms? Intuitively, I'd say not because how would they talk to each other? Am I correct?

Thanks.

---

### Post by fjf314 on 2007-02-21
You will have to mount your NTFS partition in Ubuntu.  If you do this, you will be able to read the files on the Windows partition.  By default, Ubuntu can only read from NFTS partitions, though, it cannot write to them.  You can change this, but it takes some work.

---

### Post by kristalsoldier on 2007-02-21
OK. Well, when I load up ubuntu from the cd drive, there are a few error messages - there is one about RAID, one about RNG and there is something about 'mount failed'. I'll slip in the Live CD and post the precise error msg. Does this have any bearing on what you have mentioned?

Thanks.

---

### Post by kristalsoldier on 2007-02-21
OK...here it is...

While loading ubuntu from the live cd, I ge the following:

mount: function not implemented.

How does this affect in terms of what you mentioned in your last post? What should I do?

Also, there are a few 'failed' items under ACPI.

Again, what should I do?

I have not yet installed Ubuntu and am continuing to load up from the Live CD. Should I ignore the above and go ahead and install?

Thanks

---

### Post by mikewhatever on 2007-02-21
Mount function not implemented is not an error. It just tells you the HD partitions are not mounted during a live session, but you can mount them manually.
About the other error, was it similar ti this:
> [17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
I have this error during every boot, but so far haven't found what it relates to, haven't really looked, to br honest, because it doesn't affect the performance. Probably it is something I don't use, like PCMCIA card.
You can/should check whatever you need to work from the live cd.

---

### Post by kristalsoldier on 2007-02-21
OK. Thanks. Nope. The APCI error did not look like that. I'll try to make a copy now and will repost.

Thx.

---

### Post by kristalsoldier on 2007-02-21
Here is what it looked like:

acpi support: No such manufacturer system supported

The wording may not be 100% accurate, but its close enough...the script scrolls down very fast...

Thanks

---

### Post by TimJBart on 2007-02-22
Can I just clarify on the whole dual boot thing.

About a year ago I wanted a dual boot.  So I used gparted to make some linux compatible partitions and install ubuntu to there.

I now want another dual boot.  From what people are saying, can I just use the install CD and tell it to get 100Gig from my NTFS hard drive?  Simple as that?  It won't hose the whole drive? If so, that sound brilliant!

(FYI, I gave up on ubuntu previously because I had an ATI gfx card....but now I have nvidia!)

p.s. If I do need to use gparted and do it myself, what were the 3partitions I have to make, root, hda1....something else?  I can't remember.  Obviously I'd rather the ubuntu install did it for me, but don't want to wipe my whole machine by accident as I once did in my stupidity

---

### Post by kristalsoldier on 2007-02-22
Does the ACPI-stuff have to do with power management? If yes, how does the absence of this on my laptop with ubuntu matter? Does it mean that I will not be able to control power settings? Well, I really don't care as long as it does not reduce the current power (on battery) capabilities!

This is surely the wrong thread for this. So, my apologies. I will stop this right now.

Thanks for your patience.

---

### Post by kristalsoldier on 2007-02-22
> **fjf314 said:**
> It is in Dapper.  The first time I installed Dapper I was trying to dual-boot to XP.  All I had to do was simply tell it how much space I wanted to take from my NTFS partition to use for Ubuntu and it handled the rest.

I have a 100GB HDD on my laptop. I have win xp running on the machine pre-installed. Given this what would you advise the space I should allocate?

Thanks

---

### Post by st33med on 2007-02-22
Heh, boy oh boy, I'm was the poster of Dual-Booting and I didn't know you could mount it.

How DO you mount Ubuntu on Windows?

---

### Post by gdahlbeck on 2007-02-22
My system at work is currently set up to dual boot with SUSE 10.2 and XP (we use XP for our accounting so for now we need both). I want to switch from SUSE to Ubuntu but when I start the installation and get to the partition page I'm not sure how to install Ubuntu where SUSE currently resides and preserve the dual boot capability. Can I simply designate the current Linux partitions for the Ubuntu install? Will the current Linux boot loader remain functional or will I need to re-install GRUB?

---

### Post by st33med on 2007-02-22
It will preserve your dual-boot, but you are going to manually partition Ubuntu. 

First, when you get to the part of how to partition the hard-drive, click on manually edit partition table or something like that and hit next. Delete the partition for SUSE ( I don't know what file system it should be, but it shouldn't be NTFS) and anything associated with it in the extended partitions. Make a partition for ext3 and extended, making extended 1 GB. Now below the extended partition, make a linux swap-file logical partition. And that should be it! Just follow the rest of the instructions.

---

### Post by Douglas B. on 2007-02-22
Hi Guys
  I guess if you have created partitions on a hard drive before it doesn't seem very hard; but I have never done it. And i'm running into a problem. 
   I have an Acer 9300-5024 laptop with a 160 GB hard drive. I have downloaded both 6.06.1 LTS and 6.10.  I ran "Check CD for defects" and both disks are OK. Both disks run fine from the CD. 
   Everything goes fine when I click Install  untill it gets to the options. As it is switching from the "Who are you?" page to the "Prepare disk space" page there is a quick desplay stating that I will be able to choose three options; but when the "Prepair disk space" page opens there are only two options.

          Erace entire disk, and Manually edit'  

The first option, "Resize IDE1master,partition#1[hdal]and use free space isn't there at all.
      I tried the 6.10 disk first and then the 6.06. It was the same on both disks. 
         I have no idea how to do it manually.
      If I have to do it this way does anyone know a site that will give me step by step instructions? 
                                                             Thanks again guys
                                                                        Doug

---

### Post by rusty4r on 2007-02-22
> I have win xp running on the machine pre-installed.

If your windows is preinstalled you probably have restore disks. Be careful here becausse some restore disks do nothing more than point to a restore partition on your harddrive. I have learned the hard way that if you do anything with that partition tha restore disks will no longer be able to find your restoration files.

---

### Post by kristalsoldier on 2007-02-23
> **rusty4r said:**
> If your windows is preinstalled you probably have restore disks. Be careful here becausse some restore disks do nothing more than point to a restore partition on your harddrive. I have learned the hard way that if you do anything with that partition tha restore disks will no longer be able to find your restoration files.

Hi...

Well. this Vaio did not come with any restore disks. I had to make one. So, there is a C: and D: Apparently, the D: had the restore info, which after I made the restore disks became 'free space'. Now, the Vaio documentation said that this is the way to recover the HDD space (my machine came with 100GB). Earlier the D: was full, but as I mentioned above, the making of the restore disks freed up that space.

So, my machine now looks like this:

C: Total Size 46.5 GB Free Space: 10.9 GB
D: Total Size: 39.5 GB Free Space: 39.5 GB

This leaves 14GB unaccounted for, which I presume is still held by XP. Is this where the restoration files that you referred to live? So, what are my options?

Thanks

---

