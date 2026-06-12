---
title: "[SOLVED] BIG data recovery problem - please help"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-12-20
I had been having some trouble with my old Samsung SP0802N hard disk drive (80 GB, IDE drive), so I replaced it with a new hard disk. 
I tried to transfer the data from the old one to the new one, but accidentally plugged in a USB 2.0 IDE converter the wrong way. Something smoked, and the PCB board got damaged.
Anyway, I gave the disk to data recovery pros and they say that recovering data from a Linux disk is more difficult. So they are asking for a LOT of money - Rs. 40,000 (that's more than $1000) - to recover it.
That disk contains all my important data - work, papers, photos, music - it's painful to even consider not having it back. At the same time, I cannot afford the kind of money these people are asking for.
The unfortunate part is that while I'm usually particular about backing up my data, I was sort of in the middle of it when all this happened. I haven't been able to do any work for a while now, and know too little about data recovery to figure out what to do.
I'm at my wit's end, and would really appreciate any help or advice on how to recover that data. Also, could someone tell me if their claim about recovering data from Linux disks being harder is true? Logically, (inferring from what my computer technician told me and Wikipedia's page on data recovery) is this not a matter of replacing the PCB board?
Thanks.
P.S.: I curse my idiocy a thousand times everyday as it is, so it won't help to wonder how someone could possibly plug in the connector incorrectly or be stupid enough to not back up their important data.

---

### Post by lintoon on 2007-12-20
You could check ebay for an identical hard drive and swap the boards.

---

### Post by kleo skywalker on 2007-12-20
> **lintoon said:**
> You could check ebay for an identical hard drive and swap the boards.

Swapping the boards is not the issue. The hard disk was given to a computer technician who swapped the board, and then took it to the data recovery people, who then asked for the whopping sum of money. I just don't know what to do next.

---

### Post by lintoon on 2007-12-20
> **kleo skywalker said:**
> is this not a matter of replacing the PCB board?

Sorry, I didn't realise you had tried replacing the board.  I've rescued a few like that.

---

### Post by kleo skywalker on 2007-12-21
> **lintoon said:**
> Sorry, I didn't realise you had tried replacing the board.  I've rescued a few like that.

The thing is, I don't know what to do *after* the board has been replaced - do I just use the disk normally?
Like I said earlier, the computer technician swapped the board, and then took the disk to the data recovery people. They asked for a lot of money that I don't have.
So now, I *can* get my disk back with the good board, but then what do I do?

---

### Post by Sef on 2007-12-21
Check out [Knoppix]("http://knoppix.com").  You might be able to use it to copy the files to a usb key or other hard drive.

---

### Post by kleo skywalker on 2007-12-21
> **Sef said:**
> Check out [Knoppix]("http://knoppix.com").  You might be able to use it to copy the files to a usb key or other hard drive.

I'll look up Knoppix (I don't know how to use it).
My problem starts a couple of steps behind this - what do I do with the hard disk? Should I just fit it internally and access the data using Knoppix or something?
Excuse me if this is too basic a question, but I'd rather ask it than mess up further.
Thanks.

---

### Post by Paulmd on 2007-12-21
> **kleo skywalker said:**
> Swapping the boards is not the issue. The hard disk was given to a computer technician who swapped the board, and then took it to the data recovery people, who then asked for the whopping sum of money. I just don't know what to do next.


Why'd he bother to swap the board, if he was just going to turn it over to data recovery pros?

I'm thinking there's 3 possibilities:

The controller card swap didn't work (it's a hit and miss kind of thing).  If it had, you probably would have gotten your data back by now.

OR 

The technician doesn't know how to handle linux partitions. 

OR

The physical surface of the drive is also heavily damaged. 

Should you go through with the data recovery? Only you can decide what your data is worth.

---

### Post by Paulmd on 2007-12-21
> **kleo skywalker said:**
> I'll look up Knoppix (I don't know how to use it).
My problem starts a couple of steps behind this - what do I do with the hard disk? Should I just fit it internally and access the data using Knoppix or something?
Excuse me if this is too basic a question, but I'd rather ask it than mess up further.
Thanks.

When dealing with questionable drives: It's best to kook it up internally. No usb or firewire cages, and whatnot. 

