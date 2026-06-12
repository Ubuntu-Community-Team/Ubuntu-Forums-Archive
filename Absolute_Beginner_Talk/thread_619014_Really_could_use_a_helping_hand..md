---
title: "Really could use a helping hand."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by tomcullpepper on 2007-11-21
So I just downloaded and burned Ubuntu.  I burned it once at maximun speed, and again at the slowest speed using InfraRecorder on the Burn Image command, both copies fail to install and boot Ubuntu properly.  I checked both CDs for errors, none, I have no idea what it could be.  During installation it gives me three errors, despite moving onto the next step anyway, one says "No such file or failed to load" and another says something about a "microbit error" the other says "no buffer space"  I really want Linux on this computer, but I'm stuck, one FAQ said soemthing about an alternate CD, what is all that about?  Also, it gives me a black screen after moving past the text portion of the installation, the black screen doesn't turn into anything interesting.

I am currently using an HP 6000 series notebook, AMD Turion X2 core 1.8 GHZ with an Nvidia Go 6150 graphics card.  I have a total of 2567 Mb of RAM, 2 gigs on DDR and the final bit on the card.  Also I am running the dreaded Windows Vista.

---

### Post by stanigator on 2007-11-21
The alternate CD is the one that you use for upgrades from my knowledge. Did you try burning a different CD for Ubuntu? Also did you try ordering a copy of the official CD from Canonical for free for future use until April? Your hardware should be able to support Ubuntu, as I'm using Ubuntu on a much less powerful machine right now. I personally tried installing under manufacturer mode and worked ever since then.

---

### Post by siciliancasanova on 2007-11-21
Are you planning on dual booting or just running Ubuntu?

---

### Post by antisocialist on 2007-11-21
it is likely that your download didnt complete or was invalid (md5checksum not right) if you didnt check this before burning then that cold be your problem

---

### Post by freesitebuilder on 2007-11-21
The alternate CD is one that uses the terminal rather than a graphical interface, for machines that can't run the standard desktop installation. Here's some info: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It also has a lot of other info on installing which may help you.

---

### Post by dark_harmonics on 2007-11-21
I use the alternate CD for installs. I dont like waiting for the live CD to boot. The live CD is nice for testing Ubuntu out but I just want it to install. 

The errors you are having sounds like a bad download or a bad cd burn. I've done installs on an hp nc6000 before without an issue (integrated graphics).

On my MacBook Pro i needed to use the alternate cd and then load restricted video drivers in a terminal before booting into the gui.

---

### Post by Sef on 2007-11-21
The alternate cd is fairly easy to use.  Check out the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") for how to install by using the alternate cd.   If you are not dual booting, then skip the parts about NTFS partition.

---

### Post by Jittoku on 2007-11-21
I've been surprised at how often burning errors pop up.  I had errors on three disks out of five that I burned of different ISOs (fluxbuntu, xbuntu, gutsy) over a couple of days.  MD5 checksum was okay, but the disks didn't check internally, and all of them hung on attempted install.  

It seemed to be a problem with burning at high speed.  I noticed something after the 5th burn - even though I was checking 1x speed on InfraRecorder, it was still burning at the maximum speed of the disk.  I expect I'm doing something wrong, but I don't see what . . .  Anyway, I switched from the 52X disks (which IR burned at 42X, or something) back to the 1-4X disks, and got good burns.  I still check 1X, and it still burns at 4X.  But it seems more reliable.

---

### Post by smartbei on 2007-11-21
If the MD5 checksum was okay, something else is wrong - or perhaps you aren't checking the disk with md5, rather the ISO (which you should also check of course - before burning).

Besides, the OP didn't say he wanted to use the alternate installer, which we have no reason for thinking would solve his problem.

---

### Post by tomcullpepper on 2007-11-21
for those following along, I want dual boot, should have said that as it is extremely important.  How do I partition my HD?  Is partinioning the same thing as having two harddrives only, you are splitting one into several independant sectors?  I'll try the alternate CD when I get a new disk....  Isn't there a windows based exe program for ubuntu, there should be a one touch for windows where it partitions, installs, and reboots, I'm sure I'm not hte first frustrated future user who has thought of this.

---

### Post by freesitebuilder on 2007-11-22
I found GPartEd very easy to use - deciding how much space to allocate was hardest for me, as I'm an old fogey who thinks a megabyte is 1024 bytes. I didn't realise that the European parliament or someone has decided that mega=1000, therefore a megabyte MUST be 1000 bytes! :(

I found this documentation good: [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by Edgy Eft Fan on 2007-11-22
yes thats exactly what patitioning is and the ubuntu installer does it for you, when you go through the installer, it gives you a slider option to choose how big to make the partition for windows and ubuntu

---

### Post by midgemiles on 2007-11-22
Have you read [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")? I find the resources I need to solve problems can be found by using search engine (especially google) with "ubuntu" as first word, and a brief phrase to do with your issue to follow.

---

### Post by tomcullpepper on 2007-11-22
> **midgemiles said:**
> Have you read [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")? I find the resources I need to solve problems can be found by using search engine (especially google) with "ubuntu" as first word, and a brief phrase to do with your issue to follow.

searching for anytyhing on google, with anything as obscure as ubuntu will get me search results for italian or ethopian baked beans.  It's a useless search enginge now, with too much advertising. :mad:

Thanks for all the docs everyone, I'm not sure if Sabayon Linux does the same auto partinioning, or if ubuntu does it at all, so to prevent me getting pwned I'll just read the docs frist before inserting DVDs and screwing myself forever.  :lolflag:

Also, I've given ujp on my burned CDs and acquired a dvd of sabayon, so I'll be using that instead, so hopefully it does have an auto partition, as partitioning sounds like it can ruin your day if done by someone who has no idea wtf theyre doing (me, for instance) so yeah, thanks again.  I'll hop over to the sabayon forums and ask if they have auto partition.

---

### Post by tomcullpepper on 2007-11-22
Well I did want to run Ubuntu, but I got my hands on Sabayon first, so yeah....  I got sabayon to work not by using the alternate CD, or the text installer, but ny using the graphic installer!  What the hell!  The one thing no one would have told me to do =]

---

