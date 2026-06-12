---
title: "Need to start over installing"
date: 2007-12-22
forum: Apple Intel Users
---

### Post by brandon333 on 2007-12-22
Something went wacky, so now I am on a live cd  on my intel mac mini, no os whatsoever on it.

I want to dual boot ubuntu and osx tiger maybe leopard, not sure about reinstalling that.

Going to reinstall macosx and ubuntu , osx first and then:

After installing  osx first thing to do is go to disc utility and make 3 partitions:

How big should the small one be (swap) double your memory right i have 1 gig so 2 gigs?

How big should ubuntu partition big?

In the setting for each partition you have under the name you give it, you can select mac journaled, dos, etc, what should these be set to for each one? and then theres second selection for each in the options button, mrb, guid, etc, what should these be set to also?


Then once that is done I load live cd and select manual install selecting ubuntu partion and make it "/" right?

and then the small 2 gig swap: "swap"

then install......  any help would be great.


OR Can I should I install ubuntu first?

---

### Post by xeth_delta on 2007-12-22
I will offer my opnion on some of your questions.
> How big should the small one be (swap) double your memory right i have 1 gig so 2 gigs?

How big should ubuntu partition big?


Two GB of swap seem OK to me. From experience, I would recommend your / partition to be at least 15 GB. You will install a lot of programs there and it will be also the place where you store your personal files (unless you create a separate /home partition).
I believe having an extra partition, that both OS X and Linux can write to without complications, would be a good idea, in case you intend to share files between them. For instance vfat.

> 
In the setting for each partition you have under the name you give it, you can select mac journaled, dos, etc, what should these be set to for each one?


Those are most likely file system types. For the mac partion, journaled Mac or HFS+. For linux anything, you will format it anyway when installing ubuntu.

> 
Then once that is done I load live cd and select manual install selecting ubuntu partion and make it "/" right?

and then the small 2 gig swap: "swap"


Seems right.

> OR Can I should I install ubuntu first?
I suggest you install OSX first.

Xeth

---

### Post by brandon333 on 2007-12-22
thanks xeth  , ont he disc utility options there is an option for each partition:

master boot
guid
and um....geeze forget the other, I know guid should be picked along with mac jorunaled for mac but what about ubuntu and swap partitions, mbr right?

not worried about space or a fourth partition for sharing because I have a external hard drive and I am guessing I can share between os's in live ubuntu cd i can execute files from the external but cant write to but i think that is because i am on a cd.

then the final question (yea right,lol) what do i format external hard drive as or doesnt it matter?

---

### Post by bench on 2007-12-22
brandon333, I have a recent mac mini (the 2Ghz model).  I bought it with Tiger but reinstalled with Leopard as soon as I got the upgrade CD.

1. Install Leopard.  Use the whole disk with GUID partition table.

2. Install Refit. [http://refit.sourceforge.net/](http://refit.sourceforge.net/)  Download the Mac disk image (dmg) and install.  I had to go into Terminal then:

cd /EFI/refit
./enable.sh

Reboot and you should get the Refit selection menu (with just one option for Mac OS X).

3. From Leopard, open the Disk Utility and resize the Leopard partition to give approximately 16Gb free disk space.  The create two partitions, one 15Gb, one 1Gb.  Doesn't matter what format at this stage.

4. Insert your Ubuntu live cd and reboot the machine.  The refit menu should now have two options, one for Mac OS X and one CD option for Linux.  Choose the Linux CD option to boot Ubuntu from the CD.

5. Install Ubuntu.  When it gets the partitioning stage, choose manual.  In the partition manager screen, choose "edit partition" for your 15Gb partition.  Set the type to "ext3" and the mount point to "/" (without the quotes).  Make sure you tick the "format?" checkbox.  Choose the 1Gb partition and set the type to "swap".   Carry on through the screens and let Ubuntu install.  When it's finished reboot and eject the CD.

6.  When the machine reboots your refit menu will appear with two options - one "Mac OS X" and one "Linux".  Boot the Linux and Ubuntu should run.

Hope it works out.

---

### Post by brandon333 on 2007-12-22
are you sure that is the exact command, and is that 1 command or two?

I donloaded dmg installed and then typed that in terminal, rebooted and no go

and do i still hold "C" or "option" key ?

---

### Post by brandon333 on 2007-12-22
ok got it! that was 2 commands, if I wasn't a linux noob I would of known that, nice set up...easiest explanation of dual booting linux and osx I have ever seen, thanks.

couple things:

If i dont select anything at the refit screen it will go into mac osx by itself after a minute or so, is this normal?

I see my Mac Hd in linux but dont see my linux drive in osx, do I have to set up sharing to share between them, if so how do I do this, in osx i think i just click "shared" in get info, but how in linux?

---

### Post by bench on 2007-12-23
Yes refit will default to Mac OS X.  I haven't tried to change that because it automatically detects what OSs are available for boot (as oppose to the grub bootloader in Linux where they have to be specifically listed in it's configuration file).

Sharing your disks between Linux and OS X is a bit more challenging.  The Macintosh HD partition is protected in Linux only allowing root access.  I haven't done anything yet to try and access one from the other as I store most of my stuff on another networked Linux box.  I think there are a couple of threads on this forum that describe how to go about the sharing.

---

### Post by GeneralSunTzu on 2007-12-25
To simplify life, unless some really weird stuff is requred, please note that you can read, contrary to what many "wizards" suggest in this forum, the OS X partition even if journaled, without doing anything at all. 
All it will require will be your administrator password.
Writing to the OS X partition instead is so complicated to set up that I do not recommend it, better to write to an external HD or toast CD, if in dire straits.
Good luck !

---

### Post by xeth_delta on 2007-12-26
> **GeneralSunTzu said:**
> To simplify life, unless some really weird stuff is requred, please note that you can read, contrary to what many "wizards" suggest in this forum, the OS X partition even if journaled, without doing anything at all. 
All it will require will be your administrator password.
Writing to the OS X partition instead is so complicated to set up that I do not recommend it, better to write to an external HD or toast CD, if in dire straits.
Good luck !

I agree with GEneralSunTzu, but I don't think that slight sarcasm was needed ;) It is true you can read HFS/HFS+ partitions in linux without any problems. If you want to write to it (even though it can be rather problematic), you will need to disable journaling. That is why I suggested an extra "share" partition that both OSs can write to without issues.

Xeth

---

### Post by GeneralSunTzu on 2007-12-26
> **xeth_delta said:**
> I agree with GEneralSunTzu, but I don't think that slight sarcasm was needed ;) 
<snip>

Xeth

All right, all right, I promise I shall behave in the future.
Xeth_delta is right....
Having being myself a victim of quack "recipes" I was just letting  a bit of steam off...

I also strongly oppose software patents in the European Union (and in our galaxy too :), by the way).

---

### Post by xeth_delta on 2007-12-26
> **GeneralSunTzu said:**
> 
I also strongly oppose software patents in the European Union (and in our galaxy too :), by the way).

Thanks. Now, slightly off-topic. Indeed, the misuse and abuse of ambiguous software patents, where they already exist, is just ridiculous. Luckily, AFAIK, the EU does not have such a system, and I really wouldn't want it implemented here (and if possible, removed or the system reformed in other places, where they are already being used).
It can be seen that they hamper innovation and can simply be used as weapons (without real technical fundament or justification) by big corporations.
Enough with my rant for now :D

Xeth

---

