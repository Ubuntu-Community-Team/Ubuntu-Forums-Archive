---
title: "Hello everyone - forgive an aged newbie..."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by marxman47 on 2007-08-01
Hello everyone.  I'm a bit of an old-timer who has been running M$ windows since 3.1.  Every new version of Windows seems to need a completely new machine to work properly and I don't want to get caught up in Vista and its expensive upgrades.

I've heard about linux, of course, and on an old PC I even ran an early Ubuntu from a 'live' CD; that was a really good experience, but I had no way to save files or do the other stuff I could with M$ and I was always a bit wary about 'doing things' to the hard drive, partitions and so on.

I've recently read about WUBI and think that this might be the way forward; I've read whatever I could  find, but I have one problem which I hope you might be able to help me with - I have a HDD with 2 partitions, C and E; C is the Windows partition and is about 40 GB, with about 12-15 GB free.  The other partition holds 'My Documents' and some other bits and pieces and has about 107 GB free.

Can I use WUBI to install Ubuntu on 'E', where it can have lots of space to run, or do I need to use a more limited installation on 'C' as that is where Windows lives?

I realise that this is probably a very dumb question, and that if I have to ask it I shouldn't really be bothering at my age, but I would love to try the Ubuntu OS properly before committing to it for good.

Again, any help you might be able and good enough to offer will be most welcome.

marxman47

---

### Post by sad_iq on 2007-08-01
Why not use the live cd and when you install it choose manual partitioning and resize the E:\ drive??
 Should work.remember to defrag your disks and check them for errors!!! Or let's see if someone more skilled can give you another advice!!!

---

### Post by evadwolrab on 2007-08-01
If you're getting rid of Windows then Ubuntu will give you the option to erase and overwrite the partition that Windows is currently on.

Alternatively you could create ANOTHER partition, using some of the free space on your documents partition. The menus are fairly easy to follow. If you're worried, just go for the new partition in your free space option. Then once you're confident for the jump, you can overwrite Windoze.

---

### Post by Benbow on 2007-08-01
Depends on your patience in getting to grips with a new operating system. I would say that if you can move from one version of windows to the next, Ubuntu will be a dream and using this forum will guide you through any difficulties.
I am a youngster at 68 and have been with computers since 1983 and still none the wiser.
Good luck, you'll be fine.

---

### Post by thefoolisme on 2007-08-01
I would definitely take some space from the E drive and put Ubuntu there.  Here's a great web site to get you started.  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

You can't install Ubuntu on the C Drive with Windows, so you have to create new partitions.  You'll want 1 for root (/), and 1 for swap (usually 1.5 - 2x your amount of RAM) at a minimum.  Most folks put a home partition in there too for storage of their personal settings, stuff, etc that doesn't have to be replaced with an upgrade, etc.  

Doing a manual partition setup in Gparted isn't difficult, but make sure you read :-).  Also, backup your important documents and stuff before doing anything with partitions, installs, etc.  They should be backed up regularly anyway.  Also, it is important to defragment the E drive before shrinking it and adding partitions.  I believe the current recommendation is to defrag 3x first.  

I have multiple PCs set up with dual-boot configurations now, and find myself going into Windows less and less.  If my Canon printer worked with linux, I might never go back to Windows :-)  A dual-boot would be good for you until you figure out the ins and outs, and whether it's truly something you want to do.  

Finally, the forum here is great for support.  Don't be afraid to ask a question if you can't find it in a search.  There are so many helpful people here, which is one reason I've stayed with Ubuntu so long.

---

### Post by p_quarles on 2007-08-01
@all: the original poster's question was about Wubi, which allows you to install Ubuntu inside Windows. 

@marxman47: I've never used Wubi, but I doubt you'll have any problems installing it on the E: drive. In any case, from what little I've read on this program, it doesn't look like it does anything permanent, so go ahead and install it. If it doesn't work out, you should be able to delete it.

---

### Post by SPRL on 2007-08-01
Have no idea about WUBI but I never liked the idea of duel boot or booting inside a system.(grub on boot with Windows just leads to headaches if you uninstall Ubuntu). With how cheap HD's are I just bought a new one and took out my MS drive. I installed Ubuntu to "try out" on the new drive. Its been about a month now and I have no plans on putting back the MS drive.:popcorn:

---

### Post by bodhi.zazen on 2007-08-01
WUBI is very cool, but at this point not for the feint of heart...

Best use the standard installer. Best install GRUB in the MBR. It is both reliable and easily fixed. IMO GRUB is not so easy to install **if you deviate form the MBR** and many users turn fears/FUB into self fulfilling prophecies because they can not configure grub ... 

Installing GRUB into the MBR, following the defaults is fairly failsafe and if there is a problem easily fixed.


During the install process you can easily resize your partitions. Just be careful to understand the new Linux terminology.

Partitioning information : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by marxman47 on 2007-08-01
A big thank you to everyone who read my post and for the positive help you've offered me.  I'll look into all the options carefully before deciding, although I am quite taken with the idea of installing to the 'E' drive using WUBI.

If I installed another HDD, would I need something like GRUB (?) to determine which OS to use, or would you advocate using 'plug-in' drives, which I think I've seen advertised somewhere (not external drives, but ones which fit into a caddy in the PC)?

Again, as a windows wimp, made afraid of doing anything that Big Bill hasn't approved, many thanks.  I want to break free!

