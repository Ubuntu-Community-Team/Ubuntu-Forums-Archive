---
title: "Confused about adding new drives"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-06-15
I've been using Ubuntu since Dapper, but never really got into the inner workings.. I just use it to be productive.

Now I find how little I really know about Linux.

My wife and I built up a nice machine from scratch.. Machspeed MSNV-939 motherboard, AMD X2 3800+, 4G of RAM because I want to use VMware or other virtual machines, and a single 74G 10,000 RPM Western Digital Raptor.

All went fine, and the machine runs great, so I decided to remedy to the one major shortcoming which was lack of disk space.  I should have done more research, I see now, but my plan was to buy a second identical Raptor and run them in RAID 0 for speed.  Then to buy two Western Digital Caviar SE16's, 500G each, and use those for data storage.

Well, this is where the problems begin.  I was informed that the "fakeRAID" on my motherboard wasn't going to do what I wanted, and that, furthermore, I would see no improvement in performance with the system disk a RAID 0.. that all I would do is dramatically reduce the system robustness.

Okay, plan B, suggested by someone else, was to install fresh on the two Raptors, and to simply put / and swap on one, and /home on the other.  At least then I'd be getting some benefit from the two little drives.  Furthermore, I suppose I could, in the future, reinstall the OS on the first Raptor, and the one with the /home partition would retain my settings and preferences.

But then some people started telling me I should look into LVM, the logical volume group manager, and since then I've become more confused by the moment.

I had enough screws to install the second Raptor.  Since WD didn't bother sending mounting screws with drives, the two Caviars are sitting on my desk looking at me with what I'm certain is a degree of scorn as I type this.  Using fdisk, I simply put a single ext3 partition on the new Raptor, and tried mounting it by editing fstab.. but the drive came up as root only.  I tried the fresh install, with just /home on the second disk, but It didn't seem like I was getting much benefit from this, and so I wanted to explore the LVM more.  I still don't have the least grasp of how LVM is supposed to work, but keep reading and hope I'll get my head wrapped around the concepts eventually.

I learned about Linux Software Raid, and wanted to try that.  I have a hard time understanding how RAID 0 could *not* be faster.. when you ask for a big program to load, you've got two guys loading the truck rather than just one.  Seems like it has to help.  But I couldn't get it to work.

Finally, just for time being, I decided to add all three of my new disks as just data disks, and perhaps move projects that require real speed onto the Raptor while working on them, then moving them back to the Caviars.  Could be okay, I guess.. but I keep feeling like there must be a better solution for me.

What would people suggest?  Is LVM the way to go?  If I don't care that I may have to reinstall the OS occassionally, would RAID 0 buy me anything for the system disk?  I understand it's less reliable that way, but I don't care.  I reinstall periodically anyway, and would like to see for myself how RAID 0 or perhaps some other RAID level might work.

As an aside, what's a new Windows user who just transitioned to Ubuntu going to do when they buy a new drive?  Edit /etc/fstab, and somehow know what the UUID of the new drive is supposed to be?  This may be an area where Ubuntu could focus some attention to making this as easy as on Windows.  Mount the drive, reboot, the system sees the new drive, etc.

I'm lost.  Any help appreciated, for any workable solution.. but preferably one which really uses my resources to their absolute best advantage.

Thanks,
Bob

---

### Post by kidders on 2007-06-16
Hi there,

> **RTrev said:**
> I was informed that the "fakeRAID" on my motherboard wasn't going to do what I wanted, and that, furthermore, I would see no improvement in performance with the system disk a RAID 0.That seems reasonable. I've always avoided using those cheap RAID implementations that seem to be finding their way onto more and more motherboards.

> **RTrev said:**
> Okay, plan B, suggested by someone else, was to install fresh on the two Raptors, and to simply put / and swap on one, and /home on the other. That seems sensible too. :-)

> **RTrev said:**
> But then some people started telling me I should look into LVM, the logical volume group manager, and since then I've become more confused by the moment.LVM is really just a convenient way of overcoming the limitations of the various disk partitioning schemes. Some distros use it by default; some don't. Personally, I'd never use LVM unless I had a specific reason for needing to.

> **RTrev said:**
> Using fdisk, I simply put a single ext3 partition on the new Raptor, and tried mounting it by editing fstab.. but the drive came up as root only. I'm not sure what you mean by that, but ...[LIST]
[*]Strictly speaking, Ext3 is a *filesystem* type (not a partition type).
[*]Modifying your /etc/fstab is an optional convenience.
[*]Just the same as any other OS, to use a disk with Linux, you need to partition it, and add one or more filesystems to it. It/they can then me mounted wherever you like.[/LIST]Hopefully, you already know these things, but just in case, I thought I'd write them down.

> **RTrev said:**
> I learned about Linux Software Raid, and wanted to try that.  I have a hard time understanding how RAID 0 could *not* be faster.RAID 0 *can* be faster than other possible configurations ... but not necessarily so. It depends very much on how well-configured it is, and how good your hardware is. Personally, how fast RAID 0 can be has never been relevant to me ... it's too dangerous for practical use imo.

> **RTrev said:**
> If I don't care that I may have to reinstall the OS occassionally, would RAID 0 buy me anything for the system disk?That very much depends on what you're looking for. Performance? Reliability? Scalability?

> **RTrev said:**
>  As an aside, what's a new Windows user who just transitioned to Ubuntu going to do when they buy a new drive?  Edit /etc/fstab, and somehow know what the UUID of the new drive is supposed to be?  This may be an area where Ubuntu could focus some attention to making this as easy as on Windows.  Mount the drive, reboot, the system sees the new drive, etc.A drive's UUID is not normally important (unless you want to manipulate its /dev names for some reason). You may be thinking of filesystem UUIDs ... which you don't have to refer to in /etc/fstab unless you want to, for some reason. (If you do happen to want to use them, they're easily determined though.)

To be honest, Microsoft's almost arrogant "if there's a new disk in the system it must be for me" approach isn't something I can see being adopted by any other OS. Linux quite rightly won't touch a disk unless it's told to do so.


Anyhow, to try to get the best out of your system, I would suggest two things:[LIST=1]
[*]Decide on a particular goal. Speed & reliability, for instance, often trade off against each other, so it's important to know which one you want more.
[*]Know where your system's bottlenecks are. For instance, people may tell you that you can boost performance with ...[LIST]
[*]RAID 0 (because using two disks at once seems smarter). Not so if you're I/O bus is narrow, one disk is slower than the other, or you care about doubling the failure probability of your system.[/LIST][LIST]
[*]Using high-performance filesystems. This is only smart if you have enough CPU time available to handle the increased demand.[/LIST] [/LIST]There are lots of factors that influence what's worth trying and what's not. For instance, the idea of putting applications that need to perform faster on better disks (I think you mentioned that) won't achieve much if your system libraries are living on a slow one.


I hope this post is of some help!

---

### Post by RTrev on 2007-06-16
Hi Kidders,

Thanks for your detailed reply!  It was very helpful.

Rather than end up with a monstrous quoted reply, I'll just hit on the high points.  <g>

First, I find myself reinstalling my OS so often that I can do it in my sleep.  So if I could gain some really significant speed improvements by doing some type of RAID on two system disks, I'd be willing to put up with what I consider a fairly low risk.  I think of it as low because 1) this isn't a production system that has to be up all the time, and 2) I can't honestly remember the last time I had a disk fail.  I routinely (every  three months or so) run Steve Gibson's SpinRite on my disks, and it seems to me that modern disk technology is pretty good.. and they tell me that the Raptors are even better.

