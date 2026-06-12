---
title: "[SOLVED] Serious help needed"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-01-03
Specs:
Pentium III 733mhz 256 Mb ram
Compaq Proliant ML 330 D03/F03 Rom Bios 06/02/2000
w/ a Compaq Smart Array 431 Controller  w/ three 9.1 GB HD's
ATI rage XL graphic card

When i try to install Ubuntu I get a boat load of error messages, ranging from:
partition table not recognized
ata.01: BMDMA stat 0x44
revalidation failed
SQUASHFS error: sb_bread failed reading block
SQUASHFS error: unable to load page block
basicly the same errors as this thread in[LaunchPad](https://bugs.launchpad.net/ubuntu/+bug/172937) is talking about.

and those are just the ones that I remember and had time to write down.

---

### Post by Paqman on 2008-01-04
I've never done it myself, but I believe you have to jump through a couple of extra hoops to install Ubuntu on a RAID array.

Some old info for Dapper [here](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto), not sure if it's relevant any more. It does involve downloading an extra package, though.

---

### Post by Lostincyberspace on 2008-01-04
The best way is to have a regular drive for the main installation and do the rest on a RAID since it will do almost all the drivers that way for it's self. But at start up there is an option to load the cd to memory and insert a cd with the RAID drivers on it that is how you need to install on a RAID array.

---

### Post by tad1073 on 2008-01-04
Should I format C:? Windows 2000 is running on that machine now and I cant figure out the partition tables for the hd's. the most I can do is set boot order for cd/r, hd, and set which Primary OS's I want to run such as Linux, others, NetWare 5.x, NetWare Small Business Suite 5, NetWare 4 SMP, non-SMP, NetWare 3, NetWare for Small Business 4, Windows 2000, Windows NT Server 4, Microsoft Back Office Small Business Server 4.5, SCO Open Srever 5, UnixWare 7. Only Windows 2000 is actually on the system though. I don't have an internet connection on that computer so I am a little disabled for now.

I having to read alittle go upstair mess with that comp. come back downstairs read some more go back upstairs etc. etc. etc.

---

### Post by tad1073 on 2008-01-04
Ok, I booted from the cd where it has start/install ubuntu, then I come to login screen but I have not given a user mane and password yet, is there a default user name and password to use I tried administrator/admin gut that didn't work.

---

### Post by perlluver on 2008-01-04
There is none from what I can remember.  Just hit enter and it should log you in.

---

### Post by tad1073 on 2008-01-04
> **perlluver said:**
> There is none from what I can remember.  Just hit enter and it should log you in.
tried that, nothing happened

---

### Post by perlluver on 2008-01-04
> **tad1073 said:**
> tried that, nothing happened

The only other thing I can think of is Ubuntu, no password.

---

### Post by tad1073 on 2008-01-04
I've tried ubuntu/ubuntu, ubuntu/gutsygibbon, but I have not tried ubuntu w/o a password

---

### Post by tad1073 on 2008-01-04
> **Paqman said:**
> I've never done it myself, but I believe you have to jump through a couple of extra hoops to install Ubuntu on a RAID array.

Some old info for Dapper [here](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto), not sure if it's relevant any more. It does involve downloading an extra package, though.

I have no internet connection on that computer and don't know how to network yet.

Well I am done for tonight. I will try some more tomorrow.

---

### Post by perlluver on 2008-01-04
> **tad1073 said:**
> I have no internet connection on that computer and don't know how to network yet.

I am pretty certain you will need an internet connection for it to install properly, otherwise it will hang up at about 80% installed.

---

### Post by tad1073 on 2008-01-04
thats what i figured, will a RJ-45 ethernet card work with a dsl modem or a d-link router?

---

### Post by perlluver on 2008-01-04
Yes I am using a DSL modem, and a Linksys Router.  Just pop it in the computer, and plug in a cable.

---

### Post by tad1073 on 2008-01-04
Alright, I am connected on the old box, to be a Pentium III 733mhz 256mb ram 16.9GB HD it is pretty fast. Now just need some help with the install. I can get as far as to log in but I have no user name or password set up.

[Refer to first page for more info](http://ubuntuforums.org/showthread.php?t=657796)

---

### Post by tad1073 on 2008-01-04
I am unable to install from the disk. I was able to put it on a Pentium II box with no problems but with the smart array controller I am having major probs. 

I don't know how to do this:

```
First choose which hard disks to use in the RAID array from the BIOS. 
Then from the BIOS RAID setup utility configure your RAID array.
```

---

### Post by tad1073 on 2008-01-05
Is there anyone out there that can walk me through this.

---

### Post by rkd on 2008-01-06
I can't walk you through this because I don't have any practical experience with RAID. I understand it theoretically, but that isn't a lot of help with the details of getting it working on a particular system.

The few posts I find on the Ubuntu forums that mention the Smart Array 431 Controller are from 2005 -- perhaps not useful since they are so old. (And they seem not to have found solutions to their problems then.)

I imagine the reason you haven't gotten much help here is that the Smart Array 431 is not very common, so not many people are trying to use it. Also, it probably would have been better to put the name of the controller in the title of your thread, to increase the chance that someone who knows about that controller will be able to spot it. I don't know whether the forum lets you change the title after you start the thread. If you can change it, consider doing that.

I can't tell from your posts much about what your goal is. Are you trying to install Ubuntu to dual boot this system with the Windows that is already installed? Do you want to wipe out the Windows that is installed and make it a pure Ubuntu system? Something else?

Handling RAID at boot time can be a little tricky, especially if it is software RAID or hybrid hardware/software RAID. That's because the data cannot be just read from a single disk -- GRUB has to have the complicated driver software to combine the data from all the disks to reconstruct the data stored in the RAID array.  I imagine pure hardware RAID is a bit easier -- in that case all the business about combining the data from the disks is handled by the controller, so I imagine the only difficulty is to be sure the boot code (GRUB) has a relatively simple driver for the hardware.

Linux might have the right driver available, but I don't know whether it is loaded automatically or you have to do something to tell it what driver it needs.

I did find one encouraging web site:

[http://www.cylindric.net/blog/2007/09/11/ubuntu-on-a-compaq-ml350-server](http://www.cylindric.net/blog/2007/09/11/ubuntu-on-a-compaq-ml350-server)

There, the guy reports a rather smooth installation of Ubuntu 7.04 Server onto a computer much like yours, with, I believe, exactly the same controller. He doesn't give much detail about the steps he did, but at least it does seem to provide an example that shows it *is* possible to get a recent Ubuntu installed on an array handled by that controller. He did this in September, 2007.

Perhaps you should download the 7.04 server iso and try to install it, on the chance that the server edition has built-in RAID support that the workstation version doesn't. I'm just guessing on that. There might not be any difference in the RAID support between the server and workstation versions of Ubuntu. But he *was* able to get 7.04 Server installed. If you don't want the Server install, you can always adjust it with the package manager later to delete the server stuff you don't want and add the workstation stuff you do want. Or maybe after getting Server installed, you could install Workstation over it. I don't know; I'm just speculating some more.

I notice he talks about pressing F8 during boot to do some sort of setup of the RAID system. Is the message you are asking about coming from the RAID controller's setup system? Did you get into it by pushing F8 during the boot? Or is that message coming from somewhere else?

It occurs to me that you might be able to skip the configuration of the controller if it is already configured the way you want. Or is it the case that you do want to change the configuration?

I wasn't able to find any detailed technical documentation about the controller you have -- just some spec sheets. It might be there somewhere, but HP (current owner of Compaq) isn't very good about keeping documentation of old products online, so I'm not very hopeful. Do you have any technical manuals for the controller that tell you how to configure it? Do you have a CD with any documentation or setup software on it?

---

### Post by tad1073 on 2008-01-06
That is a very detailed response you have there. I am trying to make this strickly an Ubntu machine but with all the problem i have encountered with ubuntu on another machine I will dual boot. 

My sys. goes like this:
Pentium III 733Mhz 256mb ram
Proliant ML330
Compaq Smart Array 431 Controller w/ 265kb cache
Parellel SCSI Array A 
Logical Drive 1 ( 16.9GB. Raid 5)
Three  9.1GB (Parellel SCSI) on port 1
Bus interface 64-bit PCI

If it is this message:
> First choose which hard disks to use in the RAID array from the BIOS. 
Then from the BIOS RAID setup utility configure your RAID array.
Then no, it is something i read about on a site that was suggested earlier in the thread.

This computer was a donation to my mom's Cat rescue/shelter and she gave it to me but there were no manuals or cd's that came with it. If I have left anything out feel free to ask me more questions about what is going on.

I have to disable smart array controller to boot ubuntu 7.10 CD. I get to the boot screen, I hit F4 and pick a screen resolution then I choose start or install ubuntu and hit enter. Ubuntu takes about 5 min. to boot up then I get to a login screen but I have not registered a user name and password for that particular machine yet. Am I missing something, is there a default login for first boot, no one so far has been able to help.

I can install from wubi off of the CD, then I get all these errors then busybox shell comes up and I have no clue what to do from there.

---

### Post by rkd on 2008-01-06
It still isn't very clear to me what is happening.

I found the statement about choosing which disks to use in that other post. That other post was written assuming you were starting with a newly-assembled system where the RAID controller had not yet been told which disks it should use and what type of RAID to do.  Your RAID controller is already set up to use the 3 disks you already have. Unless you want to change that, I'm pretty sure you have no choosing or configuring to do.

After reading the Ubuntu forums about using wubi, I'm not surprised that it doesn't work for you with that RAID controller. People are having lots of trouble trying to get it to work on pretty ordinary systems. I think it's a lost cause on your system because of the RAID controller, though I could be wrong about that.

When you talk about installing from wubi off the CD that really confuses me because the brief scan of the descriptions of wubi I just did says you don't use a CD when using wubi -- you download the .iso image of the CD, but wubi works from that directly from the hard disk, no CD involved. Can you explain a bit what you mean when you say "I can install from wubi off of the CD, then I get all these errors then busybox shell comes up"? I don't mean the details of the errors. I mean the precise set of actions you take from when you sit down in the chair in front of the computer. What commands did you type? What icons did you click? What responses to prompts did you give? That sort of thing. If it is many, many steps, don't tell me everything, but tell me enough of how you started so that if I walked up to the computer when you weren't around, I could get started the same way. I know nothing of wubi except what I read a few minutes ago, but what you say seems at odds with what I read, so I need to understand better what you did.

When you say you must disable the RAID controller to boot from the CD, that also puzzles me a little, though maybe not quite as much. Do you mean that if you put the CD into the CD drive, then restart the computer, it doesn't boot from the CD but instead boots from the RAID? If that is what happens, have you checked the computer's BIOS setup to see what the order of checking the boot devices is? In a system with ordinary disks, it ought to be floppy first, CD next, hard disk last. I'd be a little surprised if you couldn't get your computer set up so that it tries to boot from the RAID last, but RAID stuff is unusual, so maybe there are some restrictions.

The part about it asking for you to log on when you boot from the CD is really weird. When you boot an Ubuntu CD on a system with ordinary disk controllers, it doesn't ask you to logon. I have a hard time understanding how it could be doing that for you. I think you said you installed Ubuntu onto another computer, too. It didn't demand a logon then, did it? 

When you installed Ubuntu onto that other computer, after it was on the hard disk, you got a logon screen when you booted from the hard disk, right? Does the logon screen you are getting when you try to boot from the CD on the RAID computer look exactly like the logon screen you get when booting from the hard disk of that other computer, or is it different in some ways?

If the logon screen looks different, maybe it isn't coming from Ubuntu. Maybe the BIOS in the RAID controller or the motherboard has some sort of security mechanism that tries to protect the computer from tampering by OSes booted from the CD and is asking for an ID and password configured into the computer. Systems intended as servers have extra security mechanisms to protect against unauthorized tampering. Maybe you have hit something like that. Understand that, since I haven't seen it, I could be way off base. I'm just making guesses.

Okay, that's enough for now. Go back and read this again and each time you come to one of my questions, stop and write out the answer. Don't jump around -- answer one thing at a time. Try to be extra clear. Remember, I can see any of what you see. All I can know of what you are seeing is what you tell me.

---

### Post by tad1073 on 2008-01-06
> **rkd said:**
> It still isn't very clear to me what is happening.

I found the statement about choosing which disks to use in that other post. That other post was written assuming you were starting with a newly-assembled system where the RAID controller had not yet been told which disks it should use and what type of RAID to do.  Your RAID controller is already set up to use the 3 disks you already have. Unless you want to change that, I'm pretty sure you have no choosing or configuring to do.
Everything was already set-up when I received that computer.

> After reading the Ubuntu forums about using wubi, I'm not surprised that it doesn't work for you with that RAID controller. People are having lots of trouble trying to get it to work on pretty ordinary systems. I think it's a lost cause on your system because of the RAID controller, though I could be wrong about that.

When you talk about installing from wubi off the CD that really confuses me because the brief scan of the descriptions of wubi I just did says you don't use a CD when using wubi -- you download the .iso image of the CD, but wubi works from that directly from the hard disk, no CD involved. Can you explain a bit what you mean when you say "I can install from wubi off of the CD, then I get all these errors then busybox shell comes up"? I don't mean the details of the errors. I mean the precise set of actions you take from when you sit down in the chair in front of the computer. What commands did you type? What icons did you click? What responses to prompts did you give? That sort of thing. If it is many, many steps, don't tell me everything, but tell me enough of how you started so that if I walked up to the computer when you weren't around, I could get started the same way. I know nothing of wubi except what I read a few minutes ago, but what you say seems at odds with what I read, so I need to understand better what you did.
From windows 2000. I insert the cd into the cd drive>my computer>right click D:ubuntu.iso>explore>in that folder is the ubuntu icon which says wubi-cdboot

> When you say you must disable the RAID controller to boot from the CD, that also puzzles me a little, though maybe not quite as much. Do you mean that if you put the CD into the CD drive, then restart the computer, it doesn't boot from the CD but instead boots from the RAID? If that is what happens, have you checked the computer's BIOS setup to see what the order of checking the boot devices is? In a system with ordinary disks, it ought to be floppy first, CD next, hard disk last. I'd be a little surprised if you couldn't get your computer set up so that it tries to boot from the RAID last, but RAID stuff is unusual, so maybe there are some restrictions.
I unplugged the scsi cable from the array controller, I have boot cd then boot hd set up in dos. I removed the 3.5 floppy. So, when I uplug the scsi cable, my comp. boots from the cd 

> The part about it asking for you to log on when you boot from the CD is really weird. When you boot an Ubuntu CD on a system with ordinary disk controllers, it doesn't ask you to logon. I have a hard time understanding how it could be doing that for you. I think you said you installed Ubuntu onto another computer, too. It didn't demand a logon then, did it?
No, it didn't ask me for a login and password. The steps I took on that computer was as follows:
start in windows 2000>insert cd>open my computer>right-click D:>click wubi-cdboot. It installed fine on that other computer which is a pentium II 733mhz 256mb ram 16.5gb hd (removable) I have a wubi install on the computer that is in my sig which is my moms computer and that installed fine as well, I am affraid to migrate it to its own partition due to the fact that it is my moms computer.

> When you installed Ubuntu onto that other computer, after it was on the hard disk, you got a logon screen when you booted from the hard disk, right? Does the logon screen you are getting when you try to boot from the CD on the RAID computer look exactly like the logon screen you get when booting from the hard disk of that other computer, or is it different in some ways?
Yes both are the same. I have tried the user name and password I set up on the other machine along with many others such as administrator/admin, ubuntu/nopass, ubuntu/ubuntu, etc. etc.

> If the logon screen looks different, maybe it isn't coming from Ubuntu. Maybe the BIOS in the RAID controller or the motherboard has some sort of security mechanism that tries to protect the computer from tampering by OSes booted from the CD and is asking for an ID and password configured into the computer. Systems intended as servers have extra security mechanisms to protect against unauthorized tampering. Maybe you have hit something like that. Understand that, since I haven't seen it, I could be way off base. I'm just making guesses.
the screens are the same. it is not a bios mechanism or any other.

> Okay, that's enough for now. Go back and read this again and each time you come to one of my questions, stop and write out the answer. Don't jump around -- answer one thing at a time. Try to be extra clear. Remember, I can see any of what you see. All I can know of what you are seeing is what you tell me.

---

### Post by rkd on 2008-01-08
Sorry I don't have anything new for you today. I've been working on some other things as well as your problem and just haven't made much progress on yours today. I'll have more for you soon, though. Keep watching.

---

### Post by tad1073 on 2008-01-08
I managed to reconfigure the array to a RAID0 w/ 25.9gb and 128mb striping,  but I lost windows 2000 in the process, so now I am stuck with a computer that is basicly useless to me. The other computer is a Gateway Pentium II 733mhz w/256mb ram and 16gb hd but it has no ethernet card in it, hell I don't even know if they make an ethernet card for a computer that old.

---

### Post by rkd on 2008-01-09
I'm sorry to hear that you lost the Windows installation. I wish you had asked about it before making the change. I could have warned you that you'll lose the data if you change the RAID configuration. If you haven't written anything to the disks since you changed it, there is a small chance that if you put the RAID configuration back the way it was, the Windows files will still be intact. It depends on whether the RAID controller itself did any writes to the disks.  So if you would really, really like to have the Windows back, it probably is worth trying.

If you don't care so much about keeping Windows, or putting the RAID configuration back doesn't bring Windows back, then you could just go straight to installing Ubuntu onto the computer. If there is nothing left to lose, you can experiment freely. I still haven't figured out why it was prompting you for a username and password when booting from the CD on that computer, but I'd be VERY surprised if it still does that, now that the data on the disks has been scrambled.

I haven't had as much time as I hoped to investigate what happens when you run the wubi install from the CD, as you described. I have to swap a spare hard drive into my test system before experimenting with something that might destroy files, and I've just been too busy to do it, yet. I'll get to it soon, I hope.

Ethernet was around ages before Pentium II computers were introduced, so ethernet cards were easily available for them. If there is a used electronics store somewhere near you, you should be able to find a suitable used ethernet card for under $5. You can get brand new ethernet cards of good quality for under $10. (If your computer doesn't take PCI cards, then a new card won't help you.) I can't remember whether the Pentium II systems were still using only ISA slots or had already gone to the mixed ISA and PCI arrangement. Check what kind of slots you have free so you know which kind of card you can use. And look in the Linux Hardware Compatibility List site to find out what ethernet controllers Linux can run, so you don't get a card with some odd-ball controller that Linux doesn't recognize.

---

### Post by tad1073 on 2008-01-09
I have tried to install Ubuntu after I reset the raid so M$ W2k is probably a lost cause though I will try. The other computer has a R-45 jack in it but I think it is strickly a network adapter intranet and not an ehternet card.

---

### Post by rkd on 2008-01-09
If Ubuntu wrote anything to the disk, your chance of finding Windows intact is small, but if you want to give it a shot, you certainly can't hurt anything.

What happened when you tried to install Ubuntu after reconfiguring the RAID? Did it still ask you to logon when booting from the CD, or did you get further? If you got further, it still would not have written anything on the disk until after you clicked the Install icon on the Ubuntu desktop. Did you get that far?

The RJ-45 connector on the Gateway system could be an ethernet connection, but you are right that there is some chance that it is a different kind of network. I don't remember whether IBM's token ring network used RJ-45 jacks or something else. I think it would be a bad idea to try to connect it to any other equipment until you learned it really is an ethernet jack. The electrical characteristics of a different kind of networking might be enough different to cause damage to ethernet equipment if you plugged them together.

The computer probably has a Gateway product name and/or model number on it. Take that information and go to the Gateway web site support section, and you probably can find the specs or .pdf copies of the manuals for the system and learn pretty quickly what kind of network it supports. If you are at all unsure of what you find, tell me the product name and model and I'll check it out, too.

---

### Post by tad1073 on 2008-01-09
the "other" computer in mention is a Gateway Pentium II MMX technology. That one was donated to my mom's non-profit also. It has a working copy of Ubuntu but i am not sure if the RJ-45 is ethernet or intranet. Ubuntu didn't recognize an ethernet card but did recognize a dial-up modem.

As far as the RAID computer goes I can't get to the login screen any more, Ubuntu wil start it check the ask me to hit enter for maintenance or ctrl+d to continue. If I continue it outputs a bunch of error messeges and nothing more, if I hit enter I am taken to root@ubuntu but I have no clus as what to do from there since I am not computer savy.

[More info here](https://answers.launchpad.net/ubuntu/+question/21801)

---

### Post by tad1073 on 2008-01-10
Spec:
Compaq Proliant ML330
Pentium III 733mhz 256k cache
256mb ram
Compaq Smart Array 431 Controller set to RAID0 w/25.9gb=3/9.1gb hd's
System Embedded IDE Controller
SCSI Controller

Old problem solved, bad cd-rom drive, now I am faced with a new problem. I get all the way to where Ubuntu scans the disk for the partition set-up then hangs at 46%. HELP!!!!
So close, but yet, so far.

---

### Post by rkd on 2008-01-10
Hmmm. I think it is really odd that a bad CD drive would lead to that hit enter or ctrl-D prompt.  Are you sure that the CD drive is the only change you made to make it start booting properly?

And that still leaves unanswered what made Ubuntu prompt for a login when you were booting from the live CD.

Well, anyway, it's booting now. And it sounds like you clicked the Install icon to get it to install to the hard drive. Is that right?

So you went through the language choice, the time zone choice, the keyboard choice, and it is hanging at 46% starting up the partitioner. Is that right?

If my guesses about what you did and where you got stuck are right, I can make a guess about why it is stuck. It said it is starting up the partitioner. That will look at the disk and show you what is there, then let you decide where to put Ubuntu on the disk, and, more important, whether you want to share the disk with an operating system that is already installed. 

Your disk probably is looking very strange since you reconfigured the RAID, but (I guess) haven't created a partition table on the reconfigured RAID. The partitioner probably got nonsensical values when it read from where the partition table should be and doesn't protect itself from that situation.

If that is what happened, it probably is easy to fix. But first you have to decide whether you are going to try to put the RAID configuration back to the way it was and try to recover the Windows installation that was there. If you want to do that, you should do it before trying to install Ubuntu. If you don't want to try to recover the Windows installation, or you tried and it didn't work, then I think you can clear up your current problem by writing something sensible to the partition table before trying to install Ubuntu.

One way to attempt to do that is to use the fdisk program. It might not work because it is going to look at the partition table at the start, too, but it might defend itself against a garbaged partition table better than the partitioner used by install.  If fdisk doesn't work, then I think we could use the dd command to write zeros over the first few sectors of the disk, then try to use fdisk. The installer certainly should be able to tolerate an all-zeros partition table.

To use fdisk, you first open a Terminal. Do that by going to the Applications menu in the upper left of the screen. Under Applications, choose Accessories, then Terminal. In the Terminal type the command:
```
sudo fdisk -l
```
That should list all the disks it can see and the partitions it sees on each disk. We need this to find out what device name the RAID array has. An ordinary hard drive is usually /dev/hda, but the RAID probably will be something different. The name should be on the first line of output, right after the word "Disk". Suppose it is /dev/x just for this example. Then enter the command:
```
sudo fdisk /dev/x
```
That should display a little information about the disk, then prompt for a command. You should choose the o command, and after that, the w command. That should write an empty partition table to the disk. Then you can try installing Ubuntu again.

If fdisk displays information about more than one disk, you'll have to try to figure out which is the RAID array. I don't believe it will see more than one disk (the only disks in the system are the RAID array, right?). If fdisk does show more than one disk and you can't figure out which is the right one, copy down what fdisk displays and type it into a post and I'll help you figure it out.

If fdisk gets stuck like the partitioner did, tell me and we'll figure out another way to learn the device name of the RAID.

I don't know how much you've read about how to do the installation. There is a decent guide to installing here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

And you'll find a lot of other useful topics on the links down the left side of that page. Of course, there's lots of stuff at the ubuntu site, too.

About the Gateway computer, I'm not certain, but I think the phrase "Gateway Pentium II MMX technology" is not the model name, but more of a slogan they used on lots of their models at the time. I think Gateway used model names that looked something like G6-266M. It might not be very prominent -- it might be in small printing on the front somewhere, or on a label on the back, side, or even bottom of the case. It also might display on the screen at boot time -- put a floppy disk without an operating system on it into the floppy drive before turning on the computer. That might keep the information from scrolling off the screen. Another place it might display is on the BIOS setup screens. You can usually see directions for which key to push during boot to get into the setup screens. It often is Del or F2, but it can be others. Also, when I was at the Gateway support web page, I was reminded that they let you find information about your computer by entering the serial number. That probably is on a label on the back of the computer. Send me whatever you can find for the model name plus the serial number and I'll see what I can dig up about the network controller.

---

### Post by tad1073 on 2008-01-10
> Hmmm. I think it is really odd that a bad CD drive would lead to that hit enter or ctrl-D prompt. Are you sure that the CD drive is the only change you made to make it start booting properly?
Other than taking the nework card/video card and the scsi controller out , yes the cd-rom is the only hardware I swaped out.
> And that still leaves unanswered what made Ubuntu prompt for a login when you were booting from the live CD.

Well, anyway, it's booting now. And it sounds like you clicked the Install icon to get it to install to the hard drive. Is that right?

So you went through the language choice, the time zone choice, the keyboard choice, and it is hanging at 46% starting up the partitioner. Is that right?
yes and yes
> that is what happened, it probably is easy to fix. But first you have to decide whether you are going to try to put the RAID configuration back to the way it was and try to recover the Windows installation that was there. If you want to do that, you should do it before trying to install Ubuntu. If you don't want to try to recover the Windows installation, or you tried and it didn't work, then I think you can clear up your current problem by writing something sensible to the partition table before trying to install Ubuntu.
I tried to recover w2k but to no avail. How do I go about How do i go about configuring the partiotion table?
> One way to attempt to do that is to use the fdisk program. It might not work because it is going to look at the partition table at the start, too, but it might defend itself against a garbaged partition table better than the partitioner used by install. If fdisk doesn't work, then I think we could use the dd command to write zeros over the first few sectors of the disk, then try to use fdisk. The installer certainly should be able to tolerate an all-zeros partition table.
yeah, I already tried sudo fdisk -l and it didn't work, i guess there is nothing there yet.
> If fdisk gets stuck like the partitioner did, tell me and we'll figure out another way to learn the device name of the RAID.
Will this help:
ID0=BB00921B91
ID1=BB009222B5
ID2=BB009222B5
and I set APIC Table to Full Table Mapped
> About the Gateway computer, I'm not certain, but I think the phrase "Gateway Pentium II MMX technology" is not the model name, but more of a slogan they used on lots of their models at the time. I think Gateway used model names that looked something like G6-266M. It might not be very prominent -- it might be in small printing on the front somewhere, or on a label on the back, side, or even bottom of the case. It also might display on the screen at boot time -- put a floppy disk without an operating system on it into the floppy drive before turning on the computer. That might keep the information from scrolling off the screen. Another place it might display is on the BIOS setup screens. You can usually see directions for which key to push during boot to get into the setup screens. It often is Del or F2, but it can be others. Also, when I was at the Gateway support web page, I was reminded that they let you find information about your computer by entering the serial number. That probably is on a label on the back of the computer. Send me whatever you can find for the model name plus the serial number and I'll see what I can dig up about the network controller.
There is no serial number on the gateway machine, no model number either. all I know is that it is a pentium II w/ asus motherboard

---

### Post by rkd on 2008-01-11
For the Gateway computer, you mention it is an ASUS motherboard. If you can spot the motherboard's model number, we could look up the specs on it. If the LAN controller is built into the motherboard, that would tell us what type of LAN it is. ASUS motherboard model numbers of that era generally looked like P2L97 LX, P2B-DS, and similar. It sometimes is hard to spot the motherboard model number when the motherboard is in the computer with all the stuff plugged into it, so don't feel bad if you don't see it.

It was not common for the LAN controller to be built into the motherboard at that time, so it might be on a separate adapter card. If so, don't bother trying to find the model name of the motherboard -- look for a manufacturer name and model number on the LAN adapter card, and we could look that up.

But before looking inside the computer, a simpler thing you could try is run the lspci command in a Terminal window and see whether it identifies an ethernet controller. If you try that and don't see an ethernet controller, post the output here. You can copy the output of the lspci command from the terminal window, paste into an editor window, save the file onto a floppy disk, and carry the floppy to the computer you use to post from.

----------------------

For the Proliant, I don't know anything about configuring the RAID controller. I might be able to figure it out in a reasonable amount of time if I were sitting in front of the computer, but trying to do it by remote control isn't very likely to work. I looked at the HP site for documentation for configuring the controller, and I found this: 

[http://h20000.www2.hp.com/bc/docs/support/SupportManual/c00729544/c00729544.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/c00729544/c00729544.pdf)

But it only shows the main menu for the configuration (pages 8 to 10). I haven't been able to find any more detailed information about configuring it.

You could try reproducing the screen or screens you see when interacting with the configuration utility and I might be able to give you some advice, but as I said before, trying to figure it out remotely would be very slow.  

Did you happen to write down or remember what the settings were before you changed anything? That might provide some help deciding what you should choose now.

I suppose the ID0, ID1, and ID2 values you showed simply identify the three disks you have. What other choices are there for the APIC setting?

I found this:

[http://www.mjmwired.net/kernel/Documentation/cpqarray.txt](http://www.mjmwired.net/kernel/Documentation/cpqarray.txt)

which looks like some comments in the Linux kernel about support of the SmartArray 431 (and many other) controller. It seems to say that the device name should be /dev/ida/c0d0. You could check that by doing an ls command for that filename.

If you don't find that exact name, try this command:
```
sudo find /dev -type b
```
and look for names similar to the /dev/ida/c0d0.

Once you find the device name, you could try this (with the device name you found):
```
sudo fdisk /dev/ida/c0d0
```
and see whether it will let you list and/or create a partition on the device.

If that fdisk attempt doesn't work, another thing to try is zeroing the first few sectors of the disk and trying the fdisk again. I think this will do it:
```
sudo dd bs=512 count=10 if=/dev/null of=/dev/ida/c0d0
```

If you do get the disk partitioned with fdisk, you probably will be able to go on to install Ubuntu onto it. If we decide later that some of those RAID configuration parameters should be different than what you set them to, we might have to install again. Just keep that in mind.

---

### Post by tad1073 on 2008-01-11
From gparted i did this:
Disk Label Type=msdos
/dev/sdb1 ext3 7.47GiB
/dev/sdb2 extended 1GiB
/dev/sdb5 linux-swap 1Gib
 
As far a s the array goes:
Disk Label Type=unrecognized
dev/ida/c0d0 unallocated unallocated 16.94GiB

[Take a look at this](http://ubuntuforums.org/showthread.php?t=664316)

i got ubuntu istalled once but it wouldn't boot so I changed the device order and it still wouldn't work.

---

### Post by rkd on 2008-01-11
You need to learn a little patience. You aren't going to learn to install and run Ubuntu overnight. 

You've said several times that you don't know what you are doing, but then you don't seem to follow the instructions I give, but instead flail around trying this and that, starting new threads, and I don't know what else (because you don't do a good job of explaining what you have done between posts).

Slow down. Take things one step at a time. Realize that, since we aren't sitting there beside you, it is going to take time for several exchanges of posts between when you ask about a problem and we work out the answer.

And tell us everything. Today is, as far as I remember, the first time you gave any hint that there was another disk in the computer besides the three that are in the RAID. At least what you are showing from gparted seems to indicate that there is another disk there. And gparted seems to think the RAID is 18GB, not 27GB.

So did you reconfigure the RAID back to its original settings? I imagine the original configuration was RAID5 (two data disks and one parity disk). You had changed it to RAID0 (all three data disks) for about 27GB of storage. I thought that was what lost your Windows installation.

How about that other disk? It looks like a 9GB disk, and it looks like you installed Ubuntu onto it. Was that disk in the computer from the beginning or did you add it after you lost the Windows install when you reconfigured the RAID? Was the Windows install on the RAID? Or was it on that 9GB disk? If the Windows install was on the 9GB disk, how did reconfiguring the RAID mess up the Windows install? I don't even know what questions to ask because I don't know what you've done.

How about giving me a list of what hardware is in that computer, and a recap of everything you remember about what you have done to that computer?  And what goal are we working toward?

I'm sure we can get that computer working with Ubuntu, but you need to slow down and work methodically. Otherwise, you are wasting a lot of time and energy -- both yours and mine.

---

### Post by tad1073 on 2008-01-11
> You've said several times that you don't know what you are doing, but then you don't seem to follow the instructions I give, but instead flail around trying this and that, starting new threads, and I don't know what else (because you don't do a good job of explaining what you have done between posts).
I have been trying to install ubuntu on that machine since before Christmas, so I hope you understand my impatience and wanting to get this done. I am unemployed so i can't afford to by a new computer and I have all the time in the world to work to try and get Ubuntu installed 

> So did you reconfigure the RAID back to its original settings? I imagine the original configuration was RAID5 (two data disks and one parity disk). You had changed it to RAID0 (all three data disks) for about 27GB of storage. I thought that was what lost your Windows installation. How about giving me a list of what hardware is in that computer, and a recap of everything you remember about what you have done to that computer? And what goal are we working toward?
Hard Drive Controller Order
Slot 2 Compaq Smart Array 431 Controller
System Embedded IDE Controler
Slot 3 Compaq Wide/Ultra2 SCSI Controller
Boot Order
CD-Romm
Floppy Drive (A:)
Hard Drive (C:)
Logical Drive1, RAID 0, 25.4GB
[I tried this](http://ubuntuforums.org/showthread.php?t=630644&highlight=FakeRaid)
```
 but when I get to sudo dmraid -r it ouputs a bunch 
of error messages then the cd-rom starts acting crazy,
 it won't stop spinning, what it is reading is beyond me
```


there are only 3 hard drives in that computer, each being 9.1GB

---

### Post by rkd on 2008-01-11
You are at it again -- flailing around I mean.

A while ago, when I looked at post #33, I'm sure it said something about you seeing some report from the computer of devices and sizes something like:

   /dev/ida/c0d0  8.47 GB
   /dev/ida/c0d1  8.47 GB
   /dev/ida/c0d2  8.47 GB
   /dev/sdb 8.47 GB

and nothing about dmraid.

I was trying to imagine how that could be, given what else you have told me about the computer. Now I look at it again, and the story has changed. I can't give you advice that has much chance of working if you change things between the time you tell me what the condition of the computer is and the time I can get instructions for the next step back to you.

At this point, I can't be sure of anything. I think trying to fix problems through these support forums doesn't match your personal style and that you need to find someone in your local area who is willing to work directly with you. If you don't know anyone personally who will come and help you that way, you might be able to find someone like that through your local Linux User's Group, if there is one in your area.  You can check for Linux User's Groups on this page:

[http://www.linux.org/groups/](http://www.linux.org/groups/)

There may be Linux User's Groups that are not included in that list, so if you don't find one listed that is close to you, there still might be one near you, or a more general computer users group with some people interested in Linux. You could inquire about such local groups at your public library or if there is a used/surplus electronics store in your area, people there might know of such a group.

Good luck.

---

### Post by tad1073 on 2008-01-12
I don't have anythiing else to do. I have to exaust all possiblities to try and find something that works.  am sorry if I am impatient but you have to understand that I have been trying to get ubuntu on that machine for 3 weeks now. i read through all the documentation and try what they suggest but I run into problems and can't do anything after that.

---