What you should do is make a clone of the drive. (you need a hard drive of equal, or larger capacity)  There's a linux based tool called ddrescue that works fairly well. Just keep straight which is the source and which is the destination. (you get them wrong and you can overwrite the wrong drive)

Once you made your clone, then pull the data off of the clone drive.

---

### Post by dptxp on 2007-12-21
Plug the drive to any good machine, boot with Puppy Linux (or Knoppix). Puppy
is a small distro. Mount your partitions and pick up your files. With Puppy the CD drive is free as Puppy loadsto RAM (128 MB min needed). With Knoppix to run from RAM you need 1 GB RAM.
So you will be able to write do CD from HDD using CD burner.

---

### Post by bobpur on 2007-12-21
Go to [www.distrowatch.com](www.distrowatch.com) and download System Rescue CD. It has recovery software. You, probably, will find further help on their forums.

Good Luck!

---

### Post by kleo skywalker on 2007-12-21
Thank you everyone, I'm forwarding all this information to the technician who has my hard disk. (At this point, things don't look so good - he says the platter head or something is damaged and he needs to replace it. Of course, I'm freaked.)
bobpur, if you've used System Rescue CD, could you briefly tell me how it works?
dptxp, when you say mount partitions when booting Puppy Linux or Knoppix, do you mean the /, /home and swap partitions on the damaged disk?
Thanks again.

---

### Post by dptxp on 2007-12-21
YES. You can mount any partition you like.

---

### Post by az on 2007-12-21
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

The Rescue-remix has all the software that any other data recovery toolkit can have.


It's unlikely that your platters got dammaged by plugging the thing in the wrong way.  Platter get dammaged when you drop the drive on the floor, or if the drive is really old and the surface weakens, allowing pieces of the media to physically break off and cause your head to scratch the surface.

It's also fishy that they said it's harder to recover stuff from a linux hard disk.  It's exactly the same.  It's even easier, in fact.

My suggestion is that you try to find another data recovery service.

---

### Post by Paulmd on 2007-12-21
> **kleo skywalker said:**
> Thank you everyone, I'm forwarding all this information to the technician who has my hard disk. (At this point, things don't look so good - he says the platter head or something is damaged and he needs to replace it. Of course, I'm freaked.)
bobpur, if you've used System Rescue CD, could you briefly tell me how it works?
dptxp, when you say mount partitions when booting Puppy Linux or Knoppix, do you mean the /, /home and swap partitions on the damaged disk?
Thanks again.



If what he's talking about is the read head, then that is truly an operation that can only be performed by the pros. No software can make this work. The drive needs to be disassembled in a clean room, and repaired very carefully.

There are a handful of highly risky "get lucky" techniques, that amateurs can do.

One involves banging the drive on the bench in an attempt to unstick the head. Don't do it, it can make things much worse!

---

### Post by Duck2006 on 2007-12-21
This is how to use knoppix to do it.