So... yes, I'd be willing to take that chance if it would noticeably speed up the system.

You note that my hardware might not be sufficient to see any benefit from the RAID 0.  I don't honesstly know, but it's SATA-150, and it's my understanding that most drives can't even come close to saturating that connection, let alone the SATA-300.

If the rest of the hardware is pertinent, it's a dual-core AMD X2 3800+ with 4G of PC3200/DDR400 (a maxed out Machspeed MSNV-939 motherboard.)  I'd have gotten something a bit different perhaps, but it was a gift from my wife.  ;)

So, if I'm right, which isn't a common occurrence, the two identical 74G Raptor drives might possibly come close to the constraints of SATA-150, but they certainly aren't now.

Let's say that I were instead to reinstall and to use both disks for various partitions.  Which partitions would be best to put where, and how much would that gain me?  Follow up questions: if one of the drives died, wouldn't I be *almost* as far up the crick that way as if I'd had a RAID 0 member fail?  And, all of my data will be on other drives which *won't* be RAID 0.

Exploring the idea of dividing up the partitions between the two Raptors during install, what would be the best configuration to get the most benefit?  I'm a newbie, and the arcane world of Linux partitioning is beyond me.  I normally just tell installers to take the whole disk and do whatever they want to it.  :)  So any detailed advice about how to even the load between the two physical drives would be helpful.

Thanks very much for your help!!

---

### Post by kidders on 2007-06-16
> **RTrev said:**
> Rather than end up with a monstrous quoted reply, I'll just hit on the high points.  <g>Lol sorry about doing that! It's sort of annoying to read, isn't it!

Anyhow, your assessment of your hardware is correct imo. :-) You should be able to run RAID 0 across two disks, pretty close to theoretical speeds. The remaining issue to take care if is your choice of filesystem. When you're using striped RAID with Ext3, for instance, aligning the filesystem's block boundaries to the stripes is pretty critical. It is possible to create a filesystem with blocks that don't fit neatly, which really takes the edge off performance. Ext2/3 provide special parameters for making sure this happens the way it's supposed to.

The way I see it, one practical problem with performance-motivated RAID 0 is avoiding delaying I/O to one of the array's components. Naturally, without instant access to both disks at the same time, your efforts to increase your I/O speeds will all be in vain. :-( So you couldn't, for instance, put your swap on one of the disks being used for RAID. Similarly, if you like to edit movies (or maybe something else that requires a specially optimised filesystem), you couldn't use part of your RAID disks for that either. You'd end up with...[LIST]
[*]Maybe a 2x74 GiB RAID 0 array with a whole pile of wasted space on it.
[*]A third device with maybe /boot, /home, swap & an extra optimised-for-purpose filesystem on it.
[*]I/O being routinely spread over three devices (rather than just one or two). I can't help feeling that this might create some latency.[/LIST]Am I over-analysing things, do you suppose? Perhaps the best way to be sure would be to try a few things out, but it would be irritating & time-consuming to do that.


> **RTrev said:**
> Let's say that I were instead to reinstall and to use both disks for various partitions...The main problem I have with RAID 0 is that, given the size of modern hard disks, the sheer volume of data that can be lost in one go is a little intimidating, given a two- or three-disk array. I always feel happier if the failure (unlikely as it is) of _one_ device results the loss of _one_ disk-full of data ... or perhaps no data loss at all (with RAID 1 or 5, for instance). Not all users have the same concerns, but I still wanted to raise the issue, just in case it was something you'd overlooked.

Anyhow, if you were, as you suggested, to do away with RAID altogether, your policy would probably then shift to trying to get as much synchrony as possible out of disk accesses ... because each I/O operation would no longer be using double the bandwidth it should. Putting /home and /usr on two different disks, for instance, might be smart. Another thing people try involves splitting their virtual memory over multiple devices, to try to offset the massive difference between RAM & disk access speeds a little. With 4 GiB of RAM though, I doubt you'll be doing very much swapping lol.

It's worth noting that the idea of partitioning disks is far from arcane. In Windows, for instance...[LIST]
[*]The fact that swap space is wrapped inside another filesystem creates latency and security issues with virtual memory.
[*]The fact that applications, users' data files, virtual memory & the OS itself are all typically packed into the same filesystem forces I/O that could be performed in parallel to be done sequentially.
[*]The policy also significantly worsens the effect of filesystem fragmentation, which is a major issue with Microsoft's dumb filesystems anyway.
[*]Additionally, very few MS users' filesystems are optimised for purpose ... because they don't really have any specific one.[/LIST]Linux, on the other hand, encourages users to trade speed off against recoverability (eg by dropping filesystem journals) on some of a system (but not all of it), and allows them to use specialised filesystems like ReiserFS or XFS where appropriate, without having to suffer their disadvantages.

Perhaps the best way to get a little extra speed out of your system is to try to take advantage of the slightly odd-looking, purpose-oriented way the typical Linux filesystem is organised. As a simple example, you might decide to put some of the directories in / onto separate partitions or disks...[LIST]
[*]Having /home on a separate disk would let you take it out & slot it into another PC is an emergency. Alternatively, I answered a post recently by a guy who wanted to use RAID 1 on /home, for reliability. It's also nice to keep it away from the rest of your system, because it's probably the one directory that's most likely to fragment.
[*]/var is written to almost all the time, since it's where system logs are kept. Speeding up access to that directory any way you can would have a small impact, but it would be across the board.
[*]I often hide movies, sound, disk images & other large files in /opt, mounted on a filesystem with very large block sizes.
[*]You might find that, for many of your system directories, you couldn't care less about certain metainformation, such as the date a file was last accessed. Filesystems that store pointless information like that usually let you turn it off, so read operations don't perpetually cause writes.[/LIST]> **RTrev said:**
>  First, I find myself reinstalling my OS so often that I can do it in my sleep.That's nasty. The one thing I always say to people who are thinking of giving Linux a shot is that it takes forever to set it up properly. It offers so much freedom and flexibility over even the most insignificant of details, that I often find it takes me a *week* to get a box running just the way I like it. As a consequence, it probably isn't the right choice for a frequent reinstaller. The goal with a Linux system is to engage in the typical Microsoft behaviours (ie if it breaks, reboot; if that doesn't help, reinstall) as infrequently as humanly possible. That's chiefly why doing stuff like suspending, booting & installing Linux has always been a slightly messy affair ... people almost never (relatively speaking) do any of them!

I hope there's something useful in here ... to be honest (having re-read it) I'm not so sure! You see, aside from general advice, it can be hard to offer someone very specific help when they're not doing something blatantly silly, and just want to tweak & optimise a little. Two important things to note are:[LIST=1]
[*]Don't try to implement *_all_* the possible performance enhancements people (including me!) suggest to you. When combined, some of them will have the opposite effect!
[*]If you try something like RAID 0, be sure to measure the impact.[/LIST]Nice machine btw! I have a similar one (with less RAM), and I'm quite happy with it :-)

---

### Post by RTrev on 2007-06-16
> **kidders said:**
> Lol sorry about doing that! It's sort of annoying to read, isn't it!

No, it's actually helpful in "maintaining context" <g>, but I was thinking about a triple-level quoted message.  I'm kind of new to the forums, and not expert at snipping out just what I want.  I'll give it a try here.

> 
Anyhow, your assessment of your hardware is correct imo. :-) You should be able to run RAID 0 across two disks, pretty close to theoretical speeds. The remaining issue to take care if is your choice of filesystem. When you're using striped RAID with Ext3, for instance, aligning the filesystem's block boundaries to the stripes is pretty critical. It is possible to create a filesystem with blocks that don't fit neatly, which really takes the edge off performance. Ext2/3 provide special parameters for making sure this happens the way it's supposed to.


