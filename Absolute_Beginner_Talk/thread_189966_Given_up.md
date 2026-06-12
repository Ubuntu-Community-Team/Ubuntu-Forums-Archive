---
title: "Given up"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by MoiraA on 2006-06-05
I must be the most useless person to try ubuntu in the history of the software, I think :(  After not getting very far here:

[http://ubuntuforums.org/showthread.php?p=1092006#post1092006](http://ubuntuforums.org/showthread.php?p=1092006#post1092006)

I made a CD with the latest dapper release on and tried it tonight in my laptop.  Maybe it just doesn't have the minimum requirements.  At any rate, it got to a point early on when I was just getting a nonsensical message repeated over and over so I gave up.  As I also have dual boot vista/xp issues on another machine right now, I think I'll just keep suse for the moment - maybe have another go at some future time!

I'd be interested to know if anyone can tell my why I got this message though:

> [b]IRQ 15: nobody cared (try booting with the "irqpoll" option)

handlers [<c0252040>] (ide_intr + 0x0/0x200)

Disabled IRQ #15[/b]

Nobody cared ??? :confused:  I might have got the odd character of the middle line wrong, but the rest is accurate.

---

### Post by rado_london on 2006-06-05
I thinks the devs are joking. Did you try to include irqpoll option in the grub entry for the kernel you try to boot? Thats what it basically suggests.

---

### Post by Vati-Khan on 2006-06-05
IRQ 15 usually is the second IDE controller, could explain why the  installation stopped ;-)

what chipset are you using 

try resetting to bios defaults

---

### Post by johnc4510 on 2006-06-05
Why not download Breezy and then upgrade to Dapper. Here is the web site:
[http://www.ubuntu.com/download_new?highlight=%28Breezy%29%7C%28iso%29](http://www.ubuntu.com/download_new?highlight=%28Breezy%29%7C%28iso%29)

---

### Post by MoiraA on 2006-06-06
[QUOTE=rado_london]Did you try to include irqpoll option in the grub entry for the kernel you try to boot? Thats what it basically suggests.[/QUOTE]

:???: I wouldn't know where to start.

All I did was stick the CD in the drive, I sort of assumed that would be enough to get it started.  I'm wondering if it would install better from an unzipped download, this is an old laptop and once or twice in the past I've had issues with the CDRW not reading a disc made on my much faster DVD RW here.  Commercial CDs seem to be OK.  Yes, I could reset BIOS defaults, but I don't think they were ever tampered with in the first place, and the BIOS is very limited, ie there isn't much to set.  Also, it works just fine and this was to be a second partition with XP running too - so I don't want to break something that is working as it is.

The laptop's a 750 mhz celeron processor with something like 192MB RAM of which 8 MB is used for graphics.  It has a 10 GB hard disk, currently split in two, running  xp lite and suse 9.  Obviously it's not fast, but it does run these two operating systems quite adequately and I'd hoped it would run ubuntu.  It probably would if I could get it to install - do you think an install over the network would be worth trying?  

If not, I'll give the link johnc4510 suggests a go.

---

### Post by IYY on 2006-06-06
Try burning the CD again, maybe, at a slower speed.

---

### Post by MoiraA on 2006-06-06
Good idea - I'll do that.  I also realise how daft my suggestion to "install over the network" was - this is an operating system not a program, fgs!

Thanks for the ideas.

---

### Post by rado_london on 2006-06-06
You can install OS on the network as well.

---

### Post by u.b.u.n.t.u on 2006-06-06
Linux has a lot of humor built into it, kinda like Easter Eggs. Like Bash (Bourne Again SHell).

My favourite is thinking an operating system that requires 3 to 4 times as many resources to run is a real future competitor *Vista* :P

=D> :grin:

---

### Post by rado_london on 2006-06-06
[QUOTE=u.b.u.n.t.u]Linux has a lot of humor built into it, kinda like Easter Eggs. Like Bash (Bourne Again SHell).

My favourite is thinking an operating system that requires 3 to4 times as many resources to run is a real furture competitor *Vista* :P

=D> :grin:[/QUOTE]
=D> =D> =D>

---

### Post by uzi09 on 2006-06-06
[QUOTE=u.b.u.n.t.u]Linux has a lot of humor built into it, kinda like Easter Eggs<...>[/QUOTE]

i like this one :D:
```

apt-get moo

```

---

### Post by MoiraA on 2006-06-18
[QUOTE=rado_london]You can install OS on the network as well.[/QUOTE]

You can?

I hadn't really thought of that.  I've made another CD, burned at a slower speed but I just haven't had enough time to attempt another reinstall.  It's not like it's critical, Suse works.

If this CD doesn't install then I'll unpack the iso file onto this PC and run setup from there.  I presume I'm going to have to mount the image with daemon tools etc if I go down that road?

[quote=u.b.u.n.t.u]My favourite is thinking an operating system that requires 3 to 4 times as many resources to run is a real future competitor *Vista* :P[/quote]

Except that PCs with scarce resources seem to be a thing of the past.  If you've got a 250 GB hard drive it doesn't really matter if the OS you install uses about 15 BG.  What irritates me about Vista though, is how you're going to need a 3D graphics card to get the full benefits of it.  People buying computers a year from now are not going to be able to experience the full visual effects of Vista!  I refuse to buy a separate graphics card just to run an operating system when the rather better-than-default onboard graphics here are perfectly adequate for everything else I do.

---

### Post by rado_london on 2006-06-19
[QUOTE=MoiraA]You can?
[/QUOTE]
Yes you can at least debian can but it needs some sort of special netinstall cd. I aint sure for Ubuntu and what is the exactly way to install via the net though.

---

### Post by MoiraA on 2006-06-20
Ah OK ... I'll try the slower CD first anyway - might have a go tomorrow night.

---

### Post by BugenhagenXIII on 2006-06-20
I did a network install of Breezy on my laptop because the cd drive does not work at all.  If your other pc is Windows, like mine was, use [this]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") how-to (It's aimed at Breezy, but I assume that as long as there's a netboot image for Dapper, it should be the same).  If your other pc is Linux, I'm sure there's another how-to somewhere.

---

### Post by MoiraA on 2006-06-22
I'm beginning to regret ever deciding to do this :( the slow burn CD was no better, producing that stupid "nobody cares" message, so a network install looks the only option.  I started to read that how to ..... why is it that the most horribly complicated instructions always start with "This is a very easy method" making me feel even more useless as I struggle to understand them?

I downloaded the breezy netboot kit (thinking I could always upgrade later from that installation) and made the necessary changes to the Tftpd32.exe file.  This is on my main computer, not the laptop.  Clicking OK, I'm supposed to tell the target computer to "request a PXE boot ROM".  How?  Nothing happens.  Another point which confused me - it tells you to copy 3 files but then asks you to paste them in exactly the same location :confused:

It's no wonder most people give up on linux very quickly - it just isn't user friendly at all and there's not much incentive to change from windows when you meet all these sort of obstacles at the very first hurdle.  I might be better portioning off a section of one of the hard drives here and trying ubuntu (or buying a new laptop).

---

### Post by bocmaxima on 2006-06-22
[QUOTE=MoiraA]I'm beginning to regret ever deciding to do this :( the slow burn CD was no better, producing that stupid "nobody cares" message, so a network install looks the only option.  I started to read that how to ..... why is it that the most horribly complicated instructions always start with "This is a very easy method" making me feel even more useless as I struggle to understand them?

It's no wonder most people give up on linux very quickly - it just isn't user friendly at all and there's not much incentive to change from windows when you meet all these sort of obstacles at the very first hurdle.  I might be better portioning off a section of one of the hard drives here and trying ubuntu (or buying a new laptop).[/QUOTE]


This might not matter, but when you downloaded the .iso image, did you check the md5sum to make sure it wasnt corrupt? After that, when the CD boots up, Verify the disc. I didnt do that, twice, and I got all kinds of crazy errors. Try  this tutorial: [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) and I ended up having to burn it at 2x. It might not be the problem, but if not you can add the irqpoll option to the startup.

I almost quit before it was installed too...but then I remembered putting windows 95 on my friends machine, and setting up hardware through DOS...and windows 98. Also earlier in the day, I had to do a reformat of my GFs computer, and just getting it back to operational took me almost 6 hours (downloading updates and software that you use on a daily basis), so I figured, if I cant get it up and running in 6 hours, I'll go back to XP. I should at least give it as much time as I am accustomed to in windows. Not even 2 hours later I am up and running. Not even 48 hours later and I have my computer functioning at 90% of what my Windows box did, but I installed a different Kernel and tweaked a bunch of things.

---

### Post by MoiraA on 2006-06-22
The thing is, I first of all used an iso image from a magazine, which was giving away copies of breezy and when that didn't work, I downloaded dapper.  I could  download it again and try burning a different image - that might be an idea, but having had a go with two different copies I'm sceptical that a new iso image is going to solve the problem.

The other thing I could do is to download the image onto the laptop and actually make the cd using the laptop cd drive.  That way it might make a copy of something it will actually read.

It's an idea and certainly easier than mastering the art of a network install :) I'll give it a go.

---

### Post by bocmaxima on 2006-06-22
[QUOTE=MoiraA]The thing is, I first of all used an iso image from a magazine, which was giving away copies of breezy and when that didn't work, I downloaded dapper.  I could  download it again and try burning a different image - that might be an idea, but having had a go with two different copies I'm sceptical that a new iso image is going to solve the problem.

The other thing I could do is to download the image onto the laptop and actually make the cd using the laptop cd drive.  That way it might make a copy of something it will actually read.

It's an idea and certainly easier than mastering the art of a network install :) I'll give it a go.[/QUOTE]


Try verifying your current dapper disc. If not, when it boots up, hit f6 and add the irqpoll option to the boot. I am not sure where in the line you add it, but throwing commands into a liveCD definately wont hurt anything.

---

### Post by Graybeard on 2006-06-22
Me too. Ubuntu for me is now tucked away in a few spare gigabytes but I've tired of banging my head against all the innovations. 

I didn't, and don't, like the MS attitude that since they control the vast majority of desktops they can wring more bucks out of folks. But I can't do without GIS so I had to compromise with a dual boot machine, and chose Xandros. That was two years ago. It worked, and it was familiar enough that the learning curve was gentle. 

But Xandros users who are not hackers are locked into versions of linux apps that they have tweaked to run under Xandros. Despite all the hype, Open Office 1.x was never a serious competitor to Word. It was every bit as bloated but less competent. And 2.x is still not available for Xandros. 

That's one example of many just like it. So hearing good things about Ubuntu I tried a live CD. I was impressed. So I installed it.  Alas, the deeper I got into it the less impressed I was. True, more up-to-date versions of debian software installed easily. But while Windows, Xandros, and even Ubuntu-live, center properly on my monitor, Ubuntu installed doesn't. And the monitor adjustments can correct only half the error. 

No, don't tell me how to get under the hood and fix it. That would have been acceptable, but wasn't necessary, in the CPM days. It's still much of the fun for those who make a hobby out of it. I don't. Nor do the vast majority of current computer users. I stopped working on my own car when I sold my '52 MG TD and stopped working on my own computer when I upgraded to 16-bit computers. 

The screen problem was only the beginning. Sometimes it can't find my mouse. Sometimes it can. Sometimes it can't find my ethernet. Sometimes it can. And the file manager is a farce compared to Xandros' file manager. For me (I won't speak for others) a file manager is among the top three most frequently used apps. Total time is near the bottom but frequency is near the top. 
Ubuntu's is a constant reminder of how convenient a file manager ***can*** be by denying all that convenience. 

This is getting too long. IMHO, if Ubuntu is going to still be around in five years it will be because they gained more respect for intelligent users who don't happen to share their fascination and just want a good tool with which to do their work. End of rant.

---

### Post by MoiraA on 2006-06-23
[quote=bocmaxina]if not, when it boots up, hit f6 and add the irqpoll option to the boot. I am not sure where in the line you add it, but throwing commands into a liveCD definately wont hurt anything.[/quote]

I don't suppose you can elaborate on that at all?  I just tried yet another CD - this is my 4th.  It gives me the same "nobody cared" message, which is starting to feel a bit depressing.  I can't believe every CD has been corrupt or my laptop has failed to read each one, and it would certainly have read a CD burnt on the same CD ROM.  It recognises the Ubuntu CD all right, it just gets as far as booting the kernel or something, then won't go any further.

"Throwing commands into a live CD" may not do any harm, but unless I have some idea of what I'm doing then it's almost certainly not going to do any good either.  This is probably the last thing I can try as the network install just doesn't work. 

Can I just check something basic?  All I need to do is boot from the CD, right?  I don't need to have a ready formatted partition to install Ubuntu on before I start?  Ubuntu will format the necessary hard drive space, won't it?  I'm just trying to install it the way I would XP, ie putting the CD in the drive and booting from it.

---

### Post by Ndlovu on 2006-07-18
MoirA, the problem here has nothing to do with the CD you are using - it's an issue that Ubuntu seems to have with shared interrupts (IRQs) on some computers.

It seems that most people are able to get around this: At the boot options menu, press "F6" on your keyboard to get to other options. It will then present you with the current boot string, which contains the default boot options. You will need to add "irqpoll routeirq" (withouth the quotes) after the existing string (I think I added these options after "--").

This *should* get your system up and running. It's not a complete fix, however. You might find that you have strange issues later with some other device. For example, I can access my CD-ROM drive to get data, but I can't seem to rip a CD.

---

### Post by PriceChild on 2006-07-18
Have you tried maybe using the alternate cd?

> **u.b.u.n.t.u said:**
> Linux has a lot of humor built into it, kinda like Easter Eggs. Like Bash (Bourne Again SHell).

My favourite is thinking an operating system that requires 3 to 4 times as many resources to run is a real future competitor *Vista* :P

=D> :grin:

of course there's also the...

```
apt-get moo
```

---

### Post by PingunZ on 2006-07-18
Reset CMOS

---

### Post by MoiraA on 2006-07-18
Ndlovu, thanks for the suggestion, particularly after all this time :)

