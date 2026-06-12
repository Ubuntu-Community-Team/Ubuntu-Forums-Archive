---
title: "Did I toast my Apple?"
date: 2014-03-21
forum: Apple Hardware Users
---

### Post by yonster on 2014-03-21
I'm going to attempt to make a long story short.  As some of you may know, I had been attempting to use the live disc option of lubuntu 13.10 on a refurbished Dell Latitude D630 laptop, because I am completely new to Ubuntu, and wanted to familiarize myself with it before deciding to actually install it.  Well, I didn't have much success with the attempts I made in installing pipelight, which had been recommended to me so as to be able to watch Netflix without Adobe Flash.  I was doing this because I was getting a lot of lagging in the video aspect when watching Netflix and was curious if using lubuntu instead of Windows/Adobe would solve the problem.  However, because I wasn't having success in being able to download pipelight, I decided to try the same process on a 2007 Mac-mini.

Well, those of you who are familiar with my previous posts are very aware that the term 'novice' would be overstating my ability to use computers, particularly in regards to the capability and understanding that most of you seem to have,,,  so true to form, somehow in the process of attempting to download pipelight on the Mac, not only was it unsuccessful, but I ended up just having to manually shut it down because it went haywire, to use the most efficient lay term I can think of.  The next time I turned it on without the lubuntu disc, instead of booting up with OSX as usual, all it said was to insert boot disc and press any key to continue and was completely unresposive to anything else I tried to do, such as press 'esc' for example.

So, as I highly suspect, did I somehow toast my Apple, and completely lose everything that was in it?  Anyone know?

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
> **yonster said:**
> did I somehow toast my AppleProbably not irremediably, but, if I understand correctly that it has some sort of Apple OS (whatever it came with) on it, this is probably not the best place to look for assistance in fixing it. I'd suggest you find a forum devoted to users of whatever OS is on it.

