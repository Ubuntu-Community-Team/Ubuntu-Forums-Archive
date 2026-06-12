---
title: "need help returning to windows"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-08-16
I have tried, and failed to get on with linux.  I just can't do it.  

I have never had windows installed on my computer, and so I have had to go out and buy a complete windows operating system.  

Questions

Will I lose all my pictures, music, files etc when I install windows, or is there someway I can keep them?

Will linux totally disappear from my computer when I install windows?

Please help!

---

### Post by Frak on 2007-08-16
Unless you partition your hard drive ([GParted]("http://gparted.sourceforge.net/")), you will lose everything.
You can either store your files on a seperate disk, storage media, etc. Or hold them within their own partition.
Windows is a very greedy OS and will only take what it sees. It has a built in partitioner that only works one way, everything on a disk unless another partition is created.

---

### Post by Hobo Joe on 2007-08-16
Yes, unless you keep them in a separate partition.
Linux will dissapear unless you have it installed on a separte partition from the one you're installing windows on.

---

### Post by maitresse on 2007-08-16
Thanks.

The other problem is, that my disc drive is just not recognising blank discs, so I cannot put any of my data on disc.  Any ideas?

---

### Post by Tomosaur on 2007-08-16
The Windows installer is incredibly unfriendly - so yes, you will lose everything on your hard drive, including Ubuntu.

If you want to keep your various files, you will need to back them up to a CD or USB disk or something like that.

The Windows installer will try to take over your entire hard drive by default - there are ways and means around it, but since you want to be rid of Ubuntu completely then you may as well just let it do its thing - just remember to backup the stuff you want to keep to some kind of portable storage like a CD or even a DVD.

Were there any particular problems you've been having with Ubuntu? I'm sure people here will be able to help, but it's your choice :)

Good luck with whatever you choose to do.

---

### Post by Frak on 2007-08-16
What brand is it? And can it play CD's now.

---

### Post by stchman on 2007-08-16
> **maitresse said:**
> I have tried, and failed to get on with linux.  I just can't do it.  

I have never had windows installed on my computer, and so I have had to go out and buy a complete windows operating system.  

Questions

Will I lose all my pictures, music, files etc when I install windows, or is there someway I can keep them?

Will linux totally disappear from my computer when I install windows?

Please help!

What were the big failings?  The forum can help.  Since you have never had Windows how do you know that it will do the job better for you?

---

### Post by Trebaruna on 2007-08-16
The windows installer isnt that unfriendly at all.

In my opinion, the easiest option - if burning media or using external drives is not feasible - is to shrink Linux (use your Ubuntu LiveCD for this, and fire up Gparted) and create a FAT32 partition in the free space. 

Boot LiveCD, shrink your Linux partition, create new FAT32 partition.
Boot Ubuntu, copy/move your files onto the new partition.
Boot the windows installer. Remember which partition was which: select that one to install Windows to, be sure you do not select your data partition (for obvious reasons).
Once windows is done you should have a D: drive in My Computer with all your stuff nicely there.

Perhaps it's a good idea to keep that partition, to protect your data from exactly this kind of thing (or windows deaths, etc)

EDIT: perhaps trying to convince maitresse to keep Linux isnt the best option here. This user has given up his quest. It is commendable he/she tried in the first place! Linux, we should all know, isn't necessarily for everyone, not yet. Helpful advice, methinks, is more appropriate here.

---

### Post by maitresse on 2007-08-16
> **Frak said:**
> What brand is it? And can it play CD's now.

It plays cd's. and when i put in a blank cd, it tells me I have done so, and then asks what i want to do with it.  Then, when cd/dvd creator has opened, i put all the files in that i need............but then it always  fails to burn for me

---

### Post by Frak on 2007-08-16
> **Trebaruna said:**
> The windows installer isnt that unfriendly at all.

In my opinion, the easiest option - if burning media or using external drives is not feasible - is to shrink Linux (use your Ubuntu LiveCD for this, and fire up Gparted) and create a FAT32 partition in the free space. 

Boot LiveCD, shrink your Linux partition, create new FAT32 partition.
Boot Ubuntu, copy/move your files onto the new partition.
Boot the windows installer. Remember which partition was which: select that one to install Windows to, be sure you do not select your data partition (for obvious reasons).
Once windows is done you should have a D: drive in My Computer with all your stuff nicely there.

Perhaps it's a good idea to keep that partition, to protect your data from exactly this kind of thing (or windows deaths, etc)

EDIT: perhaps trying to convince maitresse to keep Linux isnt the best option here. This user has given up his quest. It is commendable he/she tried in the first place! Linux, we should all know, isn't necessarily for everyone, not yet. Helpful advice, methinks, is more appropriate here.
Which is why some of us create a seperate home partition ;)

---

### Post by maitresse on 2007-08-16
> **Trebaruna said:**
> The windows installer isnt that unfriendly at all.

In my opinion, the easiest option - if burning media or using external drives is not feasible - is to shrink Linux (use your Ubuntu LiveCD for this, and fire up Gparted) and create a FAT32 partition in the free space. 

Boot LiveCD, shrink your Linux partition, create new FAT32 partition.
Boot Ubuntu, copy/move your files onto the new partition.
Boot the windows installer. Remember which partition was which: select that one to install Windows to, be sure you do not select your data partition (for obvious reasons).
Once windows is done you should have a D: drive in My Computer with all your stuff nicely there.