I will certainly try what you suggest - it will have to wait for a week as I am off on holiday tomorrow and haven't even started packing :( PingunZ, resetting the CMOS on the laptop would be quite hard, wouldn't it?  And I have tried many different CDs, different downloads, different versions etc - they all do the same thing. I will first of all see if pressing F6 and adding irqpoll routeirq after the current boot string it presents me with, solves the problem anyway.

To a certain extent, it doesn't matter if not everything works, as this is just an old laptop, I have two other main desktop PCs so if I couldn't rip a CD it wouldn't be a tragedy, for instance.  In any case, it dual boots with XP, so I can always boot into that when all else fails.

Thanks again!  I will let you know the result next week :KS

---

### Post by Skia_42 on 2006-07-18
Just stick with it, be patient and it'll work. Remember:
[IMG]http://images.google.com/images?q=tbn:ajFJ35L_avzY7M:http://www.worldbestwebsites.com/images/nevergiveuplookingforawinwin.jpg[/IMG]

---

### Post by kinematic on 2006-07-18
> **u.b.u.n.t.u said:**
> Linux has a lot of humor built into it .


like typing "apropos women" in the terminal ;)

---

### Post by MoiraA on 2006-08-02
Hooray!! :) Ndlovu you are a genius! That worked and ubuntu is nicely installing.  However, I have hit one snag.  It dual boots with XP because I need visual studio and Office etc on the laptop, and I've got to the stage where it asks me to choose where to install ubuntu, "prepare mount points".  The screen says:

