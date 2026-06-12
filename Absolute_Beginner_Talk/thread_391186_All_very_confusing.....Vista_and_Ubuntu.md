---
title: "All very confusing.....Vista and Ubuntu"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by vnzjunk on 2007-03-22
Hello

I have been sorting through the various posts concerning the coexistence of Vista and Ubuntu using Grub or a different boot loader.  This is about where my confusion starts  to set in.

Let me preface this by stating that I presently have a 1Gig Pentium 350Mb ram and 8G hard drive on which I installed both Xp Pro and Ubuntu, dualbooting the two operating systems via Grub.  All works fine and haven't had a single problem.

Today I just ordered a new Dell computer which will arrive shortly with Vista Premium installed on its 250G SATA hard drive.  I have no idea in what state the hard drive will arrive but I assume that it will have unformatted space on it which I am assuming will be recognized by the Ubuntu CD and partitioned for the Ubuntu install, and that Grub will also be placed on this partition. Already I am breaking the very good rule of assume nothing. 

Any ideas ahead of time?  My intent is to not screw up the working Vista OS and then have to wade back through the posts of others who found themselves in that or similar  position and were stuck getting back to square 1. The postings which I read  were very, very confusing.  One suggestion was even made not to try to install Ubuntu along with the Vista OS,  and just be satisfied running the Live CD until the Ubuntu guru's had investigated the dual booting of Vista/Ubuntu further.  

Any thoughts and suggestions ahead of time would be appreciated.

Thanks........Mark

---