Perhaps it's a good idea to keep that partition, to protect your data from exactly this kind of thing (or windows deaths, etc)

EDIT: perhaps trying to convince maitresse to keep Linux isnt the best option here. This user has given up his quest. It is commendable he/she tried in the first place! Linux, we should all know, isn't necessarily for everyone, not yet. Helpful advice, methinks, is more appropriate here.

This sounds wonderful...........but i dont have the liveCD!

---

### Post by Frak on 2007-08-16
> **maitresse said:**
> It plays cd's. and when i put in a blank cd, it tells me I have done so, and then asks what i want to do with it.  Then, when cd/dvd creator has opened, i put all the files in that i need............but then it always  fails to burn for me
Try this
```
sudo aptitude install k3b
```
This will install a program called k3b, it should work much better than the built in one.
Its located in Applications->Sound & Video->K3b

---

### Post by Arthur Archnix on 2007-08-16
1. Get cd/dvd burner working.
2. Use a usb key.
3. Zip and upload your files to an online storage. Assume this isn't secure.
4. Forget the files, start fresh. Download pictures of other families and claim them as your own. 

Note: discuss #4 with current family before proceeding.

---

### Post by Brightbelt on 2007-08-16
With blank CD-R problems, it can sometimes be worth the trouble to try a different brand. For instance, if you've been using Memorex blank CD-Rs, try using a Sony blank CD-R instead, or anything really as long as it is a different brand.

Of course, it may not make any difference, but it might be worth a try.

Good Luck,
Frank B.

---

### Post by maitresse on 2007-08-16
> **Frak said:**
> Try this
```
sudo aptitude install k3b
```
This will install a program called k3b, it should work much better than the built in one.
Its located in Applications->Sound & Video->K3b

Tried this, but i just crashes on me.

Any other ideas?

---

### Post by stchman on 2007-08-16
> **maitresse said:**
> Tried this, but i just crashes on me.

Any other ideas?

Try this:

```
sudo apt-get install k3b libk3b2-mp3
```

---

### Post by heimo on 2007-08-16
> **maitresse said:**
> Tried this, but i just crashes on me.

Any other ideas?

I checked titles of your posts on Ubuntuforums and probably half of them are about "burning CDs", something is telling me that you should try saving your stuff to alternative media or use one of tips Arthur suggested. Good luck.

---

### Post by maitresse on 2007-08-16
> **stchman said:**
> Try this:

```
sudo apt-get install k3b libk3b2-mp3
```

still crashes.  this is driving me mad!

---

### Post by stchman on 2007-08-16
> **maitresse said:**
> still crashes.  this is driving me mad!

Define crash???  Does the PC lock up?  What happens?  Give us some terminal output from what I said to type.

---

### Post by Terl on 2007-08-16
> **maitresse said:**
> still crashes.  this is driving me mad!

Are there any error messages?

---

### Post by Frak on 2007-08-16
> **maitresse said:**
> still crashes.  this is driving me mad!
Are you using K3b or are you still using the default?

---

### Post by WebSiteGuru on 2007-08-16
> **Frak said:**
> Are you using K3b or are you still using the default?

maitresse is still having probem installing it(I think). To my understanding.

---

### Post by maitresse on 2007-08-16
Right.

I managed to get all the things i want to save onto disc.

I put the windows xp disc in...........................and don't know what to do next!!!

HELP!!!!

setup.exe keep opening in wine, but then crashes!

---

### Post by Arthur Archnix on 2007-08-16
> **maitresse said:**
> setup.exe keep opening in wine, but then crashes!

Hmm... I think you may be having a compatibility problem with WINE. It's possible to recompile your Kernel, but first let's just  try putting your windows disc in and rebooting the computer.

---

### Post by maitresse on 2007-08-16
> **Arthur Archnix said:**
> Hmm... I think you may be having a compatibility problem with WINE. It's possible to recompile your Kernel, but first let's just  try putting your windows disc in and rebooting the computer.

Tried rebooting with the disc in.........nothing.

---

### Post by heimo on 2007-08-16
> **maitresse said:**
> Right.

I managed to get all the things i want to save onto disc.

I put the windows xp disc in...........................and don't know what to do next!!!

HELP!!!!

setup.exe keep opening in wine, but then crashes!

Don't run it in wine. Boot from it like you'd start installing Ubuntu. 
[http://support.microsoft.com/kb/314458/en-us](http://support.microsoft.com/kb/314458/en-us)

---

### Post by Arthur Archnix on 2007-08-16
Ok, we need to make sure your BIOS is set to boot first from your CD/DVD. Sometimes when you're computer starts it tells you to press a key (maybe F10) to get into BIOS, do that and then under boot-up options make sure that the CD/DVD is before the hard-drive.

---

### Post by heimo on 2007-08-16
> **maitresse said:**
> Tried rebooting with the disc in.........nothing.

Helpful links:
[http://www.microsoft.com/windowsxp/using/setup/winxp/install.mspx](http://www.microsoft.com/windowsxp/using/setup/winxp/install.mspx)
[http://support.microsoft.com/?scid=gp;](http://support.microsoft.com/?scid=gp;)[ln];csshome&style=home

---