"Select which partition you want to use for your new installation and where you want to mount each of them".

Each of them?  I only want one install.

"You must mount one partition of the root file system ("/) and you must choose at least one partition as swap space."

It lists 3 mount points.  Remember this is just a 10 gig hdd and I'm not that keen to format the xp partition and have to reinstall windows too.  The choices I'm presented with are:

/media/hda1 which is shown as a 5 gig primary partition
/home which is shown as a 5 gig primary partition, in fact exactly the same
and / which is apparently 4 gig shown as partition 6 on hda6 and a logical drive.

That adds up to 14 GB.  I really don't get it, and selecting the bottom two options doesn't advance the install anyway.  It says "a partition is assigned to more than one mount point".

Should I run the XP installation disc and use it to format the linux partition as empty space, hoping ubuntu will choose to install to that?  For the moment I'm stuck, which is a pity as for the first time since I tried ubuntu, I thought I was really getting somewhere :(

---

### Post by MoiraA on 2006-08-02
Oh for goodness sake.  Accidentally posting this twice, there should be the option to delete it, but I can't find it - sorry!

---

### Post by darrenm on 2006-08-02
> **MoiraA said:**
> Oh for goodness sake.  Accidentally posting this twice, there should be the option to delete it, but I can't find it - sorry!

Firstly, dude calm down! Its only a computer ;)

Secondly, I know it doesn't make any odds to you but the IRQ thing is a problem with your laptop, not Ubuntu. The laptop will not be 100% standards compliant with the BIOS or have a slightly dodgy southbridge or have a weird ACPI implementation that XP and Suse have been able to ignore or circumvent.

The partitions thing is a suggestion, there should be an option to change the default suggestion and go with your own choices. You need at least 2 partitions as it says, 1 partition to be your main filesystem (like C:\) and 1 partition as a swap partition (like the windows swapfile).

The swap partition is generally accepted best as twice your physical memory so if you have 128MB then set it to 256MB then use the remaining space available for your / partition.

If you have no space on the drive as the whole drive is taken up by Windows then you will have to resize the NTFS partition. Im sure Ubuntu let me do this without formatting it but I may be wrong, its been a while.

I think its stretching it a bit far to say no wonder people give up on linux quickly, the problems you are having are related to your hardware. The phrase it gives you "nobody cared" is perhaps not the best choice of words from the kernel developers but its basically saying it was polling for a driver to work IRQ15 and nothing stepped up, as I say maybe to do with a nonstandard PCI DEV ID or something. I've had far more problems getting Windows installs to work than Linux installs but thats just my experience. Also you say you are just trying to install it the same way you would install Windows XP but would you expect Windows XP to install side by side with another operating system on a hard disk that was already 100% partitioned?

No malice intended mate, I just think you've got the blinkers on a little bit.

---

### Post by MoiraA on 2006-08-02
No, no - I have got this IRQ thing sussed now, thanks to Ndlovu!  What I expected Ubuntu to do was install on the Suse partition, giving me the option to format it.  Like the way Vista has just installed on a spare partition on a spare drive on another PC.  I didn't have to remove XP just to do that!  It basically showed me the partitions and offered me the chance to install Vista on to the partition of my choice.  I opted to format the I drive and install Vista on it, which went ahead without problems.

