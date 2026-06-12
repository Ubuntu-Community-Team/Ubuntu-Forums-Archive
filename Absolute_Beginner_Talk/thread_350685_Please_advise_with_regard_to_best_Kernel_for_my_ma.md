---
title: "Please advise with regard to best Kernel for my machine"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Grungydan on 2007-01-31
Hello all.  (First post! :))

Okay.  I bought and have read the official Ubuntu book (and it's great), and I've poked around just a bit in both Ubuntu and Kubuntu liveCDs of Dapper.  I have also done quite a bit of general reading on the web.  I'm trying to decide what to go with so that I can set my machine up to dual boot U/Kubuntu and XP Pro.  I basically want to get to where the only time I use Windows is for the few games that I can't convince to run in Linux.

That said, I'm trying to figure out which installation/kernel I need for my machine.  I did some searching around the forums, but the post I found that seemed to be most applicable was a bit out of date.  I apologize if this comes up a lot, I just couldn't get my searches to turn up what I was looking for.  

I'm running a dv9000t Core 2 Duo (2.0GHz) based HP Pavillion notebook.  Do I use the AMD64 kernel?  A post I read seemed to indicate that this was the case, but there was a lot of other information that left me a bit confused.  

I have the liveCD for both Ubuntu and Kubuntu Dapper (I'm still debating on GNOME or KDE as my initial environment, although I may well install both in the future), but they're probably the 32bit versions, since I just used the big shiny download links to get the ISOs.

I think I'll be okay when it finally comes time to install.  A lot of web browsing and just a general willingness to try random things until they work helps a lot, I've found. :)  I have no doubt that I'll be perusing these forums much more once I'm up and running. 

Thanks in advance for any information and advice.

---

### Post by tchoklat on 2007-01-31
One point worth noting is that if you have a a 64 bit processor you can run either. If you are unsure as to your processor install the 32 bit version.

You should install edgy - as it is the latest and remains supported. There are a few gliches - but nothing this forum cannot address.

Try the Ubuntu version, you can then install Kubuntu as well giving you the option of either.

Installing with the live-CD of either will allow you to partition your HDD allowing XP to run on it's own partition. You can then resize the partitions with GPartEd available from the repositories.

The liveCD will set up XP and (K)Ubuntu with a GRUB screen at boot-up offering the option of XP or Linux


Good luck!

Tony

---

### Post by Tux Aubrey on 2007-01-31
The -generic 32 bit kernel works for all PCs.  The old distinction between 386 and 686 kernels does not exist anymore, so go with -generic.

I gather the 64 bit version of Ubuntu is still a bit bleeding edge (and that some common apps don't have 64 bit versions yet anyway).  

So I'd suggest dual booting 32 bit K/Ubuntu with your current XP setup.

You could try the 64 bit version at a later stage (that's what I intend to do)

Welcome (and congrats on doing some homework first!)

---

### Post by Grungydan on 2007-02-01
Tux, I kinda got the same impression about the 64bit kernel from reading around here.  Am I losing a lot of performance by using a 32bit kernel though?  I dread finding out that I'm only using one core or something like that.  

tchoklat, regarding Edgy vs. Dapper, I am under the impression that while Edgy is the "current" release, and is the one that will be updated on the 6 month cycle, Dapper is the "long (18 month) support" version, and is also favorable to a new user due to it having been around for a while and being "tried and tested".  Is this incorrect?  It occurs to me that I get this impression from the Ubuntu book, but I now wonder if that 18 months is almost up?  (I forget the publishing date for the book, it might be older than I thought.  Come to think of it, I think Dapper was "new" when the book was published.)

With regard to support, I assume the community support (forums/chats/etc) will still apply to Dapper for quite some time, and that Support™ (as in paid, etc) now applies to Edgy?

I saw a couple of people with 64bit "helper" programs and scripts in their signatures.  Are those still current and necessary when doing a 64bit install, or have the issues that they addressed been fixed in the installation?  

Also, regardign GParted, I tried running it off of the LiveCD (both version 3.0 and 3.3) and it won't boot for some reason.  I know this isn't really a GParted forum, but has anyone else had experience with this program?  I'd like to repartition and resize my drives prior to installing U/Kubuntu, just so I feel better about the installation.  I have 2 80GB SATA drives partitioned as OS, Data, and Recovery (a 10GB HP crapware partition; I have made the recovery disks and would like my HDD back now).  I was thinking that I could resize the XP (NFTS) partition, create a partition for U/Kubuntu, and then try and make a partition that both OSs can read (Fat32, I think?).  Any thoughts?

Ha.  Full of questions.  Thanks again, all.  :D

---

### Post by Shatrat on 2007-02-01
There is a copy of Gparted on the Ubuntu LiveCD, although if you cant boot the gparted knoppix thingamajig you might have trouble booting the ubuntu liveCD as well, and im not sure what formatting options there are on the alternative install CD.

The -generic configured kernel that is used by default is supposedly pretty good, and should pick up your dual core setup on its own.  You can check this easily in a running system by checking /proc/cpuinfo, there should be a "processor :0"  and a "processor :1"

There are lots of benchmarks out there comparing 64 bit OSes and 32 bit ones.  Generally the difference is only a few percent, and sometimes the 32 bit wins.  The drawback to 64 bit is that lots of non open source stuff is a pain to get working. Open source stuff can usually easily be recompiled and packaged for 64, but with proprietary stuff like Flash and video drivers and so forth you have to hope that the maker is nice enough to provide 64 bit stuff as well.


{edit}
> and then try and make a partition that both OSs can read (Fat32, I think?).
Linux can read (and write, but not 100% safely) ntfs.  Fat32 is pretty bad, especially if you are gonna be putting big files on it.  The solution I use is to use the windows driver from fs-driver.org to read/write my ext3 Ubuntu partition, and keep all my media and documents on the ubuntu partition.

---

### Post by Tux Aubrey on 2007-02-01
> Am I losing a lot of performance by using a 32bit kernel though? I dread finding out that I'm only using one core or something like that.

The performance drop is unlikely to be major and both my dual core machines run both processors.  The 32 bit generic kernel is pretty well proven and once you have edgy (or dapper) running you can keep track of 64 bit developments on the forums.

By the way, edgy has been fine for me - no real problems at all.  I do note that some people do find problems with it that they didn't get in dapper.

---

### Post by Grungydan on 2007-02-01
Thanks again for all the info.

I think I'll go with -generic since you give it the Dual Core Vote of Confidence. :)

I'm not entirely sure about the partitioning thing.  I think I understand it okay, but I'm confused as to the difference that would come up between partitioning prior to installing Ubuntu and partitioning as part of the installation procedure.  I was going to partition before, but no go on GParted (which is odd, as I can run the Dapper LiveCDs just fine; although I can't seem to get the Edgy LiveCD to boot).  

I wanted to do the partitioning beforehand just to have more control over the space.  Does it not matter if I do it before or during?

---

### Post by tchoklat on 2007-02-01
GPartEd is the partitioner used by the LiveCD. I ws in your shoes and I let GPrtEd partition for me. I was then able to amend the partitions by booting to GPartEd on a CD.

The first Edgy LiveCD I downloaded would not boot either. Reburn the ISO and if that does not work download the ISO again.

Good luck

Tony

---

### Post by Grungydan on 2007-02-01
Cool, I'll try that.  Thanks again!

---

### Post by Armor on 2007-02-01
If you want to dual boot XP/Ubunto, here's what you'll do:
Reboot with CD in so that LiveCD runs then use the file on the desktop to begin installation.
When you get to the part where you are selecting partitions and what not, you want to MANUALLY setup partitions. You should only see like 1 ntfs partion that your XP is located on. It may show something like "40 gigs used and 20 free" I forget how exactly it displays, but it tells you how much is free. You're going to want to select this, then resize it. There will be a button at the top left I think that can help you do this. When resizing it, you want to free up at least 10gb of space for Ubuntu. When that's done, it will show your ntfs Windows partion (obvioulsy will show smaller size now) and a second partition that will reflect the size you designated to free up from the Windows partition. Click on this, then you need to make 2 new partitions. Do this by clicking the button in the top left. You want to create what's called a "swap" partition of about 500 megs. The middle set of numbers is going to be the size you want to edit, just set it at 500. On the right (I think it's the second option down) you want to click to pull down the menu and select "swap" then click ADD. There, that is how you make your swap partition. Do the same process again for your main Ubuntu partition, but this time you won't have to change any numbers or anything else just click on what's left of the unused partition and open that box thing and click ADD then you are done and can proceed to step 6

---