Hmm.. now there's something that hadn't even occurred to me.. using a different file system.  I had the impression, being a newbie and all, that ext3 was the latest and greatest, and that one simply used that and didn't give it a second thought.  But if I were to go with a more streamlined and designed for speed system, that might, in conjunction with moving partitions around as you discuss below, do the trick.  Hmm.  What would you think might be the fastest, least overhead, file system to try?  I think I read that an about-to-be-released version of Reiser was supposed to be super fast, but perhaps that's been delayed given his, ah, legal problems?

> 
The main problem I have with RAID 0 is that, given the size of modern hard disks, the sheer volume of data that can be lost in one go is a little intimidating, given a two- or three-disk array. I always feel happier if the failure (unlikely as it is) of _one_ device results the loss of _one_ disk-full of data ... or perhaps no data loss at all (with RAID 1 or 5, for instance). Not all users have the same concerns, but I still wanted to raise the issue, just in case it was something you'd overlooked.


I guess the way I've been viewing it is that I wouldn't have my own data on the RAID 0, so the very worst that would happen is that I stick in the install CD again, and an hour or so later I have my system set up again, with Twinview working, and with the handful of apps that I download from the repositories.  My data is intact, and I've spent at most a few hours doing  tweaks and special settings.

> 
Anyhow, if you were, as you suggested, to do away with RAID altogether, your policy would probably then shift to trying to get as much synchrony as possible out of disk accesses ... because each I/O operation would no longer be using double the bandwidth it should. Putting /home and /usr on two different disks, for instance, might be smart. Another thing people try involves splitting their virtual memory over multiple devices, to try to offset the massive difference between RAM & disk access speeds a little. With 4 GiB of RAM though, I doubt you'll be doing very much swapping lol.


You might be surprised. <g>  I've been having fun lately with VMware Server, and things like that mean that 4G of RAM doesn't go as far as one might want. :-) 

> 
It's worth noting that the idea of partitioning disks is far from arcane. In Windows, for instance...


<snipped list of excellent of examples of partitioning benefits>

Arcane: requiring secret or mysterious knowledge; "the arcane science of dowsing"  :)

I meant arcane in the sense of it being knowledge that I myself am not in possession of.  :)  For example, in my initial learning curve, I've not yet gotten to the details of what each of the partitions are intended to be for,  what goes where and why, etc.  I know a lot of things I mess with end up in /etc, like the xorg.conf file, but I think of that as the "etcetera" directory!  I have no idea of the logic behind the various divisions yet.  In fact, it was just last night that it actually dawned on me that Linux thinks of everything as files, and that once a physical drive is merged into the system it ceases to be seen as a physical device at all.  You're talking to the Linux-challenged here!

> 
[*]Having /home on a separate disk would let you take it out & slot it into another PC is an emergency.


Okay, there's a good one to keep on the secondary boot disk.  I need a list of the ones best moved, how big they should be, etc.  Probably you can't tell me the answer to that without knowing how I use the system, but my usage pattern hasn't stabilized yet as most of my time has been being put into building a good platform to begin working with.  I recently retired, and now have time to actually begin enjoying computing again. :-)

> 
Alternatively, I answered a post recently by a guy who wanted to use RAID 1 on /home, for reliability. It's also nice to keep it away from the rest of your system, because it's probably the one directory that's most likely to fragment.


Whoops, brake lights coming on here.. I thought that fragmentation was not an issue at all with Linux file systems?  Of course I'm sure it's not black and white, but I gathered that I shouldn't worry about it.  Not totally correct, eh?

> 
[*]/var is written to almost all the time, since it's where system logs are kept. Speeding up access to that directory any way you can would have a small impact, but it would be across the board.


Okay, there's another one for my list of ones to keep on the other disk.

> 
[*]I often hide movies, sound, disk images & other large files in /opt, mounted on a filesystem with very large block sizes.
[*]You might find that, for many of your system directories, you couldn't care less about certain metainformation, such as the date a file was last accessed. Filesystems that store pointless information like that usually let you turn it off, so read operations don't perpetually cause writes.


Ah, there's something I didn't know.  No, I never use such information.. and would be happy to be using a lean and mean file system with as little overhead as can be achieved.

> 
That's nasty. The one thing I always say to people who are thinking of giving Linux a shot is that it takes forever to set it up properly. It offers so much freedom and flexibility over even the most insignificant of details, that I often find it takes me a *week* to get a box running just the way I like it. As a consequence, it probably isn't the right choice for a frequent reinstaller. The goal with a Linux system is to engage in the typical Microsoft behaviours (ie if it breaks, reboot; if that doesn't help, reinstall) as infrequently as humanly possible. That's chiefly why doing stuff like suspending, booting & installing Linux has always been a slightly messy affair ... people almost never (relatively speaking) do any of them!


I messed up my quoting here somehow, so it isn't clear that you're referring to constantly reinstalling as what's nasty.  :)

I should explain.. I don't *need* to continually reinstall.  It's an artifact of my trying out different things in my learning curve.  Like 64-bit versus 32-bit, Automatix which was handy for me initially but which I've stopped using and recommending, trying  Debian Etch, trying PCLinuxOS, back to Ubuntu-64, miss the drivers, back to 32-bit, trying out the first cut of Gutsy, back to Feisty, and so  on.  I tend to find remnants of old things even after doing a complete removal of them, so am inclined often to simply reinstall and know that I'm starting clean again.  This is part of my fascination with virtual machines lately, in fact.  PCLinoxOS/2007 has some weird issue with SATA drives, and doesn't work well on my system.   But it works fine inside VMware Server, so I check it out there.  I can see myself winning over many converts from Windows when they whine about not being able to run program X, and I boot up XP  in 8 seconds inside a VM and watch their jaws drop.  ;-)

> 
I hope there's something useful in here ... to be honest (having re-read it) I'm not so sure! You see, aside from general advice, it can be hard to offer someone very specific help when they're not doing something blatantly silly, and just want to tweak & optimise a little.

Oh, have no fear.. I've learned a LOT from your notes here.. Gracias!  And I'm sure I would have come up with many silly things.  I almost pulled a "silly thing" the other day when I found the solid state disks and thought "Oh wow, my basic system install is smaller than that!"  A gentleman on the GRC groups set me straight about that.. industrial use, very slow, I wouldn't be happy, etc.  And I'm sure I'll have other silly ideas.  :)  It's the kindness and patience of people like you who make this voyage so much fun!

You've given me a lot here, like to look at other file systems besides ext3, to turn off unnecessary journaling,  and to pay attention to which partitions are being written to constantly and move those to divide up the load a bit more effectively.

Much appreciated feedback!  Thank you!

---

### Post by kidders on 2007-06-16
Hey again,

> **RTrev said:**
> I had the impression, being a newbie and all, that ext3 was the latest and greatestIn actual fact, the Extended filesystems (Ext2, Ext3) are afaik the oldest in common usage. Having said that, they are still significantly superior to anything Microsoft has to offer; Apple's HFS filesystem is probably a bit smarter than it though, imo. The most important things I would say about choosing a filesystem are...[LIST]
[*]With very few exceptions, none is necessarily any "better" than another. They are just different. I hope you'll excuse the lame analogy, but it's a little like trying to decide which *car* is best. While sometimes the choice is blatantly obvious (Toyota Starlet vs Bugatti roadster), I've heard people get tangled up in the 3 Series/C Class argument for hours!
[*]Never, ever, ever try anything new. Ever. Unless of course you're a bleeding-edge kind of person who's used to having to yank his PC back from the edge of oblivion on a daily basis hehe.[/LIST]The way you described setting up your system (ie considering your OS to be almost "disposable", while taking good care of your personal stuff), is exactly how I like mine ... on a desktop PC at least. :-) Since you mentioned twinview though, I would suggest keeping a copy of your /etc archived away in some corner of your personal space. Copying & pasting X, Samba, Apache & other system configurations into a new system is waaay nicer than going from scratch!