Plenty of problems once I actually got Vista installed and I wonder why I swapped the official beta2 version from MS for their latest build which won't activate, nor will it run the Biostar fan control, but that's irrelevant here, except that it's adding to the general annoyance I'm feeling :(

Regarding the choice of where to put Ubuntu, I selected two partitions like it said, but it didn't seem to like them.  If I selected the first partition, I'm afraid of overwriting XP.  I also don't understand the message "a partition is assigned to more than one mount point" and why is it showing space of 14GB on a 10 GB hard drive?

Maybe it's not showing the NTFS partition at all and I can select the first choice (/media/hda1).  I don't know.  Or maybe I should format the Suse partition completely and hope Ubuntu will intelligently opt for the largest area of free space to install on?

---

### Post by MoiraA on 2006-08-02
Now I seem to have lost the ability to post on a forum :confused: 

I'm sure I'm submitting this post once, but I get a message to say at least 20 seconds has to elapse, so I wait and then post again.  I then find the post duplicated.

I think I might call it a night :(

---

### Post by moshuptrail on 2006-08-02
I went back to your earlier post on HD topology:


[PHP]/media/hda1 which is shown as a 5 gig primary partition
/home which is shown as a 5 gig primary partition, in fact exactly the same
and / which is apparently 4 gig shown as partition 6 on hda6 and a logical drive.

That adds up to 14 GB. I really don't get it, and selecting the bottom two options doesn't advance the install anyway. It says "a partition is assigned to more than one mount point".[/PHP]

I'd guess that hda1 is your Windows partition and /home has been mapped to it as well.  That would explain the later message about one partition and two mount points.

So / on hda6 must be the linux partition.  Not sure what became of all the partition numbers in between.  You might want to run GParted and see how the disk and partitions are laid out.  I would not be surprised to find there's a small partition for re-installing Windows that is not active.

---

### Post by MoiraA on 2006-08-06
Well, I had a look through Partition Magic at the various partitions on the laptop.  There was the Windows partition, the Linux one, the Linux swap space and some unallocated space (irritating as I could do with all the MBs I can get). One of the partitions just seemed to be called "extended" - even all this only totalled 5, so I'm not sure where hda6 came from.

For the moment I've just been exploring ubuntu from the live CD.  So far, I like it.  Everything just seems to work.  It's not acceptable as a long term solution because the old laptop with a slow processor and a slow CD-RW means most things take ages to load, but I can see my windows network, firefox is there and accesses the internet, OpenOffice loads, etc etc.  I can even have email download.

I have a feeling I may have to just delete the linux partition (partition magic may not do this as it's a windows program) to get ubuntu to properly install.  Hopefully by default it will then just pick the largest unused space.

As a last resort I could format the entire hard drive, but I don't want to particularly reinstall windows if I can help it.  I'll let you know how things go, but ubuntu looks good up to now :)

---

### Post by MoiraA on 2006-08-09
I have just also looked at my partitions with Disk Management in Explorer.

I seem to have 3.  One is XP, fair enough.  The next has a sort of blue oblong next to the volume at the top of  disk management, and the actual partition is 353MB, described as Healthy (Unknown Partition).  I accept unknown is the linux format, but I thought I'd carved my hard disk into two?  The last partition is described exactly the same, but is larger, obviously containing Suse at the moment.

Even adding all these up, there is some space missing.  Around 500MB is unaccounted for, which would be really useful on such a small hard drive.

Tomorrow, when I've a day off work, I'm going to get Ubuntu installed somehow, even if it means formatting the disk.  I'd rather not interfere with Windows though.  The small partition has lines across it, looking like it contains the linux page file as previously mentioned. Is it necessary for these to remain as separate partitions or can I safely try to delete them and use the combined space for Ubuntu?

From what I remember, I gave over 4 gig to Suse and 6 for XP.  It appears to be the XP partition which has lost all this space.

---

### Post by richbarna on 2006-08-09
Hi Moira,

You can keep xp at the beginning and delete all the other partitions for ubuntu.

Put your ubuntu live cd in the pc and boot up. Whenit's running, don't go through the install, instead go to System/ Administration/ Gnome partition editor (Gparted) and do the partitioning first.

Leave xp on the first partition, create 3 more partitions, Right to left - SWAP 512Mb, Root/Boot partition 5.48 Gb. That's your 6 Gb used. You don't need a home partition, just use the root partition for everyhthing as you only have 6 Gb total, otherwise you will end up with 2.5 Gb Root, 3 Gb Home and 512 Mb SWAP. (you can do it that way if you want though, as you can have 4 Primary partitions on the same drive.

Do the install, usual stuff, make sure you install GRUB on Hda1/Hdc1 (the windows partition and you should be all up and running :)

Good luck

---

### Post by Ndlovu on 2006-08-10
MoiraA, I'm no expert on partitioning, but there is a bit of logic to it that might help you make sense of what's going on. Reading a couple of articles might help you understand the process. These two might help, but there may be other better resources out there (I couldn't find much useful on the Ubuntu websites):

[http://linuxplanet.com/linuxplanet/tutorials/4232/1/](http://linuxplanet.com/linuxplanet/tutorials/4232/1/)   (Introductory)
[http://twiki.iwethey.org/twiki/bin/view/Main/NixPartitioning](http://twiki.iwethey.org/twiki/bin/view/Main/NixPartitioning)    (Complicated)

The second page goes into way more detail than you really need, and in your case I wouldn't suggest using different partitions for different parts of the linux file system. It may give you good background information though.

I suspect that in your case the "extra" partition is the swap partition that linux uses. When the programs and data in memory are larger than the actual RAM that you have in your computer, this space is used for virtual memory - more or less the same as your RAM, but a lot slower. Probably it was created automatically when you installed SuSE previously.

The Ubuntu partition manager should be able to identify the correct partitions to use and I'd stick with what's there already if at all possible. I would guess that Windows is probably installed on partition hda1 - the first partition of your primary master drive. Then the smaller of the other two partitions should be the swap partition, and the larger one should be where SuSE is sitting. Windows partition format is NTFS (or possibly FAT), and the linux partition would probably be formatted as EXT3 or something similar. The other partition should be automatically identified as swap space. The partitioning tool would probably tell you the type of partition, so try to use that to identify what's going on (ie NTFS = Windows partition; EXT3 = SuSE; small partition = swap). You should be able to resize the partitions to a more useful size if necessary, but it's a good idea to defragment your windows partition first.

I have to say that I haven't installed too many dual-boot systems, so use this advice if it seems to match what you're seeing, and otherwise use your own intuition on the subject.

---

### Post by MoiraA on 2006-08-10
Many thanks for the advice!  I'm currently trying to install Ubuntu again, having deleted the linux partitions with Gparted.  I created a swap space and left the rest for the Ubuntu OS.  It didn't quite go right to left as suggested, but I don't suppose that matters.  I couldn't recover the 7MB of unallocated space either, and god knows what happened to partitions 3 and 4.  There was some space called "reiserfs" :confused: sorry, haven't had time to read the partitioning articles yet, this is probably explained there.

I'm annoyed that half a GB seems to have disappeared from my already small XP partition.  In fact, before doing this I decided to backup and uninstall all the hotfixes and SP2 uninstall files, this has created quite a bit of extra space, but there's still only really just enough free to allow the pagefile to operate efficiently.  It's not easy trying to run XP + SP2 + Office 2003 and Visual Studio on 6GB space with 182MB RAM!  I seem to be constantly running cleanup and defrag, with everything stripped down for performance optimisation.

Anyway, so far so good.

**HELP!** I've reformatted the disk again, this time I've reclaimed the unallocated space and done it from right to left, because Ubuntu just won't install :sad: it gets as far as asking me which language I want to use and then hangs.  It takes ages just to get there!  

Worse, if I try to boot into Windows I've lost that option.  Why have I still got Grub when I've reformatted the linux drives?  Now when I try to get into Windows even, this is what happens:

(some info on Grub version and memory limits)

.[Minimal BASH like line editing is supported.  For the first word TAB lists possible command completions.  Anywhere else TAB lists the possible command completions of a device/filename. .]

grub> _

What am I going to do now ?  :confused:  Why won't Ubuntu install and is there any way of getting back into my windows partition  without a complete reinstall?

**Edit** I've had an idea.  Why don't I partition off some space on this PC, and give Ubuntu a chance?  My other desktop PC that the kids use has the most free space, but it already has Vista installed and I don't want to confuse things further with yet another OS.  But this plan would then mean I could let Windows use the 10 GB hard drive on the laptop which would ease things there, and my dual core Athlon 64 here with plenty of RAM and a large SATA drive, would surely install Ubuntu?

If I could just get back into my Windows install on the laptop, it was set up just how I wanted it, I could then add the extra hard drive space :(  

Any suggestions to get round this grub message, would be welcome.

---

### Post by Ndlovu on 2006-08-11
The space called reiserfs would have been the linux partition. It's an alternative filesystem to ext3 which is generally used by ubuntu.

It is concerning that Windows is not working. I'm not surprised that GRUB works even though the linux partitions have been formatted - GRUB exists in the boot area of the disk. It is takes up very little space and its primary function is to point to where the operating system(s) are located so that they will boot.

It's hard to say what the problem is with your setup. I'd probably start by using the LiveCD to boot into ubuntu and see if you can access the data on your windows partition. If you can, it's probably that grub is not pointing to the right place to load windows (relatively minor problem). If you can't, it could mean that the partition became corrupted somehow (bigger problem but maybe can be resolved).

Windows and other partitions should be automatically available from any Ubuntu system. If they are not, you can enable them using the graphical disks tool.

1.Open System->Administration->Disks
2.Select the correct hard disk, and click the Partitions tab.
3.Select the relevant partition, and click Enable.
4.To unmount the partition, click Disable.

A google search turned up a couple of web pages that *might* have some pointers to help sort out your problem. Maybe they're useful, maybe they're not:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)
[http://forum.notebookreview.com/showthread.php?t=66046](http://forum.notebookreview.com/showthread.php?t=66046)

I suspect that the problems you were having installing ubuntu were related to the earlier problems with interrupts (IRQ handling). In my case the install went fine when I booted the LiveCD using the additional "irqpoll routeirq" options. I would expect that if you can boot with the CD, it should be able to install as well, so I'm not positive that the two issues are actually related.

I see someone else solved the problem in a different way:
> the way I fixed it was changed the settings in the BIOS to go into legacy mode as opposed to native mode. I read in the manual that legacy mode uses the traditional 13-14irqs and native uses them all.

My laptop didn't give me any options like that, but you might want to look at your BIOS settings when you boot and see if there are any changes you can make to the way interrupts are handled.

Good luck!

---

### Post by MoiraA on 2006-08-11
Hi

I found the Windows hard disk from Ubuntu live CD and clicked enable.  It made sod all difference though :(  I'm not really convinced about the "minor" part of the problem description.

As far as the BIOS is concerned, I remember from the once or twice I've gone into it, it has extremely limited options and I doubt there's much I can do with that.  I've decided not to try Ubuntu again on the laptop - I'll partition off some space on this computer and install it here instead.

What I really need to do is recover some sort of options for the laptop though.  I don't know why I've been persisting in trying to dual boot it, when Windows would really benefit from the extra space.  If I can get back into my original install I'll merge the partitions.

When I first decided to put linux on it, I thought this would be a good option for a not too powerful PC that nobody but myself would be using, and there would be no other users to object or puzzle over a different type of OS.  The I realised I needed certain Windows programs and opted for the dual boot, but to be honest this is going to be a much better idea on one of the desktop PCs.

Right well .... an update.  I was advised that the following might work, ie going to a terminal in Ubuntu, and typing the following:

sudu dd if=/dev/zero of=/dev/hda1 count=1

Something happened - but not the deletion of Grub.  So now I am installing Windows :( a complete install, having merged the 3 partitions.  The option for a repair install wasn't there.  It's uber annoying, especially after having spent quite a bit of time yesterday getting it just how I wanted it.

Still, I'll be happy just to have a working laptop again.  At the moment it's formatting the drive.  I'm still not convinced that horrid Grub boot menu won't still be there at the end of it!

In a day or so I'll put Ubuntu on this PC.  For now, I feel like slicing everyone within range with the CD.

---

### Post by MoiraA on 2006-08-23
OK, I'm ready to install Ubuntu onto my desktop PC and was about to partition off some space with Partition Magic when I was presented with a choice of formatting options :-| 

Do I select a linux format (there's ext2 and ext3) or just go with NTFS and will Ubuntu subsequently do ahy formatting necessary?  There's "linux swap" as a choice too - should I actually make two new partions and set aside some space for this?

](*,)

---

### Post by Ndlovu on 2006-08-24
MoiraA, first step is to make a backup of whatever important data you have on that computer. I don't want to sound intimidating, but partitioning is pretty low-level stuff and you're moving around big blocks of information. The tools to do it aren't exactly the most user-friendly either.

Then... yes, create two partitions, one ext3 and one swap. Ubuntu would be able to format the partitions, but it will probably be easier to format it as ext3 from the start. A rule of thumb is that the swap partition should be at least twice the size of your RAM. So if you have 512 MB RAM, the SWAP partition should be about 1GB.

---

### Post by MoiraA on 2006-08-24
That's going to be one 2GB partition and another big enough to take Ubuntu then.  I'll do it right away.  I'm hoping Ubuntu will install some sort of boot manager.

The drive I was thinking of partitioning has quite a lot of free space on - I don't think Partition Magic should have too much of a problem with it.  In fact, the most free space I have is on the same physical drive as Windows, so I've deliberately chosen to install it on a second drive.  That way if I have insurmountable problems I can at least unplug the hard drive.  That said, the data's about as backed up as I can make it.

---

### Post by RRS on 2006-08-24
Partition magic sometimes has problems with linux partitions. 

If you're using the live cd to install you can run gparted from it and set up your partitions before installing. Then select the manual partitioning option during install and assign your mount points.

If you have 1g ram then 1g of swap should be plenty. The one to one and a half recommendation seems to date back to when even 512 was rare.

Enjoy your new installation

---

### Post by MoiraA on 2006-08-24
Ah right .... pity I didn't see that before the partitioning.  However it seems to have all gone well with PM, although I've got 2GB swap space.  Still, with two large hard drives, what's 1GB?

Windows Explorer can't see the new partitions obviously, but Disk Management shows the two spaces set aside, and PM shows a new extended partition, 2GB swap space and 15GB linux ext3.  My data is still all there.

So I'm now ready to try the live CD and install from that.  I'll let you know how it goes.

---

### Post by kellogs on 2006-08-24
You know, I've got 2,5 GB ram, and I use 512 MB swap. since 3 months and a half ago, My swap partition has not changed from 0 bytes used.

---

### Post by MoiraA on 2006-08-24
Well, I'd have thought the more RAM you had the less swap space you'd need actually.  Isn't the swap space what the OS uses when it runs out of physical RAM?

**Edit** does Ubuntu normally take absolutely ages booting the kernal?  It's been "uncompressing linux" for at least 10 minutes and is showing no sign of wanting to install the CD or even run it live.

OK I've come back from swimming for two hours and it was **still** "booting the kernal" so I've removed the CD.  I guess ubuntu and I are just not made for each other. :-?

---

### Post by MoiraA on 2006-10-10
Right - well, I haven't given up on this.  I decided to install Ubuntu on another desktop PC, one already running XP pro and Vista (on two separate hard drives, which dual boot).

Initially I was quite encouraged when the live CD ran and I managed to do a lot with Ubuntu, I liked it very much.  The problems came when I tried to install it.  Clearly it was going to destroy data on any partition it took space from, so I abandoned that and used Partition Magic to create a swap space and partition formatted with ext3.  

Now is won't even load the CD!  I'm getting this:

[4294808.127000] hdc: ide_intr: huh? expected NULL handler on exit

So I'm merging the partitions back again.  If this caused a problem then I'm prepared to move data out of a partition (it's two large hard drives, and just a spare PC so there's plenty of room) and allow ubuntu to format and install on the "empty" partition.

I just can't understand why I'm having such difficulty.  :confused:  I gave up trying to install any other OS on here - a disastrous attempt at Suse meant I had to completely reinstall windows as nothing would boot.  It just seems like nothing else wants to share this dual core pc.

I really want to learn how to use linux and Ubuntu seemed a great way to start.  All that's happening is, I'm ending up fixing XP after each attempt and learning nothing - I already know how to reinstall Windows!

---

### Post by jjjosh911 on 2006-10-10
Yeah i wish i could help

---

### Post by CatKiller on 2006-10-10
> **MoiraA said:**
> Right - well, I haven't given up on this.  I decided to install Ubuntu on another desktop PC, one already running XP pro and Vista (on two separate hard drives, which dual boot).

This is a very long thread, and rather old. A lot of people, myself included, aren't going to read through the whole thing to glean the information about the computer that you are now trying to install on. You could post some specs - particularly RAM, graphics card and drives.

> Initially I was quite encouraged when the live CD ran and I managed to do a lot with Ubuntu, I liked it very much.  The problems came when I tried to install it.  Clearly it was going to destroy data on any partition it took space from,

Not necessarily. GParted, the partitioning tool that the Ubuntu installer uses, is capable of resizing partitions without damaging the data therein. You should defragment those partitions as much as possible before trying this, though, to limit the amount of data-shuffling that needs to take place.

It's a promising sign that you liked the live cd environment. You might also enjoy the installed experience, once you get there :) 

>  so I abandoned that and used Partition Magic to create a swap space and partition formatted with ext3.

Seems reasonable, although not strictly necessary.

> Now is won't even load the CD!  I'm getting this:

[4294808.127000] hdc: ide_intr: huh? expected NULL handler on exit

Which drive have you got plugged in where? You mention that you've got a dual-boot going on already. Two separate hard drives? Where are they plugged in?

hdc is the Secondary Master. Depending on what you've got plugged in, and where, that could well be indicating a cd problem. Bad cd, dirty lens, failing drive, wonky cable, intermittent connection... You get the idea. Could even be a problem with the IDE controller of your motherboard.

> So I'm merging the partitions back again.  If this caused a problem then I'm prepared to move data out of a partition (it's two large hard drives, and just a spare PC so there's plenty of room) and allow ubuntu to format and install on the "empty" partition.

Ideally, for an easy install, you'll get rid of all superfluous partitions, and let the installer manage its own partitioning of the unpartitioned space.

> I just can't understand why I'm having such difficulty.  :confused:  I gave up trying to install any other OS on here - a disastrous attempt at Suse meant I had to completely reinstall windows as nothing would boot.  It just seems like nothing else wants to share this dual core pc.

Perhaps you should read up some, particularly on partitioning schemes, MS and Linux filesystems, and the Master Boot Record. That way, when it goes wrong, you'll have some idea of **why** it went wrong, and know roughly which area to look in to fix it again.

The vast majority of people do manage to install without a hitch, and you've had problems with 3 (?) installs. You must be unlucky.

> I really want to learn how to use linux and Ubuntu seemed a great way to start.  All that's happening is, I'm ending up fixing XP after each attempt and learning nothing - I already know how to reinstall Windows!

Ubuntu does seem to me to be a great way to start on Linux. I'm sorry that you've had problems so far. Once you get it going though, I'm sure you'll like it.

Good luck, and welcome to the community.

---

### Post by MoiraA on 2006-10-11
Thanks for the reply.  Sorry if I didn't give enough information.  For the record I've read up on master boot records and how to set dual boot options till I'm blue in the face, but the last time I hit problems, believe me the easiest solution was just to reinstall Windows.  I tried the repair console, fixmbr - everything I and anyone else could think of.

If Ubuntu is meant to be a good way to start learning about linux, then I don't see I should need to become a technical whizz  simply to get the blasted CD to install!  Most people wouldn't have given it even this long.

I know GParted would have partitioned my hard drives - but it also threw up a warning about not being able to guarantee not to destroy existing data.  If I'd had a partition that was empty it looked like it would have installed there, and that's what I want to try next.  I'm crossing my fingers it'll create a boot menu that will still allow me access to Vista and XP (hopefully with the ability to have XP as the default option).

The current setup of the PC I was intending to try Ubuntu on is a SFF, processor is an AMD athlon64 3000+, with 1GB RAM, a FX5700 GeForce video card, it has two physical hard drives, one SATA and one IDE.  One problem is I have no idea which hard drive is being described as which when I view descriptions during a linux install.  XP boots from the SATA drive, C partition, that's all I know, and Vista is on the IDE drive - then if the worst happens, I can physically disconnect it.

I'm frustrated by this, because with all the changes taking place with XP and Vista looking like an expensive, bloated option with most features disabled for pirated copies, Ubuntu is starting to sound a real alternative, if I could begin to get people used to it now.  I'd rather it was on my own PC, but I couldn't get past "loading kernal" on here.  No matter how much I read up on the topic of linux filesystems and master boot records, nothing explains adequately why each of around 6 CDs I've made, refuses to install (or even run the live CD here).  One of the reasons I'd rather have Ubuntu over here (other than it's my main PC) is that the other one has a Biostar motherboard with Biostar fan control.  So far Vista (either 32 or 64 bit versions) have not produced drivers and neither have Biostar which are compatible, so the fans run at 100% all the time - wasteful.  They do this in Ubuntu as well and I just *know* I'm going to have problems finding linux Biostar drivers for fan control!  

I know it would be a pain to read the entire thread, but if I'd repeated the steps already described in it, I would have made it  even more lengthy and more or a marathon to wade through.

---

### Post by CatKiller on 2006-10-11
> **MoiraA said:**
> If Ubuntu is meant to be a good way to start learning about linux, then I don't see I should need to become a technical whizz  simply to get the blasted CD to install!  Most people wouldn't have given it even this long.

True, but most people wouldn't necessarily have two different drives of two different interfaces and want to set up the partitioning themselves. If you give the installer the Microsoft option of "I am the only Operating System on this hard drive - there is no Operating System but me" then it's a snap. The confusion comes in from the Ubuntu installer's ability to play nice with others.

> I know GParted would have partitioned my hard drives - but it also threw up a warning about not being able to guarantee not to destroy existing data.

All partitioning tools do that. It's a risky process. What happens if there's a power cut while it's writing the partition table? Do you get half a partition table? The old one? A completely malformed one that makes it difficult to retrieve your data? Who could say with any credibility whatsoever that the process of moving critical data about your data layout will be risk-free?

> If I'd had a partition that was empty it looked like it would have installed there, and that's what I want to try next.

That would depend on how exactly the rest of the drive is laid out. And you'll have to format it in ext3 for it to work at all. Well, anything but FAT or NTFS, anyway.

> I'm crossing my fingers it'll create a boot menu that will still allow me access to Vista and XP (hopefully with the ability to have XP as the default option).

In principle it should - although if it doesn't, it's only editing a text file to add that functionality once Ubuntu can boot. See? Plays nice with others.

> The current setup of the PC I was intending to try Ubuntu on is a SFF, processor is an AMD athlon64 3000+, with 1GB RAM, a FX5700 GeForce video card, it has two physical hard drives,

This is good. The biggest trouble seems to be with Ati or Intel graphics and you have enough RAM to be able to do pretty much whatever you want. I wouldn't try to install the 64-bit edition of Ubuntu though - apparently it's not really for beginners or the faint of heart.

> one SATA and one IDE.  One problem is I have no idea which hard drive is being described as which when I view descriptions during a linux install.

The SATA drive will start with "s", the IDE devices will start with "h". The rest of the device name will depend on whereabouts it is in the system.

> XP boots from the SATA drive, C partition, that's all I know, and Vista is on the IDE drive - then if the worst happens, I can physically disconnect it.

I'm frustrated by this, because with all the changes taking place with XP and Vista looking like an expensive, bloated option with most features disabled for pirated copies, Ubuntu is starting to sound a real alternative, if I could begin to get people used to it now.  I'd rather it was on my own PC, but I couldn't get past "loading kernal" on here.  No matter how much I read up on the topic of linux filesystems and master boot records, nothing explains adequately why each of around 6 CDs I've made, refuses to install (or even run the live CD here).  

The most common reason for the live cd to not work is not enough RAM. The second-most common seems to be graphics card quirks. Installation can fail for quite a few reasons - almost always down to a configuration error.

> One of the reasons I'd rather have Ubuntu over here (other than it's my main PC) is that the other one has a Biostar motherboard with Biostar fan control.  So far Vista (either 32 or 64 bit versions) have not produced drivers and neither have Biostar which are compatible, so the fans run at 100% all the time - wasteful.  They do this in Ubuntu as well and I just *know* I'm going to have problems finding linux Biostar drivers for fan control!  

You may well be right that it will be difficult to find a Linux version of the Biostar control. However, you may well be able to find an open-source equivalent, or something that does the same for a different make of motherboard that can be amended to work with yours. It isn't something that I've looked into.

> I know it would be a pain to read the entire thread, but if I'd repeated the steps already described in it, I would have made it  even more lengthy and more or a marathon to wade through.

Things are looking good for you. You have a reasonably well-supported graphics card, you have a capable-enough machine that you can run the live environment OK, you don't have any nasty laptop hacks to worry about, and you seem both to be competent and to have done some basic research.

Potential pitfalls that I see for you are:

You can (at least for IDE devices, I don't know whether SATA is significantly different) only have four primary partitions. If you have many partitions on your drives already, this may be a problem for you.

GRUB will want to install a part of itself in the MBR of one of your drives. On either of your drives, this space is probably taken by the NT bootloader. Although GRUB can still boot Windows, you may have problems should you choose to get rid of Linux in the future. You may have to configure GRUB manually to boot XP and Vista in any case.

---

### Post by gn2 on 2006-10-11
Apologies if I've missed anything in the thread, I just read the first few posts.

You will struggle to get 6.06 Live CD to install without 256mb RAM.

Ubuntu 5.10 was different, it had two discs, a live and an install disc.

I used 5.10 install disc on my P3 500 laptop with 192mb RAM, then updated to 6.06LTS via the internet, and it was all simple point-and-click stuff.

I think you can still download 5.10 but I'm not certain.

eBay sometimes has them?

I've got a copy I can post if you want.
.

---

### Post by MoiraA on 2006-10-12
Cheers :)  I've got a rare day off work, so I'm going to give this a go right now.  Just so I don't lose any data, I'm going to move everything out of a 40 gig partition and instruct ubuntu to install to there.

gn2, and for the benefit of anyone who didn't catch the beginning of the thread, I have 1 GB of RAM on both this and my secondary PC (the one earmarked for ubuntu).  It was the laptop which was low spec (and I intend to replace it at xmas).  The original idea was just to use linux on my laptop, but sadly, I find I really need programs like Office, Visual Studio and ditching Windows altogether is not an option.

But thanks for offering to post a 5.10 CD, in fact I have this among the many "coasters" I've made containing Ubuntu, but I might as well try Dapper because it ought to work.

CatKiller (hope that's not a nick based on real life! I'm a cat lover!) my only real concern is the boot menu.  I'm hoping that if it does get into a mess someone somewhere understands how to edit it in XP so if the wrong OS is set as default (or XP not even shown at all) I can get it fixed.  I don't mind not being able to get rid of Linux in future - if anything it's Windows I want to ditch!  What I particularly liked about Ubuntu was that everything just worked - I was chatting in my usual irc channel within minutes of loading the live CD.  I could see my windows network - memories of my dual boot system on the laptop where I used Suse version 9 is of the nightmare that was configuring samba.

OK I'll let you know how it goes.  I've made an acronis image of my C drive, so if it all goes wrong, I can hopefully restore.

**Edit** Just tried Kubuntu and it started the installation process!  I need to make sure I've an empty partition and have to go out but I'm hopeful I might get that to install which was recommended as not very different to Ubuntu.  It was a distro I'd tried over here, but it never progressed beyone booting the kernal.

Right, kubuntu has installed nicely.  For some reason it made two linux partitions, which I am now hopefully merging.  My problem is though, that while going through the process, it detected two other operating systems on my PC and said that if this was correct, it would add these to Grub and I'd be able to choose which to boot into.  I went ahead, but on reboot, only the two windows systems were visible - it wasn't Grub at all.  I now don't know how to get kubuntu bootable, but I've posted a link below to a screenshot of my partition table and hopefully someone can tell my what I need to add in XP to give myself the option of booting into kubuntu?

[Partition Table](http://www.moiraatkinson.co.uk/partitions.JPG)

I see that the linux partition isn't set as active.  Does this matter and can I do anything about it?

---

### Post by MoiraA on 2006-10-13
Actually forget that - it didn't work and I'm not sure a logical partition can boot anyway.  I tried to use some space on the drive containing Vista, however Kubuntu seems to have wiped out vista and installed in that partition instead (still nothing on the boot menu).

I've wiped the entire disk and started again with Kubuntu, partitioning it in two - the only good news is that this is the IDE drive and therefore my windows install on the SATA drive is safe.  I can reinstall Vista later.  I hope to goodness Grub appears this time after the install - this seems to be the problem at the moment.

---

### Post by gn2 on 2006-10-13
> **MoiraA said:**
> Actually forget that - it didn't work and I'm not sure a logical partition can boot anyway.  I tried to use some space on the drive containing Vista, however Kubuntu seems to have wiped out vista and installed in that partition instead (still nothing on the boot menu).

I've wiped the entire disk and started again with Kubuntu, partitioning it in two - the only good news is that this is the IDE drive and therefore my windows install on the SATA drive is safe.  I can reinstall Vista later.  I hope to goodness Grub appears this time after the install - this seems to be the problem at the moment.

When you boot your PC is there an option to press a key to bring up a "Boot Device Selection Menu" sometimes this is F8?

This is the key to being able to utilise this simple solution:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Alternatively have you tried PCLinuxOS?

It's (in my opinion) far superior to Ubuntu for first time Linux users.
.

---

### Post by CatKiller on 2006-10-13
> **MoiraA said:**
> Right, kubuntu has installed nicely.  For some reason it made two linux partitions, which I am now hopefully merging.

If you delete the swap partition, you may want to look at creating a swap file.

> My problem is though, that while going through the process, it detected two other operating systems on my PC and said that if this was correct, it would add these to Grub and I'd be able to choose which to boot into.  I went ahead, but on reboot, only the two windows systems were visible - it wasn't Grub at all.

It's possible that you've got an option in your BIOS turned on called "Virus Protection" or something similar, whose only purpose is to prevent writes to the MBR. I don't think you have though, since you've installed Vista recently, but it might be worth checking.

Personally, if I wanted to keep the stuff on the SATA drive safe, I'd take that out before trying to install Kubuntu. Just in case.

---

### Post by MoiraA on 2006-10-14
Many thanks for the help.  gn2, I haven't noticed any such option when I boot the SFF - in fact you see nothing but the Biostar splash screen, it's only because I know it that I can enter the BIOS by pressing del.

I'm not actually a first time linux user :) although I appreciate how incompetent I must appear.  Believe it or not, I had Suse 9 running happily on the laptop, dual booting with XP and showing the XP partition in networking.  I also installed and configured Samba so I could see the linux network from my windows machines.

I read that thread with interest.  It's somewhat comforting to know other people find this an issue too.  However in my case, since I have a Windows install on each drive and I'm looking for a triple boot, I don't know that it would be a possible solution, ie I can't "disconnect the Windows drive".  I'm beginning to sympathise with this guy: "Grub on my MBR was worse than any virus I ever had".

In fact, my second attempt to install Kubuntu was just as bad as the first.  No Grub menu which showed linux and a Windows boot menu which has a duplicate entry for Vista which doesn't work and which I can't remove.  I could do it if I could edit the bcdedit.exe file in Vista but I can't work out how to get the necessary permissions - advice from Google clearly hasn't been tried on RC1.  It seems with Vista, that MS no longer allows you to do what you want with your own computer.

CatKiller, I haven't got Virus Protection turned on in the BIOS.  In fact, I think this problem is an issue with Vista.  Because I felt the thread was drifting away from Ubuntu problems, I asked some questions about boot loaders and Vista on Whirlpool and learned:

"from what I've read it will only support a single legacy boot loader. That single legacy boot loader can support multiple OS's though."

Frankly, I'm stuck.  I've tried both installing Kubuntu without Vista being in the way (since it overwrote it) then when it wiped that out, I've tried installing Kubuntu before Vista.  In neither case did I have the option of booting into Kubuntu or indeed drive partitioning that even looked as though it might work.

I'm not really worried about my SATA drive - if you knew what a squash it was to close the case of the SFF with both drives installed, you'd not suggest removing it lightly :) at any rate it's my spare PC and everything is well backed up.

FYI my drives now look like this:

[http://www.moiraatkinson.co.uk/windows_disk_management.JPG](http://www.moiraatkinson.co.uk/windows_disk_management.JPG)

[http://www.moiraatkinson.co.uk/partition_magic.JPG](http://www.moiraatkinson.co.uk/partition_magic.JPG)

Vista will be drive D in Windows disk management, PM clearly doesn't like the drive at all now.

I'm wondering whether to leave this until I get a better laptop at xmas and hope that will dual boot again, because all I'm ending up doing here is reinstalling Windows countless times.  Maybe if I started out with a totally wiped drive, put Ubuntu on first (if I could find a copy that would install) and then installed XP and forgot about Vista I'd succeed, but I can't face another Windows reinstall here and I don't want to ditch Vista - annoying as it is, I quite enjoy seeing the new features and would like to explore more than just the bcdedit file.  And Vista isn't much good here because I only have onboard graphics on this PC.

---

### Post by gn2 on 2006-10-14
> **MoiraA said:**
> Many thanks for the help.  gn2, I haven't noticed any such option when I boot the SFF - in fact you see nothing but the Biostar splash screen, it's only because I know it that I can enter the BIOS by pressing del.


If it's del for the BIOS it's quite likely that F8 will give a boot device selection menu.

I see you have Partition magic, I would suggest wiping everything clean and starting again from scratch.

Tried Super Grub disc yet? [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

If all you've got is on-board graphics, I doubt Vista will want to fully co-operate.. 

Vista=Nasty buggy Window dressing. 
Nothing new of any significance. 
What's the attraction?

Ubuntu works for me on my laptop (Portege 3440CT) but I'm thinking of a change to SAM soon. 
In my opinion Ubuntu just doesn't live up to the hype. 
These forums are Ubuntu's best feature, and are they certainly are a godsend.

Also for SFF cases 2.5" drives are a good idea, smaller+cooler+quieter+lower power consumption.
(With adapter if IDE)

---

### Post by MoiraA on 2006-10-15
I think the suggestion to wipe everything and start again is a good one too.  I might as well because the current config just isn't working.  If nothing else I can shift the page file back onto the first partition and use the extra space.  The extra entry in the boot menu is annoying but not something to reinstall Windows over.

Sorry for any confusion - I have onboard graphics here on my dual core athlon 64 PC, because I don't need a 3D graphics card and the onboard graphics are better than default as frankly, adequate.  This is why I put Vista on the other PC which does have a dedicated graphics card - nothing fantastic but good enough for Vista.  The only problem I have with it is the lack of drivers for the Biostar fan control (they don't even exist for the 32 bit, never mind 64 bit release).

I agree these forums are a godsend, people are brilliant.  I haven't evaluated whether or not Ubuntu lives up to the hype, courtesy of not being able to use it!  Yeah, smaller drives are probably a good idea, however those were the drives I had and before long that PC will no doubt get an upgrade so it's not worth worrying about now.  End of the day, it's stable, they do fit (albeit with a bit of a squash) so the potential heat can't be that much of an issue.

---

### Post by gn2 on 2006-10-15
> **MoiraA said:**
>  The only problem I have with it is the lack of drivers for the Biostar fan control (they don't even exist for the 32 bit, never mind 64 bit release).

 Yeah, smaller drives are probably a good idea, however those were the drives I had and before long that PC will no doubt get an upgrade so it's not worth worrying about now.  End of the day, it's stable, they do fit (albeit with a bit of a squash) so the potential heat can't be that much of an issue.


Perhaps fit a fan(s) which has it's own thermal controller?

There is a marked difference in heat (and noise) production between 2.5 and 3.5 drives.

This site may be interesting if you like peace and quiet: [http://www.silentpcreview.com/](http://www.silentpcreview.com/)

---

### Post by MoiraA on 2006-10-15
That's worth considering if I really do want to use Vista or Ubuntu as a main OS and they don't release (or in the case of Ubuntu) I can't find drivers for the fan control system.  In fact, the temperature of that PC never bothers me - I don't know why people panic over temperature, the CPU and hard drives are well able to cope and the system would shut down with a serious overheat.  As long as everything is stable, I'm happy.  I've done quite a bit to make my PCs quiet, and while the SFF is noisier than this one, I'd expect that with a more powerful graphics card, but when fan control kicks in it's really hard to discern that there are two computers switched on and running.

I downloaded Super Grub and might give that a go.  I've also found [this](http://www.pro-networks.org/forum/viewtopic.php?t=78184) guide on triple booting between Vista/XP and Linux and I've done everything it suggests - I shouldn't be having this problem of failing to see the Grub menu after installing linux last of all.

---

