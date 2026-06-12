---
title: "Looking to install Ubuntu"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by peter_k on 2007-06-11
Hello all:

I am currently a Mandriva user (installed it about 5 days ago), but am thinking of switching to Ubuntu.  I had a couple of basic questions I was hoping you guys (and gals) could help me with:

1. I have just downloaded the most recent version (7.04 - Feisty Fawn) from the Ubuntu website, and am planning to make an .iso of it.  Can I boot from it and try it before I install it?  Does this .iso include the same amount of software that comes with the "Ubuntu Guide" book I've seen?  I know the book has an older version (I believe 6.10), and I'm looking to buy it anyway to help me with installation and use, but I wanted the latest Ubuntu version, and wasn't sure how hard upgrading after the fact would be.

2. Is it possible to specify what size the partitions would be during the install?  Mandriva defaults to 8GB for /hda1, and that is too small; I've tried changing it with gparted, but no luck yet.  I would only be looking to run Ubuntu, and Windoze is no longer on the machine, so I'm really just looking to have more room for the packages I install.

3. I currently have an 80GB hard drive, but am planning on buying a bigger one in a few weeks.  Can I install Ubuntu on the 80GB, with a nice size partition for /hda1, and then install a second drive later and be able to install my user files (mp3, documents, etc) to it?  Will this be a problem as far as saving files, or does Ubuntu handle this OK?  Or, am I better off just installing the new drive and starting from scratch with it?  If I do use two drives, is it OK if the second one is an external one (I'm assuming USB)?

I realize now that is more than a "couple" of questions. :)

Thanks,

Peter Knox

---

### Post by ugm6hr on 2007-06-11
Essentially the answer to all your questions is yes.

The .iso is a LiveCD - so boots directly from it (prior to installing).  Don't know much about the book though.
You can specify your partition sizes - but if you want to use the whole hard drive, it's even easier (almost one click).
You can install a second drive later.  You can even create a separate partition on it for your "/home" folder - the equivalent of "Applications and Settings" in Windows.  This can be done either at the time of installation (although I think it requires the AlternativeCD) or later:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by starcraft.man on 2007-06-11
> **peter_k said:**
> Hello all:

I am currently a Mandriva user (installed it about 5 days ago), but am thinking of switching to Ubuntu.  I had a couple of basic questions I was hoping you guys (and gals) could help me with:

1. I have just downloaded the most recent version (7.04 - Feisty Fawn) from the Ubuntu website, and am planning to make an .iso of it.  Can I boot from it and try it before I install it?  Does this .iso include the same amount of software that comes with the "Ubuntu Guide" book I've seen?  I know the book has an older version (I believe 6.10), and I'm looking to buy it anyway to help me with installation and use, but I wanted the latest Ubuntu version, and wasn't sure how hard upgrading after the fact would be.

[COLOR="Red"]If you downloaded the "Desktop Version or Live CD" ISO (it's named one of those), then yes you can boot right into it and try it live. I don't know what book your talking about, Ubuntu comes preinstalled with firefox openoffice, the GIMP, and a whole host of other basic function programs. It is very easy to add from repos all programs you desire. I don't recommend buying any books to learn Ubuntu, see end of my post for resources.[/COLOR]

2. Is it possible to specify what size the partitions would be during the install?  Mandriva defaults to 8GB for /hda1, and that is too small; I've tried changing it with gparted, but no luck yet.  I would only be looking to run Ubuntu, and Windoze is no longer on the machine, so I'm really just looking to have more room for the packages I install.

[COLOR="Red"]Yes to first question, both the live CD and the alternate installer have a manual partition option which you can use to adjust the size and number of partitions. I recommend 6-8 GB for root system, 1 GB for swap file and the rest should be designated for /home folder where you will store all your media. Of course if you have another OS to install, leave space for that deducted from Home. See end for resources.[/COLOR]

3. I currently have an 80GB hard drive, but am planning on buying a bigger one in a few weeks.  Can I install Ubuntu on the 80GB, with a nice size partition for /hda1, and then install a second drive later and be able to install my user files (mp3, documents, etc) to it?  Will this be a problem as far as saving files, or does Ubuntu handle this OK?  Or, am I better off just installing the new drive and starting from scratch with it?  If I do use two drives, is it OK if the second one is an external one (I'm assuming USB)?
[COLOR="Red"]
Yes, you can install any internal or external hard drive you like later. It will require manual mounting, please see end of post for that. It sounds to me your best option is to install to the smaller drive and then simply format (if your only using it for Linux you may want to format it as Ext3, most external come as fat32) this new drive and mount it as a media drive. Then you will be able to simply drop any files you like onto it.[/COLOR]

I realize now that is more than a "couple" of questions. :)

Thanks,

Peter Knox

My answers in red.

Resources:

1) [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") site and [psychocats]("http://www.psychocats.net/ubuntu/") for General basics. [LinuxCommand]("http://www.linuxcommand.org/") for learning the CLI/Terminal. [Ubuntu Wiki]("https://wiki.ubuntu.com/") for advanced and specific questions (also forums of course) [Linux app finder]("http://linuxappfinder.com/") for finding programs and applications that suit your needs.

2) [Info about planning partitions.]("http://www.psychocats.net/ubuntu/partitioning") [Guide to installing and partitioning from Live CD.]("http://www.psychocats.net/ubuntu/installing")

