---
title: "Dapper Drake reclaim project--end of trail?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by drifteryank on 2007-11-22
I recently decided to investigate Ubuntu as a reclaim project for an unused 10-year old Dell desktop.  It has the original 266 MgHz processor but upgraded hard drive (60GB) and RAM (256 Mb).  I believe I am at the end of the trail for Dapper on this unit.  I have picked up much helpful information from this forum.  Hopefully, these comments may be helpful to others.  And, if someone has tips they feel warrant me not yet giving up, I am open to suggestion.

Following are my experiences in chronological order:

I was initially unable to get the Dapper LiveCD to run.  Problems included several error messages.

&#8226;	Dapper Live CD wouldn&#8217;t run after changing BIOS setup to boot from floppy to CD.  First error message was &#8220;Unable to locate RSDP&#8221;.  I got past this by hitting F6 and entering &#8220;acpi=off atapi on&#8221;, thanks to Forum entry by xuejm1225.

&#8226;	 Per Forum comments, I updated BIOS.  The latest BIOS is two versions newer than the original I was running.  The Dapper Live CD now ran.  

&#8226;	After tinkering with Dapper (Live CD) and connecting by Ethernet directly to my wireless router I connected to the Internet.  I have used Firefox for years but found it very slow.  I downloaded Opera and found it to be almost twice as fast.  I tinkered with Open Office and found it acceptable.  I still had, and continue to have, a boot message, &#8220;[126.754976] PCI: Failed to allocate mem resource #6:400000@fd000000 for 0000:01:00.0&#8221;  Forum comments seem to point to old hardware.  I am not interested in spending money for new hardware on an old computer beyond the wireless card mentioned below.

&#8226;	I reformatted the 60GB hard drive and installed a dual boot of Windows 2000 and Dapper Drake.  I used Dapper&#8217;s default dual-boot partitioning for set-up.

&#8226;	I added a Belkin F5D7000 Desktop Wireless G Card, Version 5100 to try to operate remotely.  (This was recommended for Linux in a recent article.)  I was unable to get the Belkin Install CD card to run under Dapper due to a message, &#8220;Couldn&#8217;t display &#8216;/media.cdrom0/FILES/SETUP.EXE&#8217; &#8221;.  I ran the Belkin Install CD under W2k.   It installed and I connected wirelessly under Windows 2000.  I rebooted to Dapper and, to my surprise, I was able to connect to the Internet under both Firefox and Opera.

&#8226;	The day after installing the wireless card, however, I am no longer able to connect to the Internet wirelessly under Dapper.  (I can under Windows 2000, however.)  I don&#8217;t know if one of the numerous Ubuntu updates messed this up or what.  And, I have not been able to figure out how to check the wireless connection and signal strength under Dapper.

&#8226;	It looks like I am at the end of the line regarding the amount of time I am willing to put into this.  Unless there are some other ideas, I plan to uninstall and reformat the Dapper partition to be merged with the Windows 2000 partition.  I am disappointed, but then this is a 10-year old machine.  It looks like this may be my first and last post on this forum.  Any encouraging comments will be appreciated.

---

### Post by p_quarles on 2007-11-22
So, the only problem is the wireless connection, right? (by the way, that's  "only" in the sense of "one," not in the sense of "small")

Anyway, I can think of two things here:
1) In order to install a Windows wireless driver, you will need to use a package called ndiswrapper. You didn't link to the article that suggested your card, so I don't know if you've tried this already. 

2) Try the newest version of Ubuntu (7.10 Gutsy Gibbon). It's not much more resource intensive, and the out-of-the-box support for wireless cards is improved. Given your system's specs, I would suggest the "light" version of Ubuntu: Xubuntu. 

Hope this helps.

---

### Post by Paulmd on 2007-11-23
> **drifteryank said:**
> I recently decided to investigate Ubuntu as a reclaim project for an unused 10-year old Dell desktop.  It has the original 266 MgHz processor but upgraded hard drive (60GB) and RAM (256 Mb).  I believe I am at the end of the trail for Dapper on this unit.  I have picked up much helpful information from this forum.  Hopefully, these comments may be helpful to others.  And, if someone has tips they feel warrant me not yet giving up, I am open to suggestion.

Following are my experiences in chronological order:

I was initially unable to get the Dapper LiveCD to run.  Problems included several error messages.

•	Dapper Live CD wouldn’t run after changing BIOS setup to boot from floppy to CD.  First error message was “Unable to locate RSDP”.  I got past this by hitting F6 and entering “acpi=off atapi on”, thanks to Forum entry by xuejm1225.

•	 Per Forum comments, I updated BIOS.  The latest BIOS is two versions newer than the original I was running.  The Dapper Live CD now ran.  