[http://www.ibm.com/developerworks/linux/library/l-knopx.html](http://www.ibm.com/developerworks/linux/library/l-knopx.html)

A other way is to use testdisk.

---

### Post by dstew on 2007-12-21
My son had a similar problem when a powered USB hub burnt up his USB 2.0 port on his computer. The hub had manufacturing defects. Since the other ports (USB 1.0) were still working, he was able to read the external drive, but could not boot it. The problem was that USB 1.0 could not boot an external disk. The disk was not damaged, only the computer board. From your description, I suspect your disk was not damaged, but that the recovery people are confused. Get your drive back, and try to plug it in to a regular IDE cable, and see what you get.

A darker scenario is that the recovery people screwed up and damaged the disk, and are blaming it on the original event.

---

### Post by kleo skywalker on 2007-12-22
Thanks everyone.
I guess my only option right now is wait for the person who has my disk to get back to me and tell me what's up with the disk, and then choose the next course of action.

---

### Post by PreviousN on 2007-12-22
I feel like all these guys are giving you good info, but in a rather clumsy way. Its' all clustered. So here you go, at a more full explanation:


* They are lying to you. Recovering data from a linux disk is about the same as any other os. It should be cheaper because the recovery tools are mostly free and open source. 

== If the disk is physically damaged ==
1. It can only be fixed at a pro shop. It needs to be taken apart in a clean room and very meticulously taken care of. This does in fact, usually, cost about 600-1000+ dollars. 
2. If this is the case, shop around. There are multiple shops that do the same thing. 


== If the disk is not physically damaged (ie: no clicking sound when plugged in, no clanks, just running smoothly). ==

1. Get yourself a live cd. These people seem to favor Knoppix/puppy/ubuntu rescue. Personally I've used Knoppix and Ubuntu (I'm a tech consultant in real life...at least I play one). Anyways, I prefer knoppix, but your mileage may vary. 
2. What you're gona need is a disk that is significantly bigger than the failed disk. (or at least a few gigs bigger). 
3. Put both disks in your computer. boot up. DO NOT WRITE TO THE BROKEN DISK! DON"T EVEN READ IT!!!! DON"T EVEN BROWSE THE INTERNET ON THAT COMPUTER. Anything you do that may accidently put cache (like cookies, or etc) on the broken disk may make data irrecoverable. 
4. Get "ddrescue". This is a program that copies data, bit by bit, 1's and 0's (I guess), from one location to another. In fact, its just the program "dd" with a logfile. This program is extremely useful. You can even stop revery in the middle and restart later because of the log. 
5. What you'll do, is use ddrescue to copy from one drive to another. Once thats done, turn off the computer and remove the damaged drive. This is so you don't mix up things. 
6. Now, you'll have an image of the damaged drive. What do you do with it? run fsck!
7. You should be able to migrate the data to a more perminant location, or burn it to a disk. 

Hope that helps. Basically, its like this: if the drive is physically damaged, you gotta pay up. If they're being assholes because you use linux and the drive isn't physically damaged, you can save it (maybe). 

Honestly, its up to you. If you pay up, you'll get your data back. If you don't, theres a lot of room for error in this procedure. Good luck :-)

---

### Post by kleo skywalker on 2007-12-22
PreviousN, thank you very much for your post. About the physical damage on the disk, I only have the technician's word for it, and this is what he tells me: he changed the PCB board but the disk is not being detected when he plugs it in, it makes noises of the kind you mention, and that makes him suspect a jammed platter or a damaged head or something. I can only hope he gets it working.
I wish I'd asked this question as soon as my hard disk started giving trouble, and not after it had been in the hands of several technicians. I also regret not knowing anything about hardware - knowing some simple facts would've saved me so much trouble. I wouldn't have taken what the computer technicians told me at face value and probably not been in this huge a mess.
The above is not a rant, I'm posting as a warning to that people in similar situations, and hope they won't make the same mistakes I did.

---

### Post by kleo skywalker on 2007-12-22
While I wait to hear from this person, could someone tell me how these platter problems are solved?

---

### Post by Paulmd on 2007-12-22
> **kleo skywalker said:**
> While I wait to hear from this person, could someone tell me how these platter problems are solved?

The data on the platters themselves is rarely badly damaged. But a lot of mechanical problems can prevent the drive from being read by software. 

1) The read head can become jammed, or otherwise become inoperable. It looks a lot like a phonograph arm. 

2) the hard drive motor can stop spinning

3) the controller card can become inoperable.

4) there are a host of other causes, but they have a similar cure. The hard drive must be dismantled and put on a special reader, or otherwise repaired. This requires a clean room because dust in the atmosphere will act just like sandpaper once the drive starts spinning and eat away at the surface of the disk in a hurry.  People have gotten away with the "cowboy" approach, and repaired the drive, and made a clone before it dies for good.... but it's not exactly wise.

The cowboy approach requires several factors. Skill, luck, and either stupidity or desperation.


If your technician pulled a controller board swap, and the drive is  still not recognized by the bios, and is making the click of death. The best thing to do is to go to a data recovery expert. This has nothing to do with the filesystem, it's just plain mechanical failure.

The why linux is difficult to recover data from rumor relates only to EXT3, and applies only in the case of deletion. Seems ext3 removes references to where a file was stored. So you have to find deleted files the hard way. tedious, but not that difficult. It does not apply to your situation.

I think the technician is not lying, but he may be misinformed. Most techs don't get 100% correct info on linux, and little experience. He may be out of his depth on that, but I think the main problem is the drive isn't being recognized by the bios.