### Post by mikewhatever on 2007-03-22
Making groundless assumptions is definitely a mistake. Another mistake, in my opinion, is getting vista. I am not trying to dissuade you, it's just that people never learn. Anyway, good luck.
[http://ubuntuforums.org/showthread.php?t=347408](http://ubuntuforums.org/showthread.php?t=347408)

---

### Post by vnzjunk on 2007-03-22
> **mikewhatever said:**
> Making groundless assumptions is definitely a mistake. Another mistake, in my opinion, is getting vista. I am not trying to dissuade you, it's just that people never learn. Anyway, good luck.
[http://ubuntuforums.org/showthread.php?t=347408](http://ubuntuforums.org/showthread.php?t=347408)

Like I said, I just ordered the computer.  It comes with Vista.  I wasn't asking how wise it was to purchase the computer.  It is a done deal and so is the install of Vista............

I was wondering what to expect as far as putting Ubuntu on the computer along with it. It wasn't intended as a thread starter on MS vs Linunx or Ubuntu debate.

Thanks anyway

Mark

---

### Post by AndyCooll on 2007-03-22
The link in my signature is an excellent starting point for dual-booting.

:cool:

---

### Post by confused57 on 2007-03-22
> **vnzjunk said:**
> Like I said, I just ordered the computer.  It comes with Vista.  I wasn't asking how wise it was to purchase the computer.  It is a done deal and so is the install of Vista............

I was wondering what to expect as far as putting Ubuntu on the computer along with it. It wasn't intended as a thread starter on MS vs Linunx or Ubuntu debate.

Thanks anyway

Mark
One VERY important thing to note in the thread mikewhatever provided is not to use any Linux partitioning tools to resize your Vista NTFS partition...it's OK to use gparted to resize XP, but not Vista.

---

### Post by vnzjunk on 2007-03-22
Thanks Andy

I checked out the info on the dual boot from your sig.  I still have a question about Vista being placed on the second partition (what if it is pre installed on partition 1) but that probably would be better addressed via the forum on that particular page.

Thanks

Mark

---

### Post by vnzjunk on 2007-03-22
Confused57

Thanks.  And I seem to recall reading also something about the vista partitioning program couldn't/wouldn't setup a partition suitable for Ubuntu or something like that.

Mark

---

### Post by igknighted on 2007-03-22
> **vnzjunk said:**
> Like I said, I just ordered the computer.  It comes with Vista.  I wasn't asking how wise it was to purchase the computer.  It is a done deal and so is the install of Vista............

I was wondering what to expect as far as putting Ubuntu on the computer along with it. It wasn't intended as a thread starter on MS vs Linunx or Ubuntu debate.

Thanks anyway

Mark

Don't listen to the haters on this forum.  Vista is a great OS, for a MS operating system at least.  I might recommend (to avoid any issues) putting you Ubuntu partition on the 8GB HD you already have and throwing that in there.  Then you wouldn't have to worry about overwriting Vista's bootloader.  You could save all your files on Vista's NTFS partition with the newly stable NTFS-3G driver if 8GB isn't enough space.

---

### Post by mdsmedia on 2007-03-22
> **igknighted said:**
> Don't listen to the haters on this forum.  Vista is a great OS, for a MS operating system at least.  I might recommend (to avoid any issues) putting you Ubuntu partition on the 8GB HD you already have and throwing that in there.  Then you wouldn't have to worry about overwriting Vista's bootloader.  You could save all your files on Vista's NTFS partition with the newly stable NTFS-3G driver if 8GB isn't enough space.As Linux partitioning tools are not good for partitioning Vista, is the Vista partitioning tool the only alternative?

EDIT: Just read the thread linked above and have my answer

---

### Post by vnzjunk on 2007-03-22
igknighted

Thanks.

---

### Post by vnzjunk on 2007-03-22
I had considered that but want to keep the old machine intact for other purposes.  Also with such a large hard drive, if possible, I want to make use of it rather than putting the older, slower drive in the new computer.

---

### Post by antoz on 2007-03-22
I would not know how to do it but came accross this link it may be helpfull
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by confused57 on 2007-03-23
Found this with a Google search:
[http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111)

---

### Post by noobnoob on 2007-03-23
I just did this.  Got a laptop with Vista on it, discovered what a mistake that was, and decided to try adding Ubuntu.

I used the Vista file-partitioning tool to shrink the Vista partition, leaving the rest of the disk space unallocated.

Then booted up with the Ubuntu CD, used the partitioner on it to (manually) create two partitions inside the unallocated space:  one file space partition, one swap space partition, as recommended on the screen of the partitioner.  I also changed the boot flag from the Vista partition to the new Ubuntu file partition, and let the Ubuntu install proceed.  I wasn't sure what to expect at this point, but what I ended up with turned out to be exactly what I wanted:  a Grub menu with both Ubuntu and Vista boot options already on it.  The Ubuntu menu option was the first, default option, the Vista option the last one.

This is my first experience with Ubuntu;  so far it looks and works great.  Great job, folks!

---

### Post by vnzjunk on 2007-03-23
NoobNoob

Many thanks for your response.  Exactly what I was looking for.  Someone who had already faced the exact same situation and the steps taken which successfully resolved it.  I put the forum and links aside for the night after getting to the point where it seemed like I was going in circles.  Upon reflection between then and now and reading your post I got the feeling that many of the situations linked to were actually slightly different and thus the various 'fixes'.  In my mind I came to the conclusion that the situation was similar to when I reformatted my old hard drive, installed Xp in its partition leaving the rest of the hard drive un allocated (key here unallocated) and then started the Ubuntu install which went about its business of installing into the un allocated space.  The only 'problem' that I could forsee was with the boot loader or boot loaders...........

And that is where your post cleared up that question.....at least in your situation.

So thanks.  I know know that it can be done and all within the generalized steps that I had pretty much decided upon. And now there are also those other links posted in this thread to reference if something were to go wrong.

Thanks again........vnzjunk

---

### Post by vnzjunk on 2007-03-23
NoobNoob

Since you said this is your first experience with Ubuntu, and of course your new install.  If a problem does pop up with that 'new'  boot setup, please post back here any details, as that would be very informative.

vnzjunk

---

### Post by jonivey on 2007-03-23
Noobnoob,
My situation was SOMEWHAT similar to yours. My desktop PC had Vista pre-loaded. I used an
Ubuntu 6.10 CD that I got from Canonical and loaded it, winding up with a Grub bootloader
that had both OS's with ubuntu as default.  HOWEVER, whenever I choose Vista, the screen goes
kaput and nothing happens so I'm forced to power down and power back up again. In effect, it seems that Vista has gone into a virtual Witness Protection Program :)
See my thread Why Did Vista Go into Hiding?  in Installations and Upgrades category.

Jon

---

### Post by vnzjunk on 2007-03-23
Jon

If you could post a link here to that thread it would be helpfull.

Also in my readings last night, there was mention of having to go in and add some lines to the bottom of the grub file that let it know that Vista was there and where it was located.  NoobNoob didn't seem to indicate that he had to deal with this problem which had me scratching my head........but if it works then.........  That was one reason I mentioned that if he had any boot problems going forward in this regard to please post some info here.

Thanks Jon

Mark

---

### Post by Vivix729 on 2007-03-23
Not sure if anyone mentioned this, but if you don't agree with Vista's EULA, you can call up MS or Dell, and see how you could get a refund for it.

I would stay away from Vista as far as possible.

---

### Post by comhack on 2007-03-23
I am not for sure why your screen is blanking whenever you choose Vista from Grub. I have Vista Ultimate installed along with Ubuntu Edgy with no problems at all. Here is my grub file, it may help you figure out the problem you are having:

```
timeout         10

## ## End Default Options ##

title           Ubuntu                          
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro verbose splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Recovery                                        
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Vista Ultimate                 
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Thanks

---

### Post by Bias on 2007-03-23
I would expect the new Dell machine to have one partition on the disk and it to take up the entire space. Part of this will contain the stuff necessary to install and maintain Vista. Normally Dell do not include DVDs/CDs of the OS in the package however you can request them on line and they send them seperately. I would not try to change any partitions on this machine untill you have those in your hand. :)

---

### Post by vnzjunk on 2007-03-23
ViVix729

I ran across a thread the other day.  I forget exactly where it was, but the discussion was how to try for a refund, if one would be granted, how much it would be, if it would be financially worth while to do it and so on.

What I got from the posts was that the per copy cost to the manufacturer of the computer was much less than the shelf price for Vista and might or might not be worth while pursuing depending on what your time was worth and if you wanted to put up with the hassle. That is assuming they will even listen to you.  If you have ever tried in the past to get a rebate that was due to you then you probably know the procedures that I am referencing.  Some times it is painless and other times it isn't.

Your mileage and threshold for pain might vary.......<grin>

vnzjunk

---

### Post by noobnoob on 2007-03-23
> **vnzjunk said:**
> 
Also in my readings last night, there was mention of having to go in and add some lines to the bottom of the grub file that let it know that Vista was there and where it was located.  NoobNoob didn't seem to indicate that he had to deal with this problem which had me scratching my head........but if it works then.........  That was one reason I mentioned that if he had any boot problems going forward in this regard to please post some info here.

I have switched between Vista and Ubuntu on boot-up several times now, and have never had a problem.  I wonder if my changing the boot flag to the Ubuntu partition during installation made a difference?  I.e., let Grub get in the first licks, not the Vista bootloader.  (But as my name indicates, I am speaking from a position of ignorance here, so if what I say makes no sense, chalk it up to rank noobiness.)  In any case, I have never messed with, or even looked at, the grub file at all.

For further details, my machine is a Dell Latitude D420, which came with Vista pre-installed.  Dell had already laid claim to 3 partitions, so my Ubuntu file and swap partitions are logical partitions inside the 4th hard partition.  Also, my Ubuntu installation is the Japanese version of Edgy Eft.

If I do run into a problem, I will be sure to let you all know.  So far, the only boot-related problem I have run into is that the Ubuntu hibernate function does not always seem to work correctly -- sometimes I end up with a brand new session upon powering back up, rather than a continuation of the previous session.  I suspect this is not related to the dual-boot issue at all, however, and is rather a flakiness in the hibernation mode itself.  (If anybody has any suggestions for fixing this, they would of course be greatly appreciated.)

---

### Post by vnzjunk on 2007-03-23
NoobNoob

Thanks for the update.  Every once in a while you can poke around and sometimes you get lucky and hit it rite off.  Other times (more often than not) you can screw things up royally in the process.  But like they say, not much is learned by being rite all the time. Fixing stuff we break (hopefully a soft temporary break and not a permanent hard one <grin>) is how many of us learn.

The computer which I ordered is a Dell  E520 with an Intel-Pentium D Dual Core 2.8G, 1Gig memory, 250Gig hardrive.

Ok on setting that flag. I am fuzzy on that one. When I set up my present Linux box and a couple of previous ones, I used Gpart to setup the hard drive before install.  It all worked fine but of course I wasn't dealing with Msft security issues on those installs either.

Ok on the partitioning which Dell preset. Another post in this thread says that Dell will partition and grab the whole drive for Vista.  Hmmm.  If so then the shrinking of partitions might be in order but obviously 2 different partitioning schemes from the factory.  Might have something to do with laptop vs desktop.

We shall see.  Either it will go smoothly like previous installs or I will get an education along the way.......maybe both.

Thanks for your input.

vnzjunk

---

### Post by vnzjunk on 2007-03-23
Bias

Thanks for the tip on the disks.  I was expecting the re-install disk and wasn't aware that the actual OS disks were available.  I will definitely check into it as having those obviously would be a big help should something go wrong.

Thanks

vnzjunk

---

### Post by joethenoob on 2007-03-23
I can't give you much help with the boot loader, but I have an idea about the partition. Have you considered just reloading Vista when you get your new Dell? I suggest this for a couple reasons.

1. It will get rid of all the extra crap that Dell loads on their PC's. If you've purchase Office or any other software with the system, you should get copies of them that you can reinstall. It's a drag to do it, but I do every my company gets a new machine. You should be able to boot to the recovery disc and make your way thru the install.

2. Instead of relying on a partition manager, you can delete the system partition (leave the little 50? MB partition alone), and create a new partition using only maybe half your disk space. Load Vista on this partition from the get go. You can then use the rest unpartitioned space for Ubuntu, or create second partition for storage away from the OS drive.

If you decide to go this route and want more info before doing it, let me know. I'd be happy to walk you thru it.

---

### Post by joethenoob on 2007-03-23
> **vnzjunk said:**
> Bias

Thanks for the tip on the disks.  I was expecting the re-install disk and wasn't aware that the actual OS disks were available.  I will definitely check into it as having those obviously would be a big help should something go wrong.

Thanks

vnzjunk

Yeah, Dell is sneaky about that. When you build the PC on the website, you can select your OS version, but one is (no media) and another will be (media included) or something like that. I can't imagine who would want to purchase a preloaded PC without an OS disk.

The disks you get won't look like a normal Windows disk. The Vista disks I've gotten from Dell are purple.

---

### Post by tomxyz on 2007-03-23
I stumbled on this site a while ago,

maybe you can have a look here

[http://lifehacker.com/software/operating-systems/triple+boot-xp-vista-and-ubuntu-214700.php](http://lifehacker.com/software/operating-systems/triple+boot-xp-vista-and-ubuntu-214700.php)


Tom

---

### Post by airtonix on 2007-04-02
umm so again...((shakes head to clear confusion)) tell me whyyyyyyy people are actually wanting vista?

or even considering keeping it on their drive? especially if they have windows xp install discs lying around?

oh yeah wait....you can have flying feet....but before i give it to you you have to inject this here syringe full of heroine.

say again....flying feet...woooot give me that shabizbang stuf now!!!

---

### Post by vnzjunk on 2007-04-02
So tell me.  What part of it didn't cost anything extra, came already installed on the hard drive, and was not a factory option to not be installed do you not understand.

The next time you go out to purchase a new car/truck.  Tell the factory you want it without an engine so that I can get on a message board and deride you for getting an engine in your purchase.........

Have a good day

vnzjunk

---

### Post by vnzjunk on 2007-04-02
Update:

I got the computer last week.  Actually days ahead of the anticipated delivery schedule.  Everything works as advertised.  I checked the hard drive out and yes, Dell does partition the main system partition for Vista to use up all the available space after setting up the 'hidden' system restore partition.  I should be able to shrink this main partition using disk tools provided with Vista to take up much less room and then go back in with the Ubuntu disk and install into this partition.  I have not done this as of yet as I have been spending time checking out the new system as it is, before fooling around with the hard drive setup.  I did load the live ubuntu CD operating system and all seemed to work fine from that so I suppose when it comes time to install it into its own partition all will go as expected, with maybe a little tinkering of the boot loader.

So far so good and I thank all those who took the time to offer 'CONSTRUCTIVE' advice or just well wishes.

Later

vnzjunk

---

### Post by deuchar1 on 2007-04-02
> **igknighted said:**
> Don't listen to the haters on this forum.  Vista is a great OS, for a MS operating system at least.

I had my first shot of it the other day and would be inclined to disagree. I'm by no means a Microsoft hater - but it is a blatant ripoff of Beryl. Not only that - the interface is unintuitive compared to various other systems (Ubuntu included) - I'm a designer myself and can spot problems a mile off. 

It's a poor man's Apple/Beryl halfbreed. Not only that - it automatically filters out sites which the user might try and visit. Granted, filters are a good idea for content - but the user shouldn't be completely shut out by default - they should be given the option.

---

### Post by joethenoob on 2007-04-02
> **deuchar1 said:**
> I had my first shot of it the other day and would be inclined to disagree. I'm by no means a Microsoft hater - but it is a blatant ripoff of Beryl. Not only that - the interface is unintuitive compared to various other systems (Ubuntu included) - I'm a designer myself and can spot problems a mile off. 

It's a poor man's Apple/Beryl halfbreed. Not only that - it automatically filters out sites which the user might try and visit. Granted, filters are a good idea for content - but the user shouldn't be completely shut out by default - they should be given the option.

Users are given the option to have the filters run or not. If you don't want the filters, turn them off. Simple as that.

---

### Post by airtonix on 2007-04-02
Actually vnzjunk..vista is costing you more...and if you were to buy a WRX impreza from a japanese importer in a half cut sceanrio...you would indeed be able to decide which bits you dont want.

if your unsure if your paying extra for vista then you ought to read this : 

[http://www.desktoplinux.com/news/NS3179571720.html](http://www.desktoplinux.com/news/NS3179571720.html)
> 
To make Vista as capable as SLED was on the base system, I had to push my system up to 2GB of RAM and add a 256MB NVIDIA GeForce 7600GT card. I was, of course, unable to add flash memory or a flash-enabled "hybrid" hard-drive. 

and this too : [http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html)
[FONT=Arial,Helvetica][SIZE=3][/SIZE][/FONT]
to be sure some car dealers even give you the option of choosing your engine type....

even better just format the damn thing and rid your self of the plague....much better.

question : you know those brand name clothes (nike, ripcurl, billabong, holden, ford, etc,etc)? do you feel that they should be free. what with them actually being mobile adverts for the company in question? if not free then at least you should be recieving rent money for the logos.

---

### Post by jagrav on 2007-04-12
> **vnzjunk said:**
> Update:

I got the computer last week.  Actually days ahead of the anticipated delivery schedule.  Everything works as advertised.  I checked the hard drive out and yes, Dell does partition the main system partition for Vista to use up all the available space after setting up the 'hidden' system restore partition.  I should be able to shrink this main partition using disk tools provided with Vista to take up much less room and then go back in with the Ubuntu disk and install into this partition.  I have not done this as of yet as I have been spending time checking out the new system as it is, before fooling around with the hard drive setup.  I did load the live ubuntu CD operating system and all seemed to work fine from that so I suppose when it comes time to install it into its own partition all will go as expected, with maybe a little tinkering of the boot loader.

So far so good and I thank all those who took the time to offer 'CONSTRUCTIVE' advice or just well wishes.

Later

vnzjunk
vnzjunk,
Looking forward to your account of the dual-boot experience. Getting a new dell laptop with vista home basic pre-installed and wanting to dual-boot with feisty fawn.

---

### Post by olbrait on 2007-11-13
I wanna to ask, if I have drive C with vista and drive D with data, both formated to ntfs, I need to resize drive C via vista, it is clear, but can be resized drive D by gparted or I also need to use vista resizing program? I now, that it is stupid question, but I want to be sure, that I will not kill vista to someone. Had anybode do it?

---