The other thing you mentioned was VMWare...

Regardless of how much RAM you have, using VMWare will (and should, I suppose) pretty much always cause your machine to swap stuff out to disk, almost as a matter of policy. The thing I love about my X2 is that no matter how busy virtual machines get, my Ubuntu stays nice and responsive (because I confine VMs to a single core). I am falling victim to swapping-related latency though, which I haven't gotten around to fixing yet. Once I do, I'll certainly post what I tried & how it went, in case one of us can learn something from the other's experience.


> **RTrev said:**
> Arcane: requiring secret or mysterious knowledge; "the arcane science of dowsing"  :)Hehe thanks for that! I went for "Arcane = Baffling", which clearly isn't quite what you meant. Sorry.

The Linux learning curve is ... well ... intimidating as hell! I still remember the very first time I tried Linux (Corel Linux, I think), in the early 90s. I was completely stumped by it ... and I hadn't yet discovered the joys of the 33kpbs modem, so I had nowhere to turn lol.

In case you're interested, the standard layout of a Linux '/' directory (shared with Unix, BSD, OSX, and so on) is an archaism that dates right back to the dawn of time, really. It's usefulness is diminishing (particularly so in recent years), but it's a convention that has served users well. One of the things Windows users (but not Mac users) find odd about it is that nothing seems to be in the "right" place. For instance, when you install Firefox on a Windows box (if memory serves me well), pretty much all of its bits & pieces wind up somewhere sensible, like C:\Progra~1\Mozilla. Linux, on the other hand, organises its stuff by *purpose*, so bits of it go into /usr/share/doc, /usr/share/icons, /usr/share/lib, and so on.

What you remarked about Linux being very file-oriented is quite correct, and is very powerful. You can do all sorts of daft things with it, such as opening something crazy, like a property of your CPU, in a text editor & fiddling with it ... or echo-ing (I think the MS command is "type") a .wav file directly to your sound card. It also makes accessing things like network shares very easy.

Anyhow, on to partitioning schemes ...

This may seem like an obvious thing to suggest, but don't feel like you have to allocate all of your disk space right away. Over time, people develop a feel for the sort of ballpark they need to be in, when it comes to allocating space for various things, so I would suggest:[LIST]
[*]Something in the region of 10G or less for the exclusive use of your Ubuntu system, using a general purpose filesystem. Personally, I like to take steps to see that this part of my system is snappy & responsive, by *not* sharing the disk with swap space or my /home, and doing a few other things that have to wait until later, such as prelinking. The ideal, for many people, is to throw their second operating system into the spare disk space.
[*]If you write websites, making /var/www into a separate partition can be smart. In theory, small files do well on ReiserFS, although any difference is likely to be imperceptible on anything other than a production server. Basically, anything that qualifies as "personal files" should really be somewhere other than your root filesystem, for my "10G or less" guideline to hold.
[*]The usual rule for /home is "as much as is available". On my system however, I have over 300 GiB unallocated at the moment, so that if something were to require more room at some point, I could just pull it out of thin air, rather than having to steal it from someplace.
[*]One concern for you will be swap. For instance, in order to hibernate your PC, you'll need at least as much swap as RAM, so you have somewhere to put it when you power off. On the other hand, you don't really want to encourage your computer to start wallowing around in 4 GiB of virtual memory! What to do here is *very* individual, but I would suggest considering perhaps allocating one or two 768 MiB high-priority chunks (ie to operate in parallel), and if it turns out to be necessary, you could add a third 1 or 2 gig low-priority chunk (ie the kernel is discouraged from using it unless necessary) partition later.[/LIST]Anyhow, I could babble on and on about these things for ever, so I think I'll stop there!

> **RTrev said:**
> Whoops, brake lights coming on here.Lol! This is a question of context. You see, all filesystems (with the possible exception of the small few with so-called "active" fragmentation management) inevitably fragment to some degree. Having said that, modern, well-designed filesystems are exceptionally good at preventing it from happening as a result of nothing more than normal use. They are also pretty good at minimising its adverse effects. Having said that, Linux's filesystems are in a completely different league than Microsoft's ones ... which is why many people say that Linux simply doesn't fragment. For instance, many Microsoft users swear that they simply *have* to defrag their disks on a two-weekly basis (or some such), and find themselves going to all sorts of lengths to get fragments out of their pagefiles; most Linux users however might not even be able to tell you the *name* of a defragmenter!

[SIZE=1]* kidders does a quick **apt-cache search defragment** to see what the story is.
[/SIZE]
... Would you believe that Ubuntu actually has one! (It only seems capable of defragmenting Ext2 (unjournalised Ext3) though. Seriously though, I wouldn't ever suggest that any Linux user try to use one. The main reason I mentioned fragmentation is that the traditional Linux user's goal (in theory) is to install their OS once, and hold onto it until the end of time itself. The albeit teeny, tiny amounts of fragmentation can still add up over a few years.

> That's nasty.Ahhh... I see. For people who *like* to constantly try out new things, I would suggest setting up a separate /boot partition. It can live anywhere, but I would suggest putting it on the same disk as your Ubuntu system, since it would mostly only ever get used during boot-up. This will give you the freedom to mount your Grub configuration (assuming you're using Grub, rather than Lilo, etc.) into other (possibly experimental) operating systems, and play around with it, without risking damage to your core Ubuntu system. My /boot partitions (whenever I make them) are normally quite small (something of the order of tens of megabytes), and are Ext2, so there is never even the remotest possibility that an operating system won't be capable of reading it.

Anyhow, the reason for wanting to do this in the first place is so you can easily reinstall & reconfigure your bootloader to match the constantly changing contents of your box. Ubuntu, for instance, will happily overwrite Red Hat's bootloder without asking (which has always astounded me, because it's so un-Linux-like). Having some way of easily correcting something like that is very convenient.


---


Finally, there are two things I've left out that I thought I might mention. The first is to Google "noatime", and see what you come up with. It's a mount option (for /etc/fstab) that you can use to have your system forget the existence of last access timestamps. I haven't checked, but with luck, it'll lead you to some other clever ways of speeding up your disks.

The other (far more major) issue is your OS's bitness. If you have a 64-bit processor, by far the most sensible thing you can do to for performance is run a 64-bit OS, rather than forcing it to perpetually emulate non-native, 32-bit operation. As you no doubt know though, this leads you to all sorts of sticky issues that have to do with developers that don't write for 64-bit architectures. Although I've sorted *my* box out more or less properly in this respect, I can't honestly say doing so doesn't test the limits of my knowledge (and patience!) Perhaps this is something worth putting aside until you decide whether you even want to *use* Linux long term. :-)