•	After tinkering with Dapper (Live CD) and connecting by Ethernet directly to my wireless router I connected to the Internet.  I have used Firefox for years but found it very slow.  I downloaded Opera and found it to be almost twice as fast.  I tinkered with Open Office and found it acceptable.  I still had, and continue to have, a boot message, “[126.754976] PCI: Failed to allocate mem resource #6:400000@fd000000 for 0000:01:00.0”  Forum comments seem to point to old hardware.  I am not interested in spending money for new hardware on an old computer beyond the wireless card mentioned below.

•	I reformatted the 60GB hard drive and installed a dual boot of Windows 2000 and Dapper Drake.  I used Dapper’s default dual-boot partitioning for set-up.

•	I added a Belkin F5D7000 Desktop Wireless G Card, Version 5100 to try to operate remotely.  (This was recommended for Linux in a recent article.)  I was unable to get the Belkin Install CD card to run under Dapper due to a message, “Couldn’t display ‘/media.cdrom0/FILES/SETUP.EXE’ ”.  I ran the Belkin Install CD under W2k.   It installed and I connected wirelessly under Windows 2000.  I rebooted to Dapper and, to my surprise, I was able to connect to the Internet under both Firefox and Opera.

•	The day after installing the wireless card, however, I am no longer able to connect to the Internet wirelessly under Dapper.  (I can under Windows 2000, however.)  I don’t know if one of the numerous Ubuntu updates messed this up or what.  And, I have not been able to figure out how to check the wireless connection and signal strength under Dapper.

•	It looks like I am at the end of the line regarding the amount of time I am willing to put into this.  Unless there are some other ideas, I plan to uninstall and reformat the Dapper partition to be merged with the Windows 2000 partition.  I am disappointed, but then this is a 10-year old machine.  It looks like this may be my first and last post on this forum.  Any encouraging comments will be appreciated.


Do not despair.

Some notes to make your life easier:

Openoffice is a bit resource hungry: if you don't need all the features of a fulll office suite or compatibility with Word or WordPerfect, abiword is a lighter-weight solution.

Dapper has very limited compatibility with wireless, as may have already been pointed out. A later OD may be indicated. (Fiesty/gutsy) Gutsy seems to be having some issues with old machines, so perhaps fiesty Xubuntu would work better.

Aviod spending money, after all, it's a 10 year old machine. If it comes down to it, you could put the 60 GB drive in an external usb enclosure, and use it for a backup hard drive.


In terms of MS OSes, win2k is the most recent that that machine can reasonably manage. (XP is POSSIBLE, barely, but not recommended )

On the linux side, there is Damn small linux, and puppy linux, that may be acceptable alternatives to ubuntu.

---

### Post by drifteryank on 2007-11-23
Thank you for the comments.  