3) [Mounting drives in general.]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by peter_k on 2007-06-11
You guys rock.  Less than an hour and multiple posts already.  This community is even better than I thought.  I'm currently typing this from my LiveCD session, and there is no going back.:D  

I will be installing Ubuntu on my little 80GB, and then installing the bigger drive later.  Of course I will save my Firefox links so I can get back to this post when it's time to do it.  I will also print out the posting from starcraft.man to use as a guide.

BTW, one thing as a Mandriva user that I found especially nice is the control you have with installing/uninstalling programs.  For example, in Mandriva there are a bunch of games installed by default that I don't want, but I can't uninstall them, because they're not listed separately.  In Ubuntu, it seems everything is modifiable. 

Thanks,
Peter Knox

---

### Post by Nythain on 2007-06-11
as a side note, you can manual set mount points of other disks connected and partitioned during install...

i have two hard drives... one is what i like to call a system drive, its 60gigs and is partitioned out to contain
/boot
swap
/

then i have a second hard drive i like to call my dump drive... its 250gig and is one big ext3 partition
during install when i create the partitions on the main drive, i can manually set the second drive to mount at /data, and tell the installer to keep the info (dont format)

that way my fstab gets set up automatically during install and i dont have to jack around with creating mount points, finding device names and editing fstab post install

not sure if thats really relevant, but i dont think a lot of users know that option exists

ps, i havent tried this with an ntfs partition on a second drive, but it should work just the same, though you wont have write permission till installing ntfs-3g or whatever it is that allows you to do that, at wich point you will have to edit the fstab entry to illustrate that anyways

---

### Post by peter_k on 2007-06-11
> **starcraft.man said:**
> [Guide to installing and partitioning from Live CD.]("http://www.psychocats.net/ubuntu/installing")

starcraft.man:

This seems pretty straightforward, but I just wanted to make sure regarding one thing:

In the example, it talks about "guided" and manual partitioning methods.  The slider appears in the "guided" section, but the list of partitions, along with sizes, appears in the manual section.  When you use the manual method (which sounds like what your saying to do) and edit the size of the partition, can you INCREASE the size of /hda1 beyond what is recommended by the installer?  The only reason I ask is that gparted didn't let me do this.  If I increase the partition of, say, /hda1, and keep the swap the same size, does the installer automatically fill the rest of the drive with the other hda partition? (in other words, if I had an 80GB drive, and install recommends a 5GB /hda1 and a 3GB swap, leaving the other /hda at 72GB, if I change /hda1 to 15GB, and leave the swap at 3GB, will install automatically adjust the size of the remaining /hda partition to 62GB?)

Thanks - after I figure that out, I think I'm ready to do the install.

Peter Knox

---

### Post by ugm6hr on 2007-06-11
> **peter_k said:**
> The only reason I ask is that gparted didn't let me do this. 

I'm afraid I can't help with the manual installation - I didn't use it (I opted for Guided - largest continuous free space for ease).

But I think you must be doing something wrong with GParted if it won't let you chose whatever partition sizes you want.  I think it is always sensible to create partitions (and unallocated space if necessary) with GParted 
before starting the installer.  

If you are struggling - **and want to wipe the HD** - load GParted from the LiveCD (or even the GParted LiveCD - which is useful anyway) - and delete all the existing partitions.  Then just create the 3 partitions you want (with at least 1 ext3 for "/" and 1 linuxswap).  Then run the installer.

---

### Post by sailor2001 on 2007-06-11
after installing and loading up the apps, download filelight (in synaptics) to see how little space you actually used

