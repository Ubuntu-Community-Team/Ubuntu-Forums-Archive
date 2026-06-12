---
title: "what to do about firmware updates since I wiped out OS X"
date: 2009-02-19
forum: Apple Hardware Users
---

### Post by darksidedude on 2009-02-19
well I wanted to get rid of OS X ( 80gb just isn't enough for 2 OS's) I made a TM backup ( =P ) but I forgot about the Firmware and EFI updates apple will inevitably release. I don't really want to reinstall OS X now that ubuntu is working fine all by it self. so my question is 
1. I know the TM drive can be made bootable ( external USB drive) 
2. can that be done within ubuntu without hosing the backup
3. my macbook OS X install disk 2 is trashed so if I lose that backup I would have to buy OS X disks ( cant really afford that) 

so Can I make my backup bootable within ubuntu so I would have a functional OS X not stealing space from my internal harddrive 

note : I don't have any other macs

the support on these forums are great I love you guys!!!

---

### Post by darksidedude on 2009-02-19
oh great. just found out that the macbook will only boot up to the hard drive if the ubuntu cd isn't in there otherwise i get the blinking folder and question mark. :( so I have to leave the CD in there forever????

---

### Post by flaggh on 2009-02-19
Did you bless the partition?

---

### Post by darksidedude on 2009-02-19
thanks for the answer, however I don't know how to force an EFI prompt. there is no EFI partition anymore (converted from GPT to MBR) since it was the only OS on the disk. so I guess it "blessed" the CD drive but not the root partition on the hard disk

---

### Post by flaggh on 2009-02-19
Instructions on how to bless a drive are here:

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

This should make your linux partition bootable.

---

### Post by darksidedude on 2009-02-19
well since I don't have the GPT i can skip the refit step right? since the hard drive is no longer GPT but rather MBR? because when I unzip the .gz REFIT "ISO" i get a .cdr using 7zip

---

### Post by darksidedude on 2009-02-19
as a side note I fixed my OS X disk 2 with some brasso.

so + 1 to using brasso to refinish a DVD CD

---

### Post by cyberdork33 on 2009-02-19
> **darksidedude said:**
> 1. I know the TM drive can be made bootable ( external USB drive)
It can?
> **darksidedude said:**
> 2. can that be done within ubuntu without hosing the backupYou'll have to post some information about what you are talking about doing and we might be able to offer some better advice for that.
> **darksidedude said:**
> 3. my macbook OS X install disk 2 is trashed so if I lose that backup I would have to buy OS X disks ( cant really afford that) 
I think you only need the first disk to install a basic OSX system, and I think that Apple will replace your discs.

If you want to perform a firmware update, you have to have an OSX system to boot into. Luckily, you can install OSX to an external drive if you want, and you do not have to take space on your internal drive.

> **darksidedude said:**
> oh great. just found out that the macbook will only boot up to the hard drive if the ubuntu cd isn't in there otherwise i get the blinking folder and question mark. :( so I have to leave the CD in there forever????

> **darksidedude said:**
> well since I don't have the GPT i can skip the refit step right? since the hard drive is no longer GPT but rather MBR? because when I unzip the .gz REFIT "ISO" i get a .cdr using 7zipyou should create a rEFIt cd for future use. It can get you out of a bind. You do not HAVE to create a rEFIt CD, you can also boot into Ubuntu and install the "refit" package. Then you can use the gptsync command to sync the partition tables. You will have to use an OSX system to bless the Linux partition (fortunately, just booting from an install disc is enough).

---