Re. p_quarles comments: Yes, wireless is the main problem.  (Or, is it my  limited knowledge of Ubuntu?)  I have not tried ndiswrapper.  But, here is a link to the article about the Belkin wireless card [http://blogs.techrepublic.com.com/wireless/?p=128[/URL] .

Sounds like "Gutsy Light"/Xubuntu might be a more comprehensive solution.

If I try Xubuntu how do I uninstall Dapper?  I have been unable to load Dapper's default partitioner since the original install from Live CD.  I  have not been able to see the Dapper partitions if I need to reformat them.

Thanks again.

---

### Post by louieb on 2007-11-23
Sound like you have a Pentium II. CPU. to confirm ```
cat /proc/cpuinfo
```  P2 CPUs are dirt cheep (like $5 - $10 or free if your nice).  Look around and see if can find a 400mHz or higher. One plus if your motherboard is like mine the buss speed jumps from 66mHz to 100mHz too.  I've got a P2-400mHz 384 MB ram (started out as a P2-266mHz)  With the faster CPU + the increase buss speed -  That rig did a pretty decent job of running Dapper.  It has XP too but it is slow. Same for xUbuntu Gutsy (slower than Ubuntu Dapper). 

No matter what OS you end up using the CPU upgrade is well worth the price.  BTW: Now running  [PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/") Good luck with getting your wireless going.

---

### Post by p_quarles on 2007-11-23
> **drifteryank said:**
> Thank you for the comments.  

Re. p_quarles comments: Yes, wireless is the main problem.  (Or, is it my  limited knowledge of Ubuntu?)  I have not tried ndiswrapper.  But, here is a link to the article about the Belkin wireless card [http://blogs.techrepublic.com.com/wireless/?p=128[/url] .
Yeah, given that the driver you mentioned is a Windows file (ending in .exe). I've never used it myself, and my understanding is that it can be kind of a pain, but it gets good results in most cases. Here's a tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

> Sounds like "Gutsy Light"/Xubuntu might be a more comprehensive solution.
Definitely worth a try. Wireless support is much better in the current version, and you may be able to avoid the need for installing ndiswrapper manually. Don't quote me on that, though. ;)

> If I try Xubuntu how do I uninstall Dapper?  I have been unable to load Dapper's default partitioner since the original install from Live CD.  I  have not been able to see the Dapper partitions if I need to reformat them.
The installation disk itself can wipe the current partition during installation process. If you wish to keep the current dual-boot setup, you'll need to choose the "manual partitioning" option, choose the current Ubuntu partition, click "format," and then select "/" as the mount point (which means that this partition will be mounted as the root filesystem).

---

### Post by Paulmd on 2007-11-23
> **louieb said:**
> Sound like you have a Pentium II. CPU. to confirm ```
cat /proc/cpuinfo
```  P2 CPUs are dirt cheep (like $5 - $10 or free if your nice).  Look around and see if can find a 400mHz or higher. One plus if your motherboard is like mine the buss speed jumps from 66mHz to 100mHz too.  I've got a P2-400mHz 384 MB ram (started out as a P2-266mHz)  With the faster CPU + the increase buss speed -  That rig did a pretty decent job of running Dapper.  It has XP too but it is slow. Same for xUbuntu Gutsy (slower than Ubuntu Dapper). 

No matter what OS you end up using the CPU upgrade is well worth the price.  BTW: Now running  [PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/") Good luck with getting your wireless going.


It could still be a p1. 266mhz is the top p1.

If it IS a p2. Then the chances are good that you can put a p3-450 in there. You'll want to update the BIOS, but Dells are good about making that painless.

---

### Post by drifteryank on 2007-11-23
It is a P2.  I ordered it new in 4/97.  Several years ago, I upgraded to the 60GB hard drive and 256 Mb of RAM when I ran out of operating space on the original 4GB drive.  Then, I gave it to my daughter for a second computer.  She offered it back to me recently (complete with 6 Trojans) rather than donating it.

---

### Post by drifteryank on 2007-11-25
Based on forum comments about my project, I thought I would try Feisty Xubuntu.  (There seem to be quite a few issues, including speed, with Gutsy light on old machines.)  But, I can't get the download I burned to a CD to boot. I burned the "standard download": Alternate Install CD for Mac (PowerPC) and IBM-PPC (POWER5). None of the other alternates remotely fit my system description.  

What am I doing wrong?

---

### Post by p_quarles on 2007-11-25
> **drifteryank said:**
> Based on forum comments about my project, I thought I would try Feisty Xubuntu.  (There seem to be quite a few issues, including speed, with Gutsy light on old machines.)  But, I can't get the download I burned to a CD to boot. I burned the "standard download": Alternate Install CD for Mac (PowerPC) and IBM-PPC (POWER5). None of the other alternates remotely fit my system description.  

What am I doing wrong?
That's certainly not the right disk for your computer. The disk for the Pentium II architecture is the standard disk: i386

---

### Post by Bigbird999 on 2007-11-25
FWIW I am running my Armada E 500 Laptop, dual boot with Gutsy and Win2k.  Wireless was a PITA to get working on Gutsy (due to noobiness), but works now with ndiswrapper.  Performance (speed etc) is the same, **not better, but the same,** as win2k.  Also Gutsy doesn't do the suspend hibernate things (a known issue - many threads-  in Gutsy, which I guess they will eventually fix) that 2K does effortlessly.  So, all in all, for me, 2k beats Gutsy , at least so far.

I am persevering with Linux as a hobby/learning experience, but I don't expect any miracle, performance improvements.  It is just an alternative to a pretty good OS (Win2k).  

If you can add more memory ( I went from 320 MB to 512 for about $40) you will get a major performance improvement on both Win2K and any Linux flavour.  

BB

---

### Post by rustybronco on 2007-12-01
> **drifteryank said:**
> Based on forum comments about my project, I thought I would try Feisty Xubuntu. 
What am I doing wrong? Nothing...pick a -386.iso release, live cd (desktop) or alternate
[http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by drifteryank on 2007-12-01
Well, I tried both the Feisty and Gutsy versions of Xubuntu and never managed to get my wireless going again.  So, I have removed the dual-boot and repartitioned to run only Windows 2000.

I appreciate the help from the Forum.  Maybe I will tinker with this again some time.

---

### Post by rustybronco on 2007-12-01
> **drifteryank said:**
> &#8226;	I added a Belkin F5D7000 Desktop Wireless G Card, Version 5100 to try to operate remotely.  (This was recommended for Linux in a recent article.) 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)
looks like it works to me, could you see the networks in the network manager icon?

> **drifteryank said:**
> I was unable to get the Belkin Install CD card to run under Dapper due to a message, &#8220;Couldn&#8217;t display &#8216;/media.cdrom0/FILES/SETUP.EXE&#8217; &#8221;.   thats because it's a windows .exe file they don't work on linux, but you can install ndiswrapper and use the .inf and .sys files located on that cd also.

---