---

### Post by peter_k on 2007-06-11
> **ugm6hr said:**
> I'm afraid I can't help with the manual installation - I didn't use it (I opted for Guided - largest continuous free space for ease).

How big of an /hda1 partition did that give you?  (i.e. what is the Ubuntu default)

---

### Post by ugm6hr on 2007-06-11
> **peter_k said:**
> How big of an /hda1 partition did that give you?  (i.e. what is the Ubuntu default)

There is no default.  

If you want to maintain a separate 62GB partition - create that in GParted - that can be /hda1.  Leave the rest of the HD as "unallocated space" - and the Guided - largest free space option will make a sensible swap partition (probably /hda3 - around 600MB - which is plenty - search here for multiple debates on this issue), and allocate the rest to "/" (probably /hda2 - about 17GB).

PS: Ubuntu "/" does not have to be /hda1 - it makes no difference (I have mine on /sda6).

EDIT: In case that's not clear - if you leave unallocated space equivalent to your prefered swap + Ubuntu "/", it will make a sensible allocation to swap.

---

### Post by peter_k on 2007-06-11
> **ugm6hr said:**
> 
EDIT: In case that's not clear - if you leave unallocated space equivalent to your prefered swap + Ubuntu "/", it will make a sensible allocation to swap.

And is that an allocation made with gparted prior to the install, or can it be made during the install itself?  Or is that what the Manual type is for?

---

### Post by ugm6hr on 2007-06-11
> **peter_k said:**
> And is that an allocation made with gparted prior to the install, or can it be made during the install itself?  Or is that what the Manual type is for?

Hope this is clearer:

Yes - you chose what you want for **SWAP+UBUNTU** and leave that total **unallocated** in GParted.  
The rest of the drive **must contain partition(s)** (i.e. your single 62GB partition in your example).
Then go to the Installer and select Guided - free space
Then the **Installer** will decide how to divide the unallocated space between SWAP and UBUNTU (from my personal experience - SWAP will be around 600MB).

---

### Post by peter_k on 2007-06-11
> **ugm6hr said:**
> Hope this is clearer:

Yes - you chose what you want for **SWAP+UBUNTU** and leave that total **unallocated** in GParted.  
The rest of the drive **must contain partition(s)** (i.e. your single 62GB partition in your example).
Then go to the Installer and select Guided - free space
Then the **Installer** will decide how to divide the unallocated space between SWAP and UBUNTU (from my personal experience - SWAP will be around 600MB).

I think I've got it.  UBUNTU is the same as the /hda1 I was referring to before (I realize now that it doesn't have to actually be /hda1; that's what it was in Mandriva), so what your basically saying is if I have an 80GB drive, andI want say a 20GB partition in which to install my applications, in gparted, I should allocate 60GB to a partition, and leave the rest unallocated.  When I run the Guided-free space part of the install, it will know to make my /home the 60GB, and install Ubuntu+Swap in the remaining, unallocated partition.  I would then have 20GB (minus the swap) in which to install applications.

---

### Post by ugm6hr on 2007-06-11
> **peter_k said:**
> I think I've got it.  UBUNTU is the same as the /hda1 I was referring to before (I realize now that it doesn't have to actually be /hda1; that's what it was in Mandriva), so what your basically saying is if I have an 80GB drive, andI want say a 20GB partition in which to install my applications, in gparted, I should allocate 60GB to a partition, and leave the rest unallocated.  When I run the Guided-free space part of the install, it will know to make my /home the 60GB, and install Ubuntu+Swap in the remaining, unallocated partition.  I would then have 20GB (minus the swap) in which to install applications.