> **RTrev said:**
> I can see myself winning over many converts from Windows when they whine about not being able to run program X, and I boot up XP in 8 seconds inside a VM and watch their jaws drop. ;-)Roflmao!!

> **RTrev said:**
> Much appreciated feedback!  Thank you!No problem. :-)

---

### Post by RTrev on 2007-06-17
I've printed out this entire thread, and will study it and work on it.  I'll tell you one thing.. the noatime and nodiratime made a **HUGE** difference here!  Clearly my bottleneck is the disk I/O at the moment, because I can't believe how much faster that one change made virtually everything.

Thanks again for all your help!  You should write a book.  :-)

Best,
Bob

---

### Post by kidders on 2007-06-18
> **RTrev said:**
> the noatime and nodiratime made a **HUGE** difference here!Wow... I wouldn't have expected that (bold type *and* block capitals hehe). It just goes to show, you never really know what the particular quirks of your own hardware are until you try a few things out.

If you feel that disk I/O is a problem (ie that your computer should really be finding it easier to do), it might be worth spending a few minutes double-checking that Ubuntu isn't doing something crazy driver-wise. For example, buried in my machine's **dmesg** are...```
$ dmesg|grep -i scsi
SCSI subsystem initialized
scsi0 : sata_nv [SIZE=1][COLOR=DarkRed][version 3.3, apparently][/COLOR][/SIZE]
scsi1 : sata_nv
...
...
scsi2 : sata_nv
scsi3 : sata_nv
```My motherboard's support site explicitly cites this driver as the most suitable for my hardware...```
$ lspci | grep '00:0e.0'
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
```Anyhow, glad I could help. :-)

---

### Post by RTrev on 2007-06-18
Good Morning.. or whatever time it is in your part of the world.  :)

> **kidders said:**
> Wow... I wouldn't have expected that (bold type *and* block capitals hehe). It just goes to show, you never really know what the particular quirks of your own hardware are until you try a few things out.

<chuckle>.. after years of trying performance tweaks, I tend toward exuberance and hyperbole when the tweak 1) doesn't break my system completely, and 2) makes a clearly perceptible difference.  This is very clear!

As an aside, I broke my system completely, twice, yesterday, trying other tweaks.  I should learn not to give every HOW-TO I find a try!

> 
If you feel that disk I/O is a problem (ie that your computer should really be finding it easier to do), it might be worth spending a few minutes double-checking that Ubuntu isn't doing something crazy driver-wise. 


Well, I don't know that it's doing something crazy,  and as I note below I have no way to find out what driver I should be using.

```

bob@ub64:~$ dmesg|grep -i scsi
[   35.402464] SCSI subsystem initialized
[   35.434204] scsi0 : sata_nv
[   35.923286] scsi1 : sata_nv
...

```

but then goes on to enumerate each drive as being accessed directly:

```

[   36.414991] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[   36.415589] scsi 1:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[   36.416687] scsi2 : sata_nv
[   36.905912] scsi3 : sata_nv
[   37.397622] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[   37.398230] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
...

```

> 
[/CODE]My motherboard's support site explicitly cites this driver as the most suitable for my hardware...```
$ lspci | grep '00:0e.0'
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)

```


And mine looks like this for the same command:

```

bob@ub64:~$ lspci | grep '00:0e.0'
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)

