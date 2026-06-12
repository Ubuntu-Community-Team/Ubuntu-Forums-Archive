---
title: "Best way to allocate partitions on new HDD?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bliffle on 2007-10-04
I've been happily running for several months on this ubuntu 7.04 (which I installed from the LiveCD onto a fresh 80gb HDD on this IBM T40 after a few days of trying it). I've also experimented with Gparted, especially when installing a dual-boot XP/Kububtu system on another computer, an IBM 570.

Now, I want to improve this T40 by populating a fresh 80gb HDD with a windows system (XP or Vista, TBD) and all the stuff accumulated in this old reliable Feisty system, and allow room to install a mythbuntu and maybe a knoppix system on the same HDD with a multi-boot.

My question is: how to allocate partitions and how to effect the directory changes?

I'd like all the linux systems to work to the same application data, which is all in "/home", as I understand it. If so, how do I move all my existing data over to the new partition: with "dd" or "pcopy" or ????

Then, how do I got the various linis (feisty, gutsy, mythbuntu) to work from that data partition?

Some people advise puting the "root" in a partition by itself. Is the "root" simply the same as "/" or is it "/root". Would the former then include "/home" or would it include everything but?

I allocated a "swap" partition but I have no idea if it is actually being used or whether the original feisty installation  ignored it and simply uses space elsewhere. How can I know?

---

### Post by ubername on 2007-10-04
> **bliffle said:**
> I've been happily running for several months on this ubuntu 7.04 (which I installed from the LiveCD onto a fresh 80gb HDD on this IBM T40 after a few days of trying it). I've also experimented with Gparted, especially when installing a dual-boot XP/Kububtu system on another computer, an IBM 570.

Now, I want to improve this T40 by populating a fresh 80gb HDD with a windows system (XP or Vista, TBD) and all the stuff accumulated in this old reliable Feisty system, and allow room to install a mythbuntu and maybe a knoppix system on the same HDD with a multi-boot.

My question is: how to allocate partitions and how to effect the directory changes?

I'd like all the linux systems to work to the same application data, which is all in "/home", as I understand it. If so, how do I move all my existing data over to the new partition: with "dd" or "pcopy" or ????

Then, how do I got the various linis (feisty, gutsy, mythbuntu) to work from that data partition?

Some people advise puting the "root" in a partition by itself. Is the "root" simply the same as "/" or is it "/root". Would the former then include "/home" or would it include everything but?

I allocated a "swap" partition but I have no idea if it is actually being used or whether the original feisty installation  ignored it and simply uses space elsewhere. How can I know?

Hi 

Newish Ubuntu user here, but to offer some advice:

I doubt I need to say this, but first backup. Then make sure you can restore. I have just had a nightmare (sort of) trying to 'restore' my wife's email to Thunderbird from Outlook express because the CD I had burned  of her email had errors on it (and I had already trashed Outlook express. - Doh!). Check that you can restore, please!

You're right to install windows first, I couldn't get Windows loaded onto an Ubuntu machine.

If you want to have multiple distro's all accessing the same /home partition I think you should put  "/" on other partitions (one for each distro) from "/home" (if you do that it will make "/home" independent of any of the distros.)

Allow at least 5 (possibly 10) Gbytes for Ubuntu Gutsy "/" partition (don't know about other distros). I used  <4Gb for Gutsy and have had space problems (solved with sudo apt-get autoclean and sudo apt-get autoremove)

Don't forget you can only have 4 primary partitions on a physical drive. I don't know the pro's and con's of primary v. logical partitions, so maybe have a primary partition for windows, one for linux, one for linux swap, and then put all your distros and home  into logical partitions in the primary linux partition.

Something else to think about: Maybe you want to access email (thunderbird e.g.) or share browser settings (firefox e.g.) between both windows and linux. I have achieved this by having these data on an NTFS partition (so in the windows partition suggested above) and then using one of the many ways of accessing NTFS (Read / Write) from Ubuntu / Linux. If you want to do this you may want to think about how you size your NTFS partition.

Finally, you can check your swap file usage from the system log ( Normally "System>Administration>System Log" then select the "Resources" tab)

Good luck.

---

### Post by bliffle on 2007-10-04
I always backup by parking the old HDD in a  safe place and then install to a fresh HDD.

I did the email thing from Outlook Express to Thunderbird soon after I switched to ubuntu and it went almost perfectly. I see no reason to go back to OE or to even share the email database between OE and Thunderbird. I maintain secondary email addresses at Yahoo, Hotmail and Google for flexibility and backup. 

I think you're right, that one MUST install windows first. that's the only way I was able to get things going on the second computer.

And this business of 'extended' vs. 'primary' partitions brings up the question of how best to use  those 4 primaries best.

Now when I install, say, mythbuntu in an 'extended' partition (if I can), then won't it automatically create a new "/home" within that partition? How do I get it to use the "/home" that I allocated in (say) an extended partition somewhere? That way I'd have access to the same email history and the same personal data from any linux on the HDD.

Can a linux be booted from an "extended" partition, or must it be in a primary partition?

---