marxman47.

---

### Post by sad_iq on 2007-08-01
Grub will be required even without windows, and if you decide to install Ubuntu on such a removable drive you could have troubles booting into any OS if grub doesn't correctly configures itself and a manual configuration will be required(witch is not easy for a newcomer in the linux world). My advice...buy a few blanc DVD's, save your documents as a backup and install Ubuntu in your hdd(in the E:\ drive). Also I haven't used WUBI(no windows to use it :) ) but maybe you will be better with the LiveCd, download it, burn it at a low speed(4x), check it's md5 sum, then boot it just to see if it works with your hardware(sound,video...etc). Post if you need more advice!!!

---

### Post by marxman47 on 2007-08-03
Hello again everyone.  I have been using a 'live' **ubuntu **7.04 (Feisty Fawn) today, and I am deeply impressed by it, particularly as I was able to see my XP pictures and read my XP rtf files and such, to connect to the internet through my broadband router (with no problems), to watch the introductory video and listen to some music.  My PC is reasonably up-to-date and **ubuntu **'found' everything without trouble.

Now, considering the modest cost of HDDs these days, I was wondering if this might be a possible, or even better route than carving up my XP disk to carry both OSs.

Is there anything special that I should 'take on board' for this option (which means I wouldn't need to use WUBI) and how will I determine which OS to use until I am sufficiently confident to 'swap over ' to **ubuntu **permanently?

Again, please accept my apologies for my lack of knowledge, and thank you in advance for any advice you might be able to offer.  Last evening, I watched a video on Google about **linux **and apart from any technical advantages it may have, (and they seem to be abundant) I find the political basis of Open Source infinitely preferable to M$'s 'grab, grab, grab', although I'm probably preaching to the congregation here :).

marxman

---

### Post by philinux on 2007-08-03
My route exactly two weeks ago was to install a second hard drive, pretty easy to do. Then i put ubuntu on it from the live cd.

Someone said it's best to disconnect the "windoze" drive while you install linux. Is this true?

---

### Post by p_quarles on 2007-08-03
When you install Ubuntu, it automatically installs a new bootloader that gives you a menu from which you can select the operating system you want to load. 

Getting a new hard disk is an option, and it's safer for your data than partitioning the existing drive. That said, I've never configured a system that way, and I believe it involves some extra configuration during installation. 

If you backup all your data and defragment the hard drive, however, partitioning is actually very safe, and its actually the easiest of all dual-boot options, since the live CD helps you through it.

---

### Post by tszanon on 2007-08-03
> **philinux said:**
> Someone said it's best to disconnect the "windoze" drive while you install linux. Is this true?
I don't do it, because GRUB won't automatically recognize the windows installation, so it won't automatically add the option to boot windows in its menu.
Disconnecting the windows drive makes sure you won't overwrite it, but it requires that you edit /boot/grub/menu.lst later, adding the windows installation (which is easy).

As you see, each option has its advantages and disadvantages.

---

### Post by ugm6hr on 2007-08-03
> **philinux said:**
> Someone said it's best to disconnect the "windoze" drive while you install linux. Is this true?

This is only the case if it's an *external* linux HD.  This is because Windows will then be unable to boot without the external drive plugged in at the time of booting (if you get it wrong).  

Of course, removing the Windows drive will remove the risk of accidentally writing Ubuntu over the Windows HD instead of the empty one.  Probably best to use the manual partitioning option to check: [http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)  It should be fairly obvious which drive has Windows on it already.

If you're going for an *internal* HD for linux, there shouldn't be too much of an issue.  I would recommend making the new drive the 1st boot device in BIOS prior to installing though, and then selecting where Grub should be installed carefully (in the Advanced window of the partitioning section of installation: [http://img519.imageshack.us/my.php?image=feistydual18cv5.png](http://img519.imageshack.us/my.php?image=feistydual18cv5.png)).  I believe that if the blank HD (ready for linux) is the 1st boot device in BIOS, it should be identified as (hd0) by Grub - which is the Ubuntu default location for Grub anyway.

In this scenario - the worst that could happen is that Grub gets written to the MBR of the Windows HD (if you get hd0 and hd1 the wrong way round, which shouldn't matter, since both HD's will always be installed.  The only problem might occur if you decide to wipe the Ubuntu partition in the future (which would leave an unbootable Windows - but this is preventable: [http://ubuntuforums.org/showpost.php?p=3070095&postcount=7](http://ubuntuforums.org/showpost.php?p=3070095&postcount=7)).

I hope this isn't too confusing - but it's better to be prepared!

Credit: images borrowed from [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) (in fact - just read this!)

---

### Post by marxman47 on 2007-08-06
Hello again everyone.  It has been a lovely week-end for getting out and about after all that appalling weather and even linux has had to take a back seat for a day or two.

I have resized my E: partition to free up about 60GB for an installation of Feisty Fawn which I shall be carrying out very shortly.

I would like to take this opportunity of thanking everyone for their help and support in showing me the way to come off MicroCrack!  I would also like to mention the wonderful and informative screencasts at ubuntu-uk.org, which have given me a lot more confidence than I had before.

I have looked up the local (Nottingham) LGU, and a friend and I are going to get along to one of their meets.

I hope to be here for quite a while, God willing, and I hope you might all be as helpful in the future as you have been up until now.

marxman47.

---