> **yonster said:**
> did I . . .  completely lose everything that was in it?Almost certainly not. But don't do anything to write to the disk until you have a clearer picture of exactly what happened. You can always boot from some other medium and copy the files out to another drive. Even if the filesystem is corrupted there is recovery software that can probably get most or all of your files back. Unless you've actually overwritten all the files (and that doesn't sound at all likely) you can probably get them back with a little effort and without spending real money. Even if they are overwtiten it is still theoretically possible to recover some of them, but in that case you would be talking expensive professional recovery. Pretty hard to overwrite them without trying to though.


> **yonster said:**
> Anyone know?Of course. NSA knows all, sees all, hears all, but understands almost nothing because idiocy is a requirement of all federal employees.

---

### Post by yonster on 2014-03-21
Thank you so much DFA!!  I had begun installing lubuntu 13.10, but didn't get very far because I am using the 'Something else' option, and trying to install suggested partitions.  If I understand the concept correctly, using this option (properly) will also not overwrite any existing files--  sound accurate?

---

### Post by PartisanEntity on 2014-03-21
Hello there, did I understand you correctly, you tried to install Lubuntu 13.10 on the Mac? Because the way I understood your first post was that you wanted to *try* it on the Mac using the live CD.

---

### Post by tgalati4 on 2014-03-21
Macs are partitioned using HFS+ file system, not Ext4 file system that linux prefers.  So it's not clear exactly what you did.  I would take it to an Apple Store and make an appointment at the Genius Bar and wait several hours to be seen.  Then have them tell you that you are out of Apple Care (since the machine is only 7 years old).  Make sure you record the conversation with your iPhone, since that is pure entertainment value.

If you used the Gparted, the partitioner that pops up when "Something Else" is selected, then it is possible that you overwrote your OS X operating system.  "Something Else" is code for "I know exactly what I am doing and I am responsible for what happens, so I want to do Something that might screw up my system, but I have nothing Else to do this afternoon."  That got shortened to "Something Else".

If you have data that you need to recover, now is the time to read up on recovery tools.  If you don't have any data on the disk, then you can either reinstall OS X or read up on the tricks required to get Ubuntu installed on a Mac.

---

### Post by bapoumba on 2014-03-21
Moved to Apple Users.

---

### Post by yonster on 2014-03-21
Yes, please let me clarify... I was using the live disc while performing the attempted/gone haywire pipelight download.  I guess the first question might be:  Is it even possible to download in live disc mode?  Could that possibly be why I haven't had any success (outside of being a complete and mentally challenged noob) performing these procedures?  

The way that it happened was I was entering the prescribed method for pipelight installation into the terminal, from an FDSteam link I was given.  By haywire, I mean that it suddenly started opening excessive web tabs, a screen for 'a script has stopped working, stop or continue?' would continue to appear, but would take aeons to respond, and the cursor was highly uncooperative/ extremely slow.  It seemed as though it would take a week to close all the scripts/tabs the way it was acting, so I naturally "pulled the plug."  When I turned it on the next day, that's when it wouldn't boot as normal, and only showed a terminalesque screen saying to install a boot disc to continue.

That's when I posted this topic.  As I continued to check on any replies, for the first couple of hours NO ONE seemed to either read or of course reply...  so in the meantime, since it seemed like I really didn't have anything to lose, I started following some suggestions I had previously received, and hadn't tried yet, for actually installing lubuntu on the Mac-mini using 'Something else' and suggested partitions.

I hope that helps to clarify things a little.  Another clue that might help solve whether or not I managed to wipe my files, is that while toying with the install I discovered I have 160 GiBs of free space, which to me sounds about as much memory as probably came when it was new, yes?  The main question at this point is that by using the suggested partitions, IF the files haven't been wiped yet, will they still be recoverable after installing lubuntu this way?

And I can appreciate your cynicism about what it takes to *not* have you question satisfactorily answered after waiting at the nearest "friendly" Apple store, tgalati4...  I suggested my parents buy the Mac-mini because I thought Apple was the 'cool' alternative to pc's--- boy was that a mistake!  I'll be disappointed if I can't recover some pictures, etc, but other than that I will NOT miss OSX!!  Thanx to all of you who have replied!

---

### Post by tgalati4 on 2014-03-21
Yes, you can download and install during a Live Session, but everything is kept in RAM, and then immediately lost when you shut down.  Of course, if you run out of RAM during an install, then bad things will happen.  That is perhaps what happened in your case.

My cynicism is based on my experience with several Apple products over the years that fail just over the Apple Care warranty.  If you don't have Apple Care, you are 1.  Not Cool. and 2.  Out of luck.

Use *testdisk* to recover the partition.  It requires quite a bit of skill to install a new operating system on a Mac.  Have you ever removed a Ferrari engine?  About the same difficulty.

---

### Post by yonster on 2014-03-21
What is "*testdisk*"?  And NO, I tend to get injured working on my beat up old Volvo.  Apple Care was not selected at time of purchase because the research of "professionals," people who sold both Apple and pc products said "once a Mac leaves the store, we don't see it again," therefore Apple Care smacked of an unnecessary whistle that folks who struggle to afford Apple product costs can't afford. 

So the gist of what I'm understanding you say at this point is that as far as you're concerned my Apple is indeed toast, outside of whatever "*testdisk"* is reveals?

And yeah, I guess you could say I gave up on being cool with steering my parents to purchase this Mac-mini.

One last thing... I wasn't attempting to install a new OS at the time it melted down; I was trying to see if I could successfully install pipelight on it, having failed to successfully install it on an old Dell Latitude laptop.

---

### Post by Dreamer Fithp Apprentice on 2014-03-22
> **yonster said:**
> Thank you so much DFA!!You are most welcome.

> **yonster said:**
> using the 'Something else' option, and trying to install suggested partitions.  If I understand the concept correctly, using this option (properly) will also not overwrite any existing files--  sound accurate? . . . er . . . yeees. Depending on who was suggesting, or more precisely, what was suggested. And provided there is not some joker in the Apple deck I don't know about. I know very lilttle about Apples. The idea when you use "something else" to install to a drive that has no significant unpartitioned space is to shrink an existing partition to make enough room to create a partition big enough to install in. Or multiple partitions if you want to do it that way. Certainly for any gnu/linux system, or more broadly, for any unix-like system or dos-like system that uses filesystems that gparted understands, that is pretty straight forward. As far as I know it is still pretty straight forward for Windows too but I don't know anything about W8 or the new efi booting procedures. And it seems they are always trying to come up with ways to make Windows not play nice with other operating systems.
I don't know about Apple filesystems but I imagine if you looked you could find some combination of software in the repositories that could deal with whatever filesystem(s) it has, shrink them properly, and do the repartitioning. After all we can deal with FAT, NTFS, and Finagle knows how many other kinds of non-native filesystems, so I doubt if Apple has been left out. You would have to install it in the live disk which will use a lot of RAM but it is probably doable. But that is all academic at the moment. Your first priority needs to be to recover your data, i.e., the "pictures, etc." you refer to. If you boot a live disk and can read all the files you want to recover  just copy them to some other media, such as a usb stick (they are  getting to be fairly cheap) or if the total amount of files isn't that  great you could even email them to yourself at a webmail account or pile  them into an archive and upload to a file locker. Or burn a cd if you  have 2 cd drives. Lots of options there if you can access the files.  Once you are sure you have them copied to some place safe, and  preferably backed up a second time to some place else also safe, and  verified you can read the copies, then you can decide what to do next without fear of losing the data.

 If you wanted to conserve the OS it had and make it dual bootable I'd concentrate on fixing the one that it has first and after it was working I'd study up on tools to shrink the partition it is on (which of course implies shrinking the filesystem, which probably means that whatever system you use to do the shrinking has to understand the filesystem but I'm not absolutely certain of that). If you are just plain short of drive space anyway a second drive might make everything easier.

But -> **yonster said:**
> I'll be disappointed if I can't recover some  pictures, etc, but other than that I will NOT miss OSX!!If you are absolutely sure about that things get radically easier. After securing your data as discussed above, you can install over the existing OS easily. As for partitioning in that case I personally would still use the manual "something else" because I think life is a LOT easier if you keep your data on a seperate partition from your OS(s), but not everyone agrees.

---

### Post by slooksterpsv on 2014-03-22
It's always good idea to make a backup.

testdisk is a utility you can use on *buntu to help recover lost partitions, files, etc. If you boot into *buntu Live CD, connect it to the internet, and install testdisk, you can run it to see what's going on.

Depending on the size of the disk, yeah 160GB could have been the entire disk.

Normally with a mac if you hold the Option key it'll give you a list of bootable OS's - be it the hard drive, external, cd, dvd, usb, etc.
Now if everything did get wiped, yes testdisk may be able to recover the data - no guarantee, but its possible.

---

