---
title: "Triple Booting Help...from a Newb to a Newb"
date: 2008-10-12
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2008-10-12
While the standard Ubuntu Community Macbook Pro WIKI is pretty effective (click here: [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro")), it seems to be a mere quick guide to triple booting. I'd like to outline a few pointers which may help people when doing this so they don't have to run into as many snags along the way!

[LIST=1]
[*]**Not all Ubuntu flavors are created equal! - **This may seem obvious to the more experienced users, but to newbies of Ubuntu (such as myself), this isn't so clear. There are several different types of Ubuntu ("vanilla" Ubuntu, Ubuntu Studio, Xubuntu, Ubuntu JeOS, and a few dozen more!), and all are specific to different uses or needs. Make sure you do some research if you decide to use anything other than Ubuntu "vanilla." My first installation was Ubuntu Studio, and after many a battle with getting wireless to work, I found out that many people had found issue with wireless in Ubuntu Studio. So don't just research its uses/packages/etc...also research it's quirks/glitches/issues. This could save you a lot of time in the end if you can find a way to make Ubuntu "vanilla" work like the particular Ubuntu flavor you're eyeballing.

[*]**Windows is easily p***ed off! - **Triple booting with a Macbook Pro can be easier than it might seem. However, in one Triple Boot instruction outline in the above-mentioned Wiki, it mentions how to create a Mac OS X/Ubuntu/Windows XP configuration (that's the physical organization). They state that you should first divide your Mac OS X partition into two, and then install WinXP on the second partition. It then states to divide the Mac OS X partition even further and install Ubuntu on the resulting partition. **THIS IS A BAAAAD IDEA!** Here's why: for reasons a bit too technical for me to comprehend, Windows XP doesn't like being moved around (I can't speak on Vista, though). If you install XP on one partition, then lodge another partition between the Mac OS and the Windows XP partition, then you alter where the Windows XP is on the partition map (usually, you are moving it from sda3 to sda4). Windows XP might decide to no longer work after this. There are two solutions that I've found effective:

1. Instead of making one partition at a time, make all three in one go using Disk Utility. Maintain your first partition (unless this is a fresh install, in which case format it in HFS+ or whatever you use for Mac OS X), format your second partition with the name LINUX in HFS+ (for the reason outlined in the tutorial above), then format your third partition as FAT32 (this can/will be changed when Windows installs to NTFS). This whole process may freak out Boot Camp (if ever you use the Boot Camp GUI at startup, it won't work because it will look for Windows and find Linux instead, stating "Error Loading Operating System"), but no worries because you're using rEFIt (or some other boot loading alternative). Install Windows first, then Ubuntu...although I don't think this order makes a difference.

2. You've already done it? Well then, back up WPA.DBL and WPA.BAK (if you've already activated) then do a Repair Install. This link will help you with all of this: [http://www.aumha.org/win5/a/wpa.php]("http://www.aumha.org/win5/a/wpa.php")

[*]**Wireless can be a pain! - **There are three possible solutions to the whole Macbook Pro Wireless problem:
ath9k - Search the forum or the above mentioned WIKI. This seems to be the easiest to do (use the .deb located lower on the page). However, it also seems to be the least reliable. Only some people have reported succes.
MadWifi - Current MadWifi drivers are not effective, but older drivers seem to work for a lot of people. However, if you're someone like me who has no internet other than wireless, this "rollback" method is useless...leaving
ndiswrapper - this is a program which takes non-free Windows drivers and "wraps" them in Linux clothing (that's not a technical explanation, of course, but I don't really understand the ins and outs of this program enough to pass on to you...it's not all that important either). This has been what has wound up working for me.

[*]**MAKE SURE YOU WRITE DOWN WHICH PARTITION TO WRITE GRUB TO! - **I accidentally wrote GRUB to the Mac OS X partition instead of the Ubuntu one. Long story short, I lost a day to backing up and restoring Mac OS X, then Windows XP, then Ubuntu.

[*]**Finally, ext2 is your friend if you want Mac OS to communicate with your Ubuntu partition - **Ubuntu defaults on formatting a new install partition to ext3 file system. However, I have learned that ext3 is nothing more than ext2 with journaling. And basically what that means is that if Ubuntu shuts down improperly with an ext2 file system, it has to run this tedious program known as fsck. So why would you use ext2, then? Well, Mac OS X has the ability to communicate with ext2 (with very limited success communicating with ext3) with the help of a certain SourceForge project. I've even been told you can enable journaling with an ext2 file system using a program named tune2fs (provided in your LiveCD, apparently, but I haven't had a chance to implement this solution into Ubuntu).
[/LIST]

Triple Booting is certainly not something for the newest Ubuntu user to attempt. However, as in my case, sometimes you need to learn the process fast. With the help of many people in this forum and through my own experiences, I have learned these things that have proven helpful. So hopefully my (limited) wisdom can help you, too, triple boot your Macbook Pro!

Oh, and as a side note, it might help you to invest some time in creating a virtual machine with the Ubuntu flavor you're using. This allows you to test solutions to specific issues before you apply said solutions to your ACTUAL Ubuntu OS. Also, if you don't have wireless working in Ubuntu (and, like me, wireless is your only internet access point), you can use apt-get or aptitude within the virtual machine, then use APTonCD to burn your packages to a CD or .iso for use on your ACTUAL Ubuntu OS (the upside to this is that apt-get resolves any dependency issues you may run into...the packages repository website can be far to complex to help with downloading these packages). Here are some options, both freeware and commercial, for creating virtual machines:

[VMWare]("http://www.vmware.com/") - I haven't worked with this one, but have heard good things. I think this is available for Windows OR Mac OS X.
[Parallels]("http://www.parallels.com/") - I love this one, and it's relatively cheap ($80). However, I think this is exclusive to Mac. And, also, the support forums suck...undoubtedly so that you HAVE to call their help hotline.
[VirtualBox]("http://www.virtualbox.org/") - As far as freeware goes, this works pretty well. It's available for a number of different platforms (Linux, Mac, Windows and Solaris). The only one I've used is for Mac, and it tends to be a little glitchy (nevermind the fact that you can't move it to a different folder or it doesn't work).

Anyhow, there's my two cents. Hope I help someone with all of this. Latah!

---