### Post by darksidedude on 2009-02-19
ok to start, here is the info to make the TM back ups bootable [http://www.macosxhints.com/article.php?story=2008011623365026]("http://www.macosxhints.com/article.php?story=2008011623365026")

in short, you restore to your hard drive the OS X install Disk # 1

since I fixed my OS X disk 2 and installed again.  If I knew how to mark the thread solved. I have fixed the computer. but I still have OS X. ( striped out the stuff I didn't need. ) i guess it would be better to just keep OS X rather then try and single boot ubuntu?

---

### Post by cyberdork33 on 2009-02-19
> **darksidedude said:**
> ok to start, here is the info to make the TM back ups bootable [http://www.macosxhints.com/article.php?story=2008011623365026](http://www.macosxhints.com/article.php?story=2008011623365026)

in short, you restore to your hard drive the OS X install Disk # 1
ok well that would erase the data you have on there already, and i don't think there would be an easy way to do that in Linux, except maybe with dd, but then you still lose everything on there.

> **darksidedude said:**
> since I fixed my OS X disk 2 and installed again.  If I knew how to mark the thread solved. I have fixed the computer. but I still have OS X. ( striped out the stuff I didn't need. ) i guess it would be better to just keep OS X rather then try and single boot ubuntu?why don't you just use the time machine drive to install OSX on. Then you can boot from it any time you want to check for firmware updates.

---

### Post by darksidedude on 2009-02-20
you can do that? 

but what should I do for the EFI not booting grub. 

im sorry but I am very confused!

---

### Post by ajmctaggart on 2009-02-20
A Time Machine Backup can only be made bootable IF you choose the option when booting from Leopard Disk and select "restore from Time Machine." It takes awhile, but does work...that would effectively give you back your old Leopard system, so you'll have to erase Ubuntu or get some other type of USB/Firewire drive to hold the new installation.

I believe I have a better idea...

Here's the deal...
How much room is on the TM drive?  Partition that thing with a 15 Gig partition if possible for Leopard (That should hold it right?).

From that point, all your TM stuff is completely browse-able ONCE you're in Leopard (And maybe w/ Ibex' support for HFS, I haven't tried that...)

So, You need a small partition for a copy of Leopard, with nothing fancy installed, and go ahead and do all updates till your heart's content.  

You'll have access to all your TM stuff, just by browsing through the files, and you'll be able to get firmware/hardware fixes Apple releases going forward, etc...When you're in Leopard, the TM will show up as a drive on your Desktop just like Macintosh HD does, double click and you're in there, and can grab any file you'll need.  

Just keep in mind that when an update for hardware/firmware comes out, it's gonna take sometime for the Ubuntu community to play catch up, so don't go read something on Macworld and be so excited that you hose your Ubuntu installation...I speak from experience of "jumping the gun," on stuff like that :)

Good Luck, don't make it too complex!

---

### Post by cyberdork33 on 2009-02-20
> **darksidedude said:**
> you can do that?
yes.

> **darksidedude said:**
> but what should I do for the EFI not booting grub.
You need to follow the direction in the link given to sync your partition tables.

---

### Post by cyberdork33 on 2009-02-20
> **ajmctaggart said:**
> A Time Machine Backup can only be made bootable IF you choose the option when booting from Leopard Disk and select "restore from Time Machine." It takes awhile, but does work...that would effectively give you back your old Leopard system, so you'll have to erase Ubuntu or get some other type of USB/Firewire drive to hold the new installation.That is not booting from the Time Machine drive, that is restore the time machine backup (which is what it is for). You are still "booting" from the DVD.

> **ajmctaggart said:**
> I believe I have a better idea...

Here's the deal...
How much room is on the TM drive?  Partition that thing with a 15 Gig partition if possible for Leopard (That should hold it right?).

From that point, all your TM stuff is completely browse-able ONCE you're in Leopard (And maybe w/ Ibex' support for HFS, I haven't tried that...)

So, You need a small partition for a copy of Leopard, with nothing fancy installed, and go ahead and do all updates till your heart's content.  

You'll have access to all your TM stuff, just by browsing through the files, and you'll be able to get firmware/hardware fixes Apple releases going forward, etc...When you're in Leopard, the TM will show up as a drive on your Desktop just like Macintosh HD does, double click and you're in there, and can grab any file you'll need.   yep that is pretty much what I am suggesting as well.

---

### Post by ajmctaggart on 2009-02-20
cyberdork,

Didn't mean to "steal your thunder," :)

Correct, You are booting from DVD still...there's no way to use TM for a backup and then boot it...None whatsoever...at least not yet...

---

### Post by cyberdork33 on 2009-02-20
> **ajmctaggart said:**
> cyberdork,

Didn't mean to "steal your thunder," :)

Correct, You are booting from DVD still...there's no way to use TM for a backup and then boot it...None whatsoever...at least not yet...
agreement reassures uncertain users

---

### Post by darksidedude on 2009-02-20
WOW, Leopard takes way to much space on my harddrive!!. even with nothing extra installed on a 80gb drive only 61gb is available. ( thats without office 2004 I work or the printer drivers. Leopard is a vista!!!

I wish I had Tiger!

---

### Post by cyberdork33 on 2009-02-20
> **darksidedude said:**
> WOW, Leopard takes way to much space on my harddrive!!. even with nothing extra installed on a 80gb drive only 61gb is available. ( thats without office 2004 I work or the printer drivers. Leopard is a vista!!!

I wish I had Tiger!
you must not have done a custom install.

---