Many major hard disk manufacturers do data recovery. Seagate, WD, and even IOMEGA. Some offer a no-data-no-money policy, and will do free estimates. You'll have to ask. Your drive can almost certainly be recovered by a specialist.

---

### Post by dptxp on 2007-12-23
Never trust a hard disk.
Flash memories are best for data backup. No moving parts. No scratches like in CDs.

---

### Post by Paulmd on 2007-12-23
> **dptxp said:**
> Never trust a hard disk.
Flash memories are best for data backup. No moving parts. No scratches like in CDs.


The Problem with flash is high price for the amount of storage. Anything more than a few GB bay be cost prohibitive. Also they can be very, very, hard to recover should the media fail.

---

### Post by PreviousN on 2007-12-23
You know, hard disks now days are pretty reliable. I've seen them last for 8+ years. Flash technology (like a flash keydrive) hasn't even been around that long. Also, there's a limit on how many times you can rewrite over them. So...Who knows for sure how long their flash disk will last?!  I know they take thousands...but...

Also, if you put a hdd in a raid, even a software one, you'll have less than a .01% of both drives being out at once. And if you have it in a raid 5, you have even lower. 

But you're partially correct in saying that flash is very strong...I've seen them run over by cars and still work...I just don't know how they stand up to the test of time. We'll just have to wait and see... :popcorn:

---

### Post by kleo skywalker on 2007-12-23
> **PreviousN said:**
> 
6. Now, you'll have an image of the damaged drive. What do you do with it? run fsck!

I'm trying to compile these instructions in as much detail as possible to email the chap who has my hard disk, and I don't know how to run fsck. I'd be very thankful if someone could tell me how it works.

Also, when I go to the Knoppix, Puppy Linux and ddrescue websites to download them, there's this whole list of things - which one am I supposed to download?

Thanks a lot.

---

### Post by PreviousN on 2007-12-23
I know this is a copout, but the copy from the man page of ddrescue....

Ddrescue
Jump to: navigation, search

ddrescue is a raw disk imaging tool that "copies data from one file or block device to another, trying hard to rescue data in case of read errors." The application is developed as part of the GNU project and has written with UNIX/Linux in mind.
Examples

These two examples are taken directly from the ddrescue info pages.

Example 1: Rescue an ext2 partition in /dev/hda2 to /dev/hdb2

    ddrescue -r3 /dev/hda2 /dev/hdb2 logfile
    e2fsck -v -f /dev/hdb2
    mount -t ext2 -o ro /dev/hdb2 /mnt

In this example, ddrescue is retrying 3 times. At the end it will compare using a logfile to make sure all data that it can get is back and spiffy. 

So, I haven't done this too much (like twice...we just don't have to do this very often where I work/at home) but after your data is back on the other partition/disk, you'll run this command...

```
fsck -v [device] 
```

fsck (reiserfsck, or e2fsck, depending on the file system..) is basically a disk repair tool, -v stands for verbose and -f is...I can't remember. It isn't functional yet in reiserfsck though (at least in my version). I think you likely have ext3 because thats what ubuntu usually installs by default, but honestly, I ONLY use reiser for my hdds. I just prefer it more. Maybe someone else on the forums can give you better command advice with ext3. 

Anyways,

Then, after running fsck, the code, 

```
mount -t ext2 -o ro /dev/hdb2 /mnt
```

Basically means, "mount a type ext2 partion in read only from /dev/hdb2 to /mnt"

After you do that, you can open up "/mnt" in nautilus or in terminal, and you'll magically see all the data it saved!
Hope this helps. 

Oh, and I would recommend getting the torrent for knoppix. It cuts down on the costs for their server AND you could potentially get it faster. Here's a link:

[http://www.tlm-project.org/public/distributions/knoppix-std/0.1/i386/knoppix-std-0.1.iso.torrent](http://www.tlm-project.org/public/distributions/knoppix-std/0.1/i386/knoppix-std-0.1.iso.torrent)

Cheers!

---

### Post by kleo skywalker on 2007-12-23
PreviousN, can't thank you enough for the details, even if I don't understand it at all!

---

### Post by Paulmd on 2007-12-23
> **PreviousN said:**
> You know, hard disks now days are pretty reliable. I've seen them last for 8+ years. Flash technology (like a flash keydrive) hasn't even been around that long. Also, there's a limit on how many times you can rewrite over them. So...Who knows for sure how long their flash disk will last?!  I know they take thousands...but...

Also, if you put a hdd in a raid, even a software one, you'll have less than a .01% of both drives being out at once. And if you have it in a raid 5, you have even lower. 

But you're partially correct in saying that flash is very strong...I've seen them run over by cars and still work...I just don't know how they stand up to the test of time. We'll just have to wait and see... :popcorn:

Pendrives are weak at the usb connector. The PCB material itself is very strong. (just try to break your typical pci card in half bare handed. It's possible, but not easy.)

The Other thing that happens is they're more vulnerable than they should be to static electricity. Some models of course are better than others, but the real cheap ones you can zap'em sometimes by touching the usb connector. 

Raid arrays can fail when the raid controller goes. It can sometimes be a bad problem, as the array may not be compatible with a new controller. Sometimes.

Limit on rewrites on flash (the stuff that goes into pendrives, anyway) is at least 10,000 rewrites. Different chips are rated differently. Sometimes in the millions.

As for hard drive life span, a surprising number of 386s and 486s still work on the original hdd. So that's quite a long time.

---

### Post by kleo skywalker on 2007-12-23
There's no end to my stupid questions.
Another one: I sort of compiled what I gathered from all the helpful responses to email the person who has my disk. The thing is, I'm afraid they are not detailed enough. (How do I give more details when I don't know how to use some of the things I'm suggesting?!)
I'd be very thankful if someone could take a look at it and tell me if it's enough for a data recovery person even if they're not very familiar with Linux.

> This may be useful in case the data recovery people are not familiar with Linux.

The following are needed:

    * A spare, clean hard disk that is at least a few GB larger than my disk.
    * Knoppix (download from here and burn to CD as iso image)
    * ddrescue (download from here)

   1. After repairing the hard disk in clean room conditions, plug in my repaired hard disk and the spare disk into a machine.
   2. Boot from the Knoppix CD. Do NOT write to or read from the broken disk, don't even surf the internet on that machine.
   3. Use ddrescue to make an image of my repaired disk to the spare disk.
   4. Data can be accessed from this spare disk.

---

### Post by Paulmd on 2007-12-24
> **kleo skywalker said:**
> There's no end to my stupid questions.
Another one: I sort of compiled what I gathered from all the helpful responses to email the person who has my disk. The thing is, I'm afraid they are not detailed enough. (How do I give more details when I don't know how to use some of the things I'm suggesting?!)
I'd be very thankful if someone could take a look at it and tell me if it's enough for a data recovery person even if they're not very familiar with Linux.

Once it goes to the data recovery pros, and out of your small shop tech, it'll be in good hands.

Intructions for the big boys are more on the order of "rescue my documents, and pictures, and everything in my home directory and put them on cds. PS, I have Ubuntu linux 7.10 installed."

The instuction set you gave implies that it will be sent to a specialist. After all, the specialists are the ones with the clean rooms.

Instruction set for the tech would be more like "send it to the data recovery people"

---

### Post by PreviousN on 2007-12-24
Yeah... If you've already sent it to the pros (ie: the people who charge in the hundreds - thousands), the pros should know how to handle any kinda data. In fact, what they usually do is have their own tool for bit by bit copying. So once its out of the hands of the lesser experienced guy, and to the big boys with the clean room you shouldn't have to tell them much. Just something like "please save everything" would likely even do. 

And you don't have to tell the guys with the clean room to get knoppix. They probabally already use linux or bsd, maybe even their own specialized distro. Its not uncommon for big shops/companies to use linux. Hell, even google runs on their own special customized version of ubuntu (some of it...that is).

---

### Post by kleo skywalker on 2008-01-08
I need some urgent advice - the data recovery people just emailed me this text file with a sort of list of the "recovered data" - I don't get all of it, but it's definitely incomplete - less than half my stuff is there.
To be precise, there is no home folder at all, and other than files in /bin etc (which I can't figure out anyway, and don't need), there's only one user's mp3 files. (There were 2 users on this computer - my brother and me.) I can see most of my brother's mp3 files (strangely in a folder with my name on it) and nothing else - not his pictures or documents, and nothing that was in my folder - music, pictures, documents - nothing!
This is scary and befuddling. Can someone offer any clues or explanations?
Many thanks.

---

### Post by kleo skywalker on 2008-01-08
> **kleo skywalker said:**
> I need some urgent advice - the data recovery people just emailed me this text file with a sort of list of the "recovered data" - I don't get all of it, but it's definitely incomplete - less than half my stuff is there.
To be precise, there is no home folder at all, and other than files in /bin etc (which I can't figure out anyway, and don't need), there's only one user's mp3 files. (There were 2 users on this computer - my brother and me.) I can see most of my brother's mp3 files (strangely in a folder with my name on it) and nothing else - not his pictures or documents, and nothing that was in my folder - music, pictures, documents - nothing!
This is scary and befuddling. Can someone offer any clues or explanations?
Many thanks.

Please help!

---

### Post by ByteJuggler on 2008-01-08
> **kleo skywalker said:**
> Swapping the boards is not the issue. The hard disk was given to a computer technician who swapped the board, and then took it to the data recovery people, who then asked for the whopping sum of money. I just don't know what to do next.

If he's swapped the board, is the drive then still not accessible in a Pc?

Edit: never mind, I need to read the rest of the thread it seems...

---

### Post by ByteJuggler on 2008-01-08
Personally, if I was in your shoes, my goal would be to get the drive back, in a state where the BIOS picks it up.  Once you're at that point, you can give attention to recovering the files from the (apparently now damaged) filesystem.  I would aproach that as has been suggested, by imaging (using e.g. ddrescue or so) the original disk to another working disk (or ideally 2 disks), and then doing data recovery/filesystem checks/fixes on there.  If any particular tool messes up, you then still have the original disk (or the second copy) so you can start again.

---

### Post by kleo skywalker on 2008-01-08
> **ByteJuggler said:**
> If he's swapped the board, is the drive then still not accessible in a Pc?

Edit: never mind, I need to read the rest of the thread it seems...

Briefly, my disk finally reached some data recovery people who repaired the disk (I'm not sure of what they did, but I think they replaced a head or some such.) The disk was detected, and they emailed this complex text file which was sort of a list of what they'd recovered for me to check.
The problem with this list is described in my previous post. Also, I see some things similar to a Windows file system - My Documents, My Pictures and stuff, which I'm pretty sure shouldn't be there.
I called them with my doubts and they say that the data has been "corrupted" and this was what they could recover; and that they were trying to do some more stuff to see if more could be recovered.
I'm confused and worried, so I'd really appreciate if someone could throw light on what might be happening here.
Thanks very much.

---

### Post by kleo skywalker on 2008-01-08
> **ByteJuggler said:**
> Personally, if I was in your shoes, my goal would be to get the drive back, in a state where the BIOS picks it up.  Once you're at that point, you can give attention to recovering the files from the (apparently now damaged) filesystem.  I would aproach that as has been suggested, by imaging (using e.g. ddrescue or so) the original disk to another working disk (or ideally 2 disks), and then doing data recovery/filesystem checks/fixes on there.  If any particular tool messes up, you then still have the original disk (or the second copy) so you can start again.

That would make sense if I was any good at it.
I was the one stupid enough to plug in a USB 2.0 IDE converter upside down and ruin the disk in the first place, so I don't trust myself to do this.
Plus, I haven't spoken with the tech people who're doing the actual work, so I don't know what state the disk is in or exactly what they're doing to it now; and therefore if at all they can give the repaired disk back to me.

---

### Post by ByteJuggler on 2008-01-08
> **kleo skywalker said:**
> I need some urgent advice - the data recovery people just emailed me this text file with a sort of list of the "recovered data" - I don't get all of it, but it's definitely incomplete - less than half my stuff is there.
To be precise, there is no home folder at all, and other than files in /bin etc (which I can't figure out anyway, and don't need), there's only one user's mp3 files. (There were 2 users on this computer - my brother and me.) I can see most of my brother's mp3 files (strangely in a folder with my name on it) and nothing else - not his pictures or documents, and nothing that was in my folder - music, pictures, documents - nothing!
This is scary and befuddling. Can someone offer any clues or explanations?
Many thanks.

It's hard to know how they generated this list etc. without knowing what they've done and what tools they've used.  It sounds like they've run a filesystem recovery tool on the disk and that this is what the tool identified as recoverable.  The fact that things appear to be crosslinked suggest that for some reason the tool had to do some reconstructive surgery (as it were) on the filesystem and perhaps relinked your brothers folder to your home folder (and/or hasn't found your actual document folders for some reason.)  All this, *may* be due to the disk having developed filesystem damage somewhere along the line.  The question is whether the filesystem damage is due to logical or physical causes.  

Now, it's fairly unlikely that your original PCB frying wouldv'e been the cause of physcial head/platter damage (although I can conceive of an unlikely hypothesis about how it might've happened, depending on whether the physical design of the heads/head controller etc is such that they can be physically damaged if sent totally incorrect electrical control signals hence moving in a way/to a place where they then acquired physical damage, as was the case in years gone by with hard drives.  I'd expect this not to be the case with modern drives, but I cannot therefore rule out the possibility that the PCB frying caused knock on damage.  But, I digress.)  In any case, it seems that there has nevertheless been some platter/head damage (based on what I've gathered in this thread) so it's possible that the result of what they sent you is what was recovered/visible from the dying disk.  If however the filesystem was just logically damaged (perhaps the frying just wrote garbage to parts of the disk) then the damage is likely less severe and should with a bit of luck be recoverable with a filesystem check (as has also been suggested) once it's located a physically working hard disk.

If I was you I'd like to find out the following:
1) Confirm whether there is/was in fact physical head/platter damage (and when that might've happened/could've been caused by the PCB frying.)
2) What was done about it if anything. Was the drive put together again semi-broken and the recovery done like that or was a new head fitted as well?  Was this done in clean-room conditions? 
3) What state the drive is in now.  Is it idetified by a normal PC by the BIOS?  Is it stable or in a deteriorating state?
4) Has a binary bit image been made of the disk?  Is a copy of this available somewhere?

If there was head damage, then the head should be replaced to maximise data recovery chances (and/or imaging quality), otherwise you're obviously unlikely to be able to read/recovery whatever was on the platter under that head which might end up punching holes in many/most of your files.  Unfortuantely I cannot advise in this respect as I've never dealt with someone capable of actually doing that level of physical hard drive repair.  (Let's hope that there was no or no serious platter/head damage.)

To recover the filesystem (assuming it's somehow damaged) and/or data from it, there's several approaches one might take. The simplest is, run the filesystem check utility (fsck) and see what happens.  In many cases it will fix a slightly damaged filesystem very well (and lost stuff will appear under "lost+found" folder, perhaps with the wrong name.)  If the filesystem is very badly damaged and you can't rely on it anymore, I'd also try "PhotoRec" ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)), which is a tool which tries to recover only files without relying on any filesystem information.  It relies on files not being fragmented, so in that respect may fail if you had a badly fragmented disk.  Fortunately Linux is quite fragmentation resistant so that would improve your chances using this tool.  Lastly, if both these fail and there's specific files you need to recover, you can do your own manual data slicing/carving/reconstruction by searching/"grepping" through the disk image and cutting out bits you want to save.  Obivously that's very time consuming and usually boild down to saving the barest essentials of what you want to save.

Edit: OK some of the above was answered before I posted this.  So ignore as appropriate.

---

### Post by ByteJuggler on 2008-01-08
> **kleo skywalker said:**
> Briefly, my disk finally reached some data recovery people who repaired the disk (I'm not sure of what they did, but I think they replaced a head or some such.) The disk was detected, and they emailed this complex text file which was sort of a list of what they'd recovered for me to check.
The problem with this list is described in my previous post. Also, I see some things similar to a Windows file system - My Documents, My Pictures and stuff, which I'm pretty sure shouldn't be there.
I called them with my doubts and they say that the data has been "corrupted" and this was what they could recover; and that they were trying to do some more stuff to see if more could be recovered.
I'm confused and worried, so I'd really appreciate if someone could throw light on what might be happening here.
Thanks very much.

Sounds like some person (idiot?) installed Windows on the disk in order to recover it (probably to install recovery software.)   If they did that they're seriously incompetent.  The first (common sense!!) rule of data recovery is to STOP doing any writes whatsoever to the damaged/dying disk, and get a copy/image of the disk as soon as you possibly can. I would try to get the disk (edit: or an image copy of it on an external USB disk) back from whoever's got it so you can asses some of these things yourself.  If someone indeed installed Windows on it then they should be held accountable for that really, they should not be providing data recovery services if they're stupid enough to do that IMHO.

Edit: Anyway, if they installed Windows, that would explain why your fileysystem apparently has damange/your document wasn't found (has become "corrupted") - it's probable that a full windows installation would've overwritten a substantial amount of information, which probably included a lot of the filesystem structural information and possibly your data files. :-(

As an aside, I frequently use TRK when doing data recovery, it's a useful tool to have in your toolbox.  The TRK site also has lots of extra information on data recovery and various scenarios, so for your added elucidation I thought I'd just mention this.  See e.g. [TRK here]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") and for example [this relevant documentation]("http://trinityhome.org/Home/index.php?wpid=59&front_id=12") (the heat comments obviously don't apply here).

---

### Post by ByteJuggler on 2008-01-08
> **kleo skywalker said:**
> That would make sense if I was any good at it.

I understand your dilemma.  We can try and help you (Edit: to do some investigations yourself), but I agree it would be better to find a competent professional that actually deals with this on a day to day basis, which is what you've tried already.  A difficult situation.  

Even so, at the very least I would enquire whether it would be possible to have a straight binary disk image of the dying disk (make e.g. with dd or ddrescue) so you can do your own investigation even while the recovery people have the disk.   IF the drive is in a state where it's picked up by the BIOS and basically functioning, making an image to another disk, either as a partition or as a file is pretty easy using most of the recovery CD's.  But if the people dealing with your disk is not Linux aware/savvy they may not know this.  If so I'd actually consider trying to see if you can find someone else who knows what "dd", "ddrescue" and disk images are to have a look at the disk.

---

### Post by kleo skywalker on 2008-01-08
ByteJuggler, thank you very very much for that information. Now that I know what kind of things to ask them, I'm going to call them right away.
I hope they didn't do the Windows thing, because that would be really idiotic. I checked their website before giving them the go-ahead about my disk, and there they said that they handled Linux including Ubuntu. I also told them that my disk had Ubuntu, so I really checked as far as I could :(
Thanks again, and I'll post what they tell me.

---

### Post by kleo skywalker on 2008-01-08
Didn't realize the time, they seem to be closed for the day. I guess I can only find the answers to those questions tomorrow.
In the meantime, I have a strange question: if they really made the idiotic blunder of installing Windows, is it possible that they might have accidentally retrieved data from a previous Windows install on that disk? Or is this thought just proof of my ignorance? (I'm asking because my brother says that 99% of the mp3 files he acquired after we got Ubuntu are missing from that long list of mp3's.)

---

### Post by ByteJuggler on 2008-01-08
> **kleo skywalker said:**
> Didn't realize the time, they seem to be closed for the day. I guess I can only find the answers to those questions tomorrow.
In the meantime, I have a strange question: if they really made the idiotic blunder of installing Windows, is it possible that they might have accidentally retrieved data from a previous Windows install on that disk? Or is this thought just proof of my ignorance? (I'm asking because my brother says that 99% of the mp3 files he acquired after we got Ubuntu are missing from that long list of mp3's.)

Hey Skywalker,

No that's a good question, glad you asked it.  I was (probably wrongly in retrospect) assuming you only ever had Linux on that drive (e.g. from new.)  If it had Windows on before (e.g. you got it second hand or if you had Windows on there yourself originally) then it is quite possible (and even probable) that a filesystem recovery may still retrieve parts of that old filesystem, especially if your Linux didn't fill it up nearly as much as the original filesystem did.  That then could possibly also explain the presence of those Windows folders in the list they recovered.

Good luck anyway... :(

---

### Post by kleo skywalker on 2008-01-09
My data has finally been recovered - the data recovery people said that platter was scratched so some data was lost. So a  bunch of video files are missing but the ones from trips and special events weren't recent, so I probably have them on a CD somewhere. There were 2-3 movies, but I don't care about those so all is good.
Its been a longish thread so I'm clubbing all the thanks in this post. Thank you everyone for posting with all your advice and suggestions, I'm wiser from it. Your posts kept me informed throughout this mess and reduced the extra panic that would've been caused if I was completely clueless!
Many thanks!

---