```

I'm having generic issues with hardware, am not sure how serious they are if at all, and have no way to get information.  You see, I went with TigerDirect for this purchase, and the board came with minimal written documentation and some CDs for Windows.. but we don't run Windows at all.  (As I got your note, I had installed an old copy of XP that my wife got with some machine she ordered once, and was about to try reading the disks under XP in VMware Server.)

The problem with this board, at least in my view, is that if I go to the site which makes the Phoenix Award WorkStation BIOS v6.00PG the site tells me I have to go to my vendor.  If I go to my vendor, there is no information about this board that I can find except that they sell it.  Maybe the really good deals at TG aren't quite as good as they appear if one ends up with no support.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2945301&Sku=MBM-MSNV-3800](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2945301&Sku=MBM-MSNV-3800)

I ran into another hardware related "issue" last night.. I just noticed that, having bought precisely the brand and type of memory Tiger Direct recommended for this board, DDR400, PC3200, my system is now registering a memory bus speed of 333 MHz rather than the previous 400 MHz when only two of the 1-G modules were installed.  Googling around, I see this happens to a lot of people.. they add more modules and then find that their board can't maintain the timing needed for 4 sticks.  I can raise the CAS to 3  and get back to 400 Mhz, but some people suggest it's better to have the 2.5 CAS than it is the increased Mhz.  Something else I have to study; the arcane <g> science of over-clocking.

Just as an aside, I tried using CAS 2, and my machine wouldn't even give me the BIOS screen.. so I had to open it up and find the CMOS CLEAR jumper to fix that.  :-)

My memory is now running 2.5-3-7-3 (2T timing)   whatever that actually means.

Sure wish I had a place to go and get information about the BIOS, etc.  Maybe there is such a place, and if anyone knows where it is I'd be very appreciative.

> 
Anyhow, glad I could help. :-)

Very much so!  :)  Thanks again!

---

### Post by kidders on 2007-06-18
> **RTrev said:**
> I have no way to find out what driver I should be using.I did some checking, and apparently yours is an nForce4 chipset ... the same as mine. Incidentally, the commands I posted (particularly the one with the PCI ID in it) weren't really intended to be typed on your own machine ... I was mostly interested in showing you the sort of language used in the output they generated ... the "grep"s were a way for me to chop out irrelevant information.

> **RTrev said:**
> I'm having generic issues with hardware, am not sure how serious they are if at all, and have no way to get information. Well, there's no harm in throwing a few of them at the forum, and seeing what happens. :-) Where to go for info can be difficult to figure out sometimes ... for instance, the manufacturer of your BIOS won't necessarily have much interest in helping you with issues that have more to do with your SATA chipset, and so on. Your CPU is by AMD, your chipset is by Nvidia, and the motherboard itself is by Machspeed.

In terms of your RAM issues, I note the following from your motherboard's support site...> DO NOT [SIZE=1][COLOR=DarkRed][they were quite emphatic hehe!][/COLOR][/SIZE] use three individual sticks of memory as it may cause failures. Please use either 1 piece, 2 pieces, or 4 pieces.They go on to give reasons why your maximum memory speed may drop...
> [LIST]
[*]Each memory slot is installed with double-sided memory
[*]Both DIMM1 and DIMM3 are installed with double-sided memory module (for motherboards with 4 DIMM sockets)[/LIST]You *could* probably bump your speed back up again by overclocking, I suppose ... but that should be done with caution.

Incidentally, they also say...> Due to resource usage by the South Bridge chipset, system memory may only detect up to 3.9 GB (not the full 4GB) when each DIMM is installed with a 1GB memory stick. To utilize a full 4GB of system memory, you will need to use 2x 2GB sticks of memory.> **RTrev said:**
> My memory is now running 2.5-3-7-3 (2T timing)   whatever that actually means.Afaik...
[SIZE=1][SIZE=2]2.5 - Your column access strobe latency
3 - The delay between "Row" and "Column" instructions sent by the CPU.
7 - The amount of time allowed for bank switching.
3 - Your row access strobe latency
[/SIZE][/SIZE]
I don't have a complete grasp of exactly how the various latencies impact Linux's performance, I'm afraid. :-( In general terms though ...[LIST]
[*]Much of the talk (especially from manufacturers) about low-latency RAM is hype.
[*]Not allowing your RAM enough time to perform operations (ie by shortening delays too much) will cause errors.
[*]The way to get best performance is normally (a) not to use all available DIMMs, and (b) when using multiple chips, they should always be identical.[/LIST]I doubt very much that you didn't know that already though, by the sound of things.

---

### Post by RTrev on 2007-06-18
> **kidders said:**
> I did some checking, and apparently yours is an nForce4 chipset ... the same as mine. Incidentally, the commands I posted (particularly the one with the PCI ID in it) weren't really intended to be typed on your own machine ... I was mostly interested in showing you the sort of language used in the output they generated ... the "grep"s were a way for me to chop out irrelevant information.


Right after I posted, of course, I realized that.  :)  

> 
Well, there's no harm in throwing a few of them at the forum, and seeing what happens. :-) Where to go for info can be difficult to figure out sometimes ... for instance, the manufacturer of your BIOS won't necessarily have much interest in helping you with issues that have more to do with your SATA chipset, and so on. Your CPU is by AMD, your chipset is by Nvidia, and the motherboard itself is by Machspeed.


I wonder if it was so wise to build my own machine, given issues like this.  Hmm.  But I love the machine, so I guess maybe I should stop being so anal about getting it all perfect.

> 
In terms of your RAM issues, I note the following from your motherboard's support site...They go on to give reasons why your maximum memory speed may drop...
You *could* probably bump your speed back up again by overclocking, I suppose ... but that should be done with caution.


Something weird is happening in creating this reply note.  Your note includes a section which mentions using two 2G rather than four 1G modules.  But when I go to reply, that part isn't here to quote.  Go figure.  Anyway, this is an area where their messages are contradictory, it seems.  The little booklet I got with the motherboard specifically says that each slot can accept a 128M, a 256M, a 512M, or a 1GB.  Period.  No allowance for using a 2G chip in any of the dimms.  And no, I'd never heard the part about it being best to not use all of the available memory slots.  This is the first machine I've ever had with more that 512K, and the others were purchased fully-built.. Dells and Gateways.  So I'm not very up to speed on this stuff.  (You may have noticed!  :-))  Combine that with trying to learn Linux at the same time, and I sense I'm in it up to my ears.  LOL!

I'm having a frustrating morning.  Got XP running in a virtual machine, then put in the CD that came with the motherboard/CPU combo.  On it are pdf files which are documentation for the motherboard and CPU.  I figured I'd just copy them to a USB drive and then store them on my real machine.  But for some reason, although it worked the other day, Windows can't see the USB drive.  Though I'd have to download Foxit in Windows to read the silly things.  Nothing is ever easy.  Then it dawned on me that I can read the CD just fine from Linux.  Good Lord.. two steps forward and one step back.  From looking at that CD it appears that they made it very easy for Windows users.  All the drivers, lots of docs, support drivers for the fakeRAID, and on and on.  They just assume everybody uses Windows.  I'm tempted to write and tell them the world has moved on and they'd better try to catch up.  :-)

---

### Post by kidders on 2007-06-18
> **RTrev said:**
> I wonder if it was so wise to build my own machine, given issues like this.  Hmm.  But I love the machine, so I guess maybe I should stop being so anal about getting it all perfect.Lol no... building machines is fun. I suppose absolutely *everything* will never be perfect, no matter how much thought you put into things, but you'll get pretty close, I'm sure. Personally, I like the sound of what you've got. :-)

> **RTrev said:**
> Something weird is happening in creating this reply note.My fault... sorry. The system drops anything marked as [KWOTE] (excuse the misspelling hehe), when replying. Anyhow, I imagine that the 2 Gig suggestion only applies to variants that support chips that size, but the problem (ie that you'll appear to be missing 100MiB of RAM) still remains, I suspect. Hardware manufacturers always do that sort of thing ... you know ... make something *seem* better, but not necessarily *be* better. So, you might imagine that 4 DIMMS are better than 2, right? [SIZE=1]Of course as it turns out, when you read the fine print, there can often be catches.[/SIZE]

Your SATA bus will probably suffer similarly if you overload it (to come full circle in our discussion!) These days, motherboard manufacturers are building in a lot of things that used to be exclusive to expensive servers ... RAID, space for lots of RAM and so on ... but corners always get cut, to keep the prices down.

It sounds like you're getting more and more frustrated by the minute! Then, of course (if you're anything like me), things start looking more complicated than they are, you stop thinking straight... :-x You poor thing!

The "if you have a computer at all, you must be using windoze" assumption is commonplace, I'm afraid. Thankfully, you probably don't need much of what those CDs you have offer MS users though ... RAID, SATA support, etc. has all been built into the standard Linux kernel for ages. :-)

---

### Post by RTrev on 2007-06-18
> **kidders said:**
> Lol no... building machines is fun. I suppose absolutely *everything* will never be perfect, no matter how much thought you put into things, but you'll get pretty close, I'm sure. Personally, I like the sound of what you've got. :-)


You're right.. I think I need to take a bit of a break.. starting to burn out!  :cry:

> 
My fault... sorry. The system drops anything marked as [KWOTE] (excuse the misspelling hehe), when replying. Anyhow, I imagine that the 2 Gig suggestion only applies to variants that support chips that size, but the problem (ie that you'll appear to be missing 100MiB of RAM) still remains, I suspect. Hardware manufacturers always do that sort of thing ... you know ... make something *seem* better, but not necessarily *be* better. So, you might imagine that 4 DIMMS are better than 2, right? [SIZE=1]Of course as it turns out, when you read the fine print, there can often be catches.[/SIZE]


LOL!  Yes, it's the fine print.  Should be illegal.  When I bought the motherboard, there was tiny fine print at the bottom which mentioned, oh, by the way, if you don't buy a CPU fan from us you'll void your CPU warranty.  Sheesh.  I bought one from them, it broke it's mount after three days, and I had to go and get a Zalman to replace it.

And I'd never even heard of "fakeRAID" until after the purchase.  I looked at the board and said "Oh wow, a RAID controller on board!"  Sigh...

> 
Your SATA bus will probably suffer similarly if you overload it (to come full circle in our discussion!) These days, motherboard manufacturers are building in a lot of things that used to be exclusive to expensive servers ... RAID, space for lots of RAM and so on ... but corners always get cut, to keep the prices down.


Yep.  Well, for $139 with the CPU I guess I shouldn't have been expecting it all to be top of the line stuff.  <g>

> 
It sounds like you're getting more and more frustrated by the minute! Then, of course (if you're anything like me), things start looking more complicated than they are, you stop thinking straight... :-x You poor thing!


LOL!  Yes, actually I've been struggling with this whole thing for so long now that I've almost forgotten why I wanted a computer in the first place.  My wife, kind soul, wanted me to have a nice computer to use, so she said she'd ordered me some extra RAM which should speed things up a bit.  She neglected to mention the motherboard, CPU, case, etc.  And now that I have all this stuff, I'm having a ball.. but also becoming overloaded on things to learn.  In my past life, I had a little Gateway with 512K, one who-knows-what-kind 80G drive, a big CRT, and an install of Ubuntu.  All was fine, because I'd never really thought about needing a super fast machine.  But now that I have the basics of a fast box, I'm compulsively trying to get everything running optimally, Every door I open, there are 16 more doors to choose from.  <g>

> 
The "if you have a computer at all, you must be using windoze" assumption is commonplace, I'm afraid. Thankfully, you probably don't need much of what those CDs you have offer MS users though ... RAID, SATA support, etc. has all been built into the standard Linux kernel for ages. :-)

Yeah, I gather, but I need to learn how to use all of that stuff, and my attempts so far have been spectacular failures.  What I want is a book with all the answers, in words of one syllable or less.  My attempt to set up the software RAID was a dismal failure, and that was the main thing I was psyched about trying with the two Raptors.  Got a link to anything that walks someone through setting that up, one simple step at a time?

Actually, looking at it from a more relaxed perspective, I've got a setup now that isn't half bad.  I've got Feisty on one of the Raptors, and Gutsy on the other, and both have access to the two big Caviar 500G drives.  I've created symbolic links to a directory on one of the big drives, so that no matter which OS I'm using at the moment, my news reader always has the current files and so on.  Both Feisty and Gutsy are running fine, solid, fast and clean.

Okay, time to take a deep breathe, and resign myself to learning one thing at a time.

I'd love to get those two Raptors running as RAID 0 just to see if it's faster.  And I need to experiment with the memory.  With CAS set to 3, I'm back to 400 Mhz.  With it set to 2.5 I'm at 333 Mhz.  Got to find some way to benchmark which is actually faster in the majority of cases.

Thanks for your patience and humor.. you've been more help that I can tell you!

---

### Post by kidders on 2007-06-18
Your wife sounds really great! (* Jealous)

> **RTrev said:**
> Every door I open, there are 16 more doors to choose from.  <g>I know the feeling! Of course, if you were using an MS operating system, half these decisions would have been made *for* you by the OS developers. So, the big question is whether that's a dream come true ... or a nightmare! Hehe.

> **RTrev said:**
> Thanks for your patience and humor.. you've been more help that I can tell you!No problem. :-) If you need someone to walk you through your RAID setup, I'd be happy to. I'm pretty available today anyhow, because (as luck would have it) I'm trying to to be on hand to help another poster rescue *his* RAID from the brink of oblivion.

---

### Post by RTrev on 2007-06-18
> **kidders said:**
> Your wife sounds really great! (* Jealous)

I know the feeling! Of course, if you were using an MS operating system, half these decisions would have been made *for* you by the OS developers. So, the big question is whether that's a dream come true ... or a nightmare! Hehe.

No problem. :-) If you need someone to walk you through your RAID setup, I'd be happy to. I'm pretty available today anyhow, because (as luck would have it) I'm trying to to be on hand to help another poster rescue *his* RAID from the brink of oblivion.

I appreciate that!  The only issue is that this is pretty much my only PC.. so once it goes down for the install we're pretty much out of touch.  OTOH, if things blow up, I'll stick in the live CD and try to get back here that way.  My wife's machine is working hard as she's coming up with a solution for a new customer (she's set up her own business and getting started..)

And we have a cat who's having kittens at the moment.  :-)  Life is complicated, isn't it?

If you could give me a good push in the right direction, I can probably take it from there?

Thanks!

---

### Post by kidders on 2007-06-18
Assuming you're going for "proper" software RAID, **mdadm** is the tool to use. You shouldn't need to take your machine down, or do any rebooting though ... unless of course you're planning on putting your OS on the RAID array, in which case, one quick reboot would be required at the end. Moving your OS around like that can be a little finicky though, so I won't go typing that out just yet hehe.

Anyhow, actually constructing the array is a one-liner (**sudo mdadm...**). After that, you can create a filesystem (**sudo mkfs...**) on it, mount it (**sudo mount...**), and you're done -- at least in theory!

If you want to put your OS on the array though, let me know ... that's a little more involved.

---

### Post by RTrev on 2007-06-18
> **kidders said:**
> Assuming you're going for "proper" software RAID, **mdadm** is the tool to use. You shouldn't need to take your machine down, or do any rebooting though ... unless of course you're planning on putting your OS on the RAID array, in which case, one quick reboot would be required at the end. Moving your OS around like that can be a little finicky though, so I won't go typing that out just yet hehe.

Anyhow, actually constructing the array is a one-liner (**sudo mdadm...**). After that, you can create a filesystem (**sudo mkfs...**) on it, mount it (**sudo mount...**), and you're done -- at least in theory!

If you want to put your OS on the array though, let me know ... that's a little more involved.

Well, yes.. the disks I want the RAID on are my current small system disks.  I don't mind doing a complete reinstall, though.  If I can just get the disks working in RAID, and the Ubuntu install routine sees the disk as a single RAID volume and can install to it, I'll be good to go I think?

---

### Post by kidders on 2007-06-18
Yep... you *should* be able to do it that way. My preferred approach (personally) would be to avoid reinstalling, and retain your current OS. Generally, I prefer not to reinstall an OS if there is any other practical way of achieving the same effect ... but maybe that's just me hehe. Roughly speaking, that would involve...
[LIST]
[*]Booting from a LiveCD
[*]Temporarily allocating a large chunk of disk space not earmarked for RAID.
[*]Tarballing your entire system into your temporary location.
[*]Running mdadm to create your RAID 0 array.
[*]Untarring your OS onto the array.
[*]Altering your /etc/fstab to reflect the new location of your root filesystem.
[*]Setting up a /boot partition & moving the contents of your existing /boot over there.
[*]Reinstalling your bootloader.
[*]Double-checking your bootloader configuration.
[*]Rebooting into your system.[/LIST]Unfortunately, since the disks that currently contain your OS are the ones you want to use for RAID, booting from a LiveCD is necessary. :-(

---

### Post by RTrev on 2007-06-18
> **kidders said:**
> Unfortunately, since the disks that currently contain your OS are the ones you want to use for RAID, booting from a LiveCD is necessary. :-(

Okay, I'm working from the live CD for most of this.. and I install mdadm, use it to create the RAID, I use both of the 74G drives in the RAID array.  Then I run the install routine on the Live CD, and when it comes to the partitioning part it should see a single 150G disk to install to.  Just do the normal install from there on out.  Actually, you'll laugh, but that sounds much easier to me that trying to copy and preserve and re-set-up the existing OS..  :-)

I'll report in when I'm done..   Not quite sure when that will be, given the chaos here at the house and my utter unfamiliarity with even basic mount commands.  See you on the other side!  Thanks again!!

---

### Post by RTrev on 2007-06-18
> **RTrev said:**
> I'll report in when I'm done..   Not quite sure when that will be, given the chaos here at the house and my utter unfamiliarity with even basic mount commands.  See you on the other side!  Thanks again!!

I'm on the live CD.. things have gone all haywire.  I've now got one of my Raptors with no disk label, and it's mounted read-only, and gParted keeps yelling at me that I shouldn't be doing this unless I REALLY know what I'm doing.  :-)

For some reason I don't have an unmount command, and can't get it from the repos.  

mdadm keeps throwing errors at me, telling me one of the disks is already part of a RAID, probably as a result of some misguided command I issued before.

Having fun though.  Just hope I haven't somehow wrecked my Raptor.

The enemy is closing in.. this may be my last transm.........

---

### Post by RTrev on 2007-06-18
> **RTrev said:**
> I'm on the live CD.. things have gone all haywire.  I've now got one of my Raptors with no disk label, and it's mounted read-only, and gParted keeps yelling at me that I shouldn't be doing this unless I REALLY know what I'm doing.  :-)

For some reason I don't have an unmount command, and can't get it from the repos.  

mdadm keeps throwing errors at me, telling me one of the disks is already part of a RAID, probably as a result of some misguided command I issued before.

Having fun though.  Just hope I haven't somehow wrecked my Raptor.

The enemy is closing in.. this may be my last transm.........

--//--

Addendum.. I got the drive sorted.. turned out it was mounted read-only for some reason.

Got the raid set up.  Installed, booted, installed mdadm, and at that point some updates were announced.  Got those, rebooted.. and no boot.  Booted in maint mode, and saw that the RAID thing was working.. it compared the two disks, found them identical, etc.  Then it came time to load the CDROM drivers, and the machine just hangs there.  Never gets booted at all.  I think I'm real close.. so close I can taste it.  :)  But the elusive fruit is still too high.  What did I do wrong??

---

### Post by kidders on 2007-06-19
Crap... sorry... I had to go to bed. :-(

Seems like you made good progress in two hours! Are you still having problems?

---

### Post by RTrev on 2007-06-19
> **kidders said:**
> Crap... sorry... I had to go to bed. :-(

Seems like you made good progress in two hours! Are you still having problems?

Well, let's put it this way.. I'm still working on it and it's 4:30 in the morning here.  :)

I don't see a problem, but there certainly is one.  I even verified that the RAID was checking itself and proclaiming itself clean, but the boot just hangs right after I see the lines about the DVD or CDROM.  

I even went so far as to try the alternate CD which helps walk you through the install.. and that went fine until it wasn't able to install GRUB anywhere.

I figure what I should do is create a raid with a couple of partitions which aren't involved in the boot process.. and do my testing that way.  If it's significantly faster then I'll dig deeper into the boot mystery.. and either way I will have answered my question.

Right now I'm just reinstalling the non-raid way, after having decided I couldn't think about it any more.  <g>  This routine install stuff is rote for me now.. mindless work.  Just setting things up the way I like them.

---

### Post by kidders on 2007-06-19
[LEFT]Hmm...

Yeah, I tend not to like to try to boot off RAID either ... too much trouble. Generally, it's not a good idea to put your bootloader on disks involved in RAID either. Could one of these be the source of your problem?
[/LEFT]

---

### Post by RTrev on 2007-06-19
> **kidders said:**
> [LEFT]Hmm...

Yeah, I tend not to like to try to boot off RAID either ... too much trouble. Generally, it's not a good idea to put your bootloader on disks involved in RAID either. Could one of these be the source of your problem?
[/LEFT]

I'm sure.  What I did was boot the normal Live CD, get to a root terminal, and then set up the drives for RAID.  Then I apt-got <g> mdadm and let it set them up and it was fine.  I then simply proceeded to run the normal installer and let it have all of the first disk in my RAID set.  The installer doesn't give an option for /dev/md0 so I'd read that just using the first drive works.

Once it was installed and booted up on the hard drive, I apt-got mdadm again and let it do the same thing on the hard drives.  Seemed to work fine, and I couldn't think of any reason why a boot shouldn't work provided the RAID was up and running early in the boot.. which it was.  And it got quite a ways into the boot before it simply hung.

Obviously this isn't the correct way to do it.

I'm thinking now that I will simply use the fist disk as / and the second as /home.  Maybe put a few small swap files somewhere, and the /var on the second disk since it's getting written to constantly.

How would that sound?

---

### Post by kidders on 2007-06-25
Oh crap... did I ignore your questions here, or did I maybe PM you or something? I can't remember whether this thread is resolved! :-/

---

### Post by RTrev on 2007-06-25
> **kidders said:**
> Oh crap... did I ignore your questions here, or did I maybe PM you or something? I can't remember whether this thread is resolved! :-/

LOL.. you don't personally have to solve *all* of my issues.  :-)

I finally back-shelved the whole notion and moved on to other areas.. like a lighter-weight desktop.  I did a minimal install of xfce4, and I think it's going to work out great for me.  Just been a day or so, so still working out the kinks.  RAID 0 really sounded fun, but for a machine being run by a noob, it probably ain't the best idea in the world.  I'm bound to blow it up and need to go in and fix things from time to time.  Maybe I'll run like it is for a while, and then can revisit the idea of RAID if I'm happy with the new desktop.

Thanks for remembering!

Bob  :)

---

### Post by kidders on 2007-06-25
> **RTrev said:**
> Thanks for remembering!... so sorry for forgetting you!! Somehow or other, you managed to find your way *off* my list of posts, and your thread got lost in my subscription list. :-(

Anyhow, your plan sounds good... Linux doesn't mind having RAID & other things shoved on it as time goes by, so you don't have to do *everything* the way you want it right from day one. :-) If you feel like experimenting in a few weeks, may I suggest setting up a small RAID array (ie maybe a few tens of megabytes), just for the sake of playing with it. After a while, creation, destruction, rescuing, etc. should start to seem simple to you, and you're off!

Also, don't forget that fiddling with RAID arrays don't have to involve messing around with your partition table (which, after all, isn't exactly the safest pass-time in the world). Just like pagefiles in Windows, Linux will happily let you embed filesystems inside each other. (Think ISO images.) Your experimental RAID array need be no more than a pair of oversized files in your home directory.

---

### Post by RTrev on 2007-06-25
> **kidders said:**
> ... so sorry for forgetting you!! Somehow or other, you managed to find your way *off* my list of posts, and your thread got lost in my subscription list. :-(


Not a problem!  Sounds like you're busy helping a *lot* of people.  :)

> 
Anyhow, your plan sounds good... Linux doesn't mind having RAID & other things shoved on it as time goes by, so you don't have to do *everything* the way you want it right from day one. :-) If you feel like experimenting in a few weeks, may I suggest setting up a small RAID array (ie maybe a few tens of megabytes), just for the sake of playing with it. After a while, creation, destruction, rescuing, etc. should start to seem simple to you, and you're off!


That's something I eventually realized.  And yes, when things settle down a bit, I'll resize a couple of partitions and create a RAID to play with.  I'll just take it slow and see what happens.  It occurred to me that perhaps my boot problem was because the RAID had just been created and had'nt had time to fully sync up yet.  I'll experiment some.

> 
Also, don't forget that fiddling with RAID arrays don't have to involve messing around with your partition table (which, after all, isn't exactly the safest pass-time in the world). Just like pagefiles in Windows, Linux will happily let you embed filesystems inside each other. (Think ISO images.) Your experimental RAID array need be no more than a pair of oversized files in your home directory.

Hey, I hadn't even thought of that.  I keep forgetting how file-oriented Linux is.  Everything seems to be a file system to Linux.  I'm going to try storing my resume on one of my cooling fans and see what happens.  :-)

Thanks a lot for all your help and guidance.. it's much appreciated!

Best,
Bob

---

### Post by kidders on 2007-06-26
> **RTrev said:**
> I'm going to try storing my resume on one of my cooling fans and see what happens.  :-)Lol!

> **RTrev said:**
> I keep forgetting how file-oriented Linux is.Yep! For instance, /proc & /sys don't physically exist, neither does /dev, on some systems, /tmp might be in your RAM (for speed) ... they're all just filesystem-like implementations of other things. Having an OS that works that way is very handy. Perhaps the biggest advantage of treating everything like files (other than convenience) is access control.

Anyhow, glad I could help a little. :-)

---