Yes.  Except Guided Install won't actually make the 60GB partition into /home.
/home defaults to being contained within UBUNTU partition (e.g. /hda2).  
The benefits of a separate /home are documented elsewhere, but if you want to do that, then you either have to use Manual Install (which, as stated, I couldn't work out), or:
Use my suggestion with Guided - Free Space
Then use the advice in [COLOR="DarkOrange"]Using the new partition[/COLOR] from [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) - using the LiveCD
(but substitute "/dev/hda1" for "/dev/*UBUNTUpartition*" and "dev/hda7" for "/dev/*60GBpartition*" - obviously using the correct entries for partitions - which UBUNTU is probably hda2 and 60GB is hda1 in the example given.

---

### Post by peter_k on 2007-06-11
> **ugm6hr said:**
> Yes.  Except Guided Install won't actually make the 60GB partition into /home.
/home defaults to being contained within UBUNTU partition (e.g. /hda2). 

Ah.  Probably shouldn't have called it that.  I'm still in Mandriva-speak. :)

What I meant to say when I was saying /home was the directory where all my user files go to (documents, mp3s, bookmarks, preferences, etc.).  I'm thinking I probably don't need a separate /home directory.

Given that, then, out of the 80GB HDD, I'm looking to devote about 20-25GB for Ubuntu + any programs I wish to install.  The rest I'm looking to use for my (and my wife - only 2 users) files.  Thus, in gparted, I would allocate a 55-60GB partition, and leave the rest unallocated.  I would then selected Guided Install-->Free Space, and the remaining 20-25GB will be divvied up between Ubuntu and the Swap file(which will be rather small).

---

### Post by ugm6hr on 2007-06-11
> **peter_k said:**
> Ah.  Probably shouldn't have called it that.  I'm still in Mandriva-speak. :)

What I meant to say when I was saying /home was the directory where all my user files go to (documents, mp3s, bookmarks, preferences, etc.).  I'm thinking I probably don't need a separate /home directory.

Given that, then, out of the 80GB HDD, I'm looking to devote about 20-25GB for Ubuntu + any programs I wish to install.  The rest I'm looking to use for my (and my wife - only 2 users) files.  Thus, in gparted, I would allocate a 55-60GB partition, and leave the rest unallocated.  I would then selected Guided Install-->Free Space, and the remaining 20-25GB will be divvied up between Ubuntu and the Swap file(which will be rather small).

Yes.

If you decide you want a separate /home partition - you can always use the 60GB partition later - as in my previous post (it looks pretty easy - and the psychocats website has been 100% reliable for everything I've tried so far).

Just in case you haven't understood about /home:
Ubuntu also uses /home (just like Mandriva), but puts it inside your main Ubuntu installation partition as default.  If you're from a Windows environment - think of it as the "Documents and Settings" folder - where "My Documents", bookmarks, emails etc are stored.  The difference between Windows and Linux is that you can have it as either a folder within the main OS, or as a separate partition.  The benefits of a separate partition are fairly obvious - if you make a mess of the main partition, it is easy to restore your user settings.  I haven't (yet) bothered - but only because I backup everything to an external drive anyway, and have a short-cut to a separate "My Documents" folder in a different partition.

Hope that's clear.

---

### Post by steve.horsley on 2007-06-11
Sounds right, though I've never used guided that I can remember. I always create the partitions first with gparted, then use custom partitioning to specify which partitions to use for what. That must be the control freak in me.

Just to clarify one point - the Ubuntu installer normally only creates two partitions - swap and  "/". No separate home partition or others. This may be why you are having trouble getting good answers on the subject of the home partition. I believe [www.psychocats.net](www.psychocats.net) has a guide on installing with a separate home partition.

---

### Post by peter_k on 2007-06-11
Thanks everybody.  I will be logging out now to run gparted, and then to install Ubuntu.:D

---

### Post by peter_k on 2007-06-11
OK.  I've managed to install, but I'm really not sure if I did it right.  When I'm on the Desktop, and I look at "File System", it says I have 27GB.  This does sound about like the amount I did not have allocated in gparted; but where is the remainding space?  I'm just wondering if and how I can access the rest.  Perhaps it's hidden somewhere, but when I click on each of the user's folders, it also says there is 27.0GB.  Could this be a mounting issue, or do I need to run gparted again and reinstall?

---

### Post by peter_k on 2007-06-11
Success!

I finally said screw it, and just installed it all on one partition.  It worked!  I now have a 67GB drive with which to play.

Evidently Ubuntu just made it too easy for me...When I installed Mandriva, it automatically created the extra partition, but Ubuntu had the sense not to.  Another reason to switch.

By the way, something that I think is really cool is the Details section when you install a package.  It opens up the shell, and shows what is going on.  Very cool for us noobs, so we can get an idea what is really happening.  It reminds me of the old DOS batch file days :D

Thanks again everybody for the help.  When people ask me to recommend a distro, I will tell them Ubuntu, and one of the top reasons I will is because there is such an extensive and helpful support community.

Thanks!

Peter Knox

---

### Post by ugm6hr on 2007-06-12
Glad your happy with it.

If you're planning on a second drive for backups - there's no real need to have a separate partition on the main drive anyway.

As I said - if you're not trying to be too clever - Guided is the way forward.  As it says on the tin - it just works.

---

