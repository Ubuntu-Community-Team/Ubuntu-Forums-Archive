---
title: "trying to rescue Mac drive..."
date: 2012-03-16
forum: Apple Hardware Users
---

### Post by mzimmers on 2012-03-16
...I just pulled a failing drive out of an iMac. It doesn't mount in either Mac OS X or Windows 7, but it does in Ubuntu. Now, though, I need to access the files, and I'm getting ownership/privilege issues. When I try to chmod or chown, I get an error that the file system is read-only.

This mounted automatically; can someone tell me how to dismount and remount to get access to the data?

Thanks.

---

### Post by NoBugs! on 2012-03-16
If you run "sudo nautilus", it should let you copy the files to another drive. From there you should be able to chown them.

---

### Post by mzimmers on 2012-03-16
OK, I just ran that command, and got a couple of errors:

1. in the terminal, I got a message that Syncdaemon isn't running, and missing callback etc.

2. I got a pop-up saying that Nautilus could not create the required folder "/root/.config/nautilus"

Any ideas on this?

And, do I gather that I'll have to do the copy from the terminal? I can do that (if I can get the destination pathname right; It's just easier if done drag-and-drop.

Thank you for your help.

---

### Post by winh8r on 2012-03-16
Launch nautilus by using 

```
gksudo nautilus
```

Nautilus will allow you to move the files by drag and drop.

---

### Post by mzimmers on 2012-03-16
Thank you. That looks more promising.

Now...I have a lot of stuff on this drive, and my ubuntu system currently has a pretty small SSD. What would be *really* slick (and I know this is probably asking for a lot) is if I could transfer all the files on the drive to a shared drive on my Mac. 

I'm trying this right now, and it's still giving me some error messages about files that can't copy because of permissions. There are 34GB in her folder, and it says it's copying 4.3 GB (I did a "skip all"). So, assuming some of the stuff doesn't copy over, what can I do with permissions/ownership/whatever to get the rest? Would I use the properties to change the permissions?

Thanks so much...this looked hopeless a few hours ago, but now we have a fighting chance to get her data back. (And trust me, we'll be doing backups from now on.)

---

### Post by mzimmers on 2012-03-16
Actually, I think I have a better idea -- I can mount the failing drive inside my ubuntu box, along with a new disk I got today (intended for backups for the sick Mac). I can do an internal copy, then pull the disk out and connect it to the Mac for copying.

I still will have to get around this issue of permissions, though. How do I go about setting the permissions for an entire volume (or at least, everything on it)?

Thanks a lot for the help. I'm sure I seem a bit scattered, but it's been one of those days.

---

### Post by MisterGaribaldi on 2012-03-16
EDIT: Der... never mind. Just re-read your post and saw you were going to do what I suggested.

That's what I get for skimming!

Sorry!

---

### Post by mzimmers on 2012-03-16
I got two new drives today. One is in the sick Mac, and is its new system disk. The other, I'm going to put in the ubuntu box, along with the sick drive, and do a disk-to-disk copy. (Somehow, the sick drive seems OK when mounted to ubuntu.)

Then, the plan is to remove the drive I just bought (actually, I'll probably remove both of them), and connect the new drive to the sick Mac. Mac has a utility called Migration Assistant, which should help me get all the (non system) stuff from newDrive2 onto newDrive1.

*Then,* I erase newDrive2, reformat it and begin running Time Machine on it.

Any gotchas that you can see? I'm pretty sure I don't have any super-huge files.

The only thing I need to understand to make this happen, is how to chown/chmod the *entire* sick drive, so that access control doesn't thwart my plan.

Thanks.

---

### Post by MisterGaribaldi on 2012-03-16
If you format the new HDD as FAT32, you shouldn't have to worry about permissions, coming out the other end of the copy process.

In any event, if at all possible, I'd recommend not messing with the files on the bad HDD. Just copy them, lest you risk corruption due to changes and the bad state of that drive to begin with.

Good luck!

---

### Post by mzimmers on 2012-03-16
Well, I should have known that my last idea was too optimistic to work. The system reported "imminent" device failure. So, I left newDisk2 in the box, and am again connecting sickDisk via USB (that's how I saw it last time.)

So...what's the command/app for "seeing" these devices? There's a device manager somewhere, right? I'm going to make a last-ditch effort to pull some stuff off of sickDisk here.

I'll return my attention to permissions once I see the devices in ubuntu again.

EDIT: OK, I ran nautilus again, and now I see sickDisk. I still don't see newDisk2, though. What am I doing wrong?

BTW: I still can't change permissions on files using nautilus and going to their properties. Or at least, my attempts are failing. I keep getting messages about a read-only file system.

---

### Post by mzimmers on 2012-03-16
I removed newDisk2 from the ubuntu box, formatted it on the Mac, and returned it to the ubuntu box. I now see it.

BUT:

It -- like sickDisk -- is READ-ONLY.

Someone please tell me...WHAT do I have to do to make these volumes accessible? I feel I'm very close to a solution, but I'm also on borrowed time with sickDisk. Any timely suggestions would be much appreciated.

Thanks...

---

### Post by MisterGaribaldi on 2012-03-16
Dunno exactly what you're doing, but here is what I would recommend if you're going to do this on the Mac side:

Disk Utility -> Left Pane -> click on the device listing for the new HDD;

then

Partition tab -> click the pop-up above the partition table and choose "1 Partition"

then

Click the "Custom" button below, and change the partition table to MBR;

then

Change the partition type to MS-DOS;

At this point, format the drive, unmount it and then unplug it, and then try attaching it to your Ubuntu box.

---

### Post by mzimmers on 2012-03-16
Thanks for the suggestion. I tried it, and now, newDisk2 doesn't show up in ubuntu. Any other formatting/partitioning ideas?

EDIT: I don't know whether this matters, but when I start nautilus, I get a buch of Gtk-WARNING messages: Unable to locate theme engine in module_path: "pixmap",

---

### Post by MisterGaribaldi on 2012-03-16
> **mzimmers said:**
> Thanks for the suggestion. I tried it, and now, newDisk2 doesn't show up in ubuntu. Any other formatting/partitioning ideas?

EDIT: I don't know whether this matters, but when I start nautilus, I get a buch of Gtk-WARNING messages: Unable to locate theme engine in module_path: "pixmap",

Huh. How are you attaching this drive to your Mac, and how are you attaching it to your PC?

---

### Post by mzimmers on 2012-03-16
I assume you're talking about newDisk2. On the Mac, I put into an enclosure that connects via USB 2.0. On ubuntu, I put it inside the case, connecting it via SATA.

I *did* see newDisk2 when I formatted it conventionally on the Mac, but...that was read-only on Ubuntu.

EDIT: can't I somehow initialize it on ubuntu? Again, I'm not intending to boot from it on the Mac; I just want to copy files.

---

### Post by MisterGaribaldi on 2012-03-16
Well yeah, absolutely you should be able to. At this point, though, I'm left wondering why it would make a difference, but sure... *any* port in a storm.

---

### Post by mzimmers on 2012-03-17
OK, so...can you tell me how I do that, please? How to format a drive on ubuntu that I don't see?

---

### Post by MisterGaribaldi on 2012-03-17
Well, it would be nice to know why your PC seems to not want to work with this drive.

An off-handed guess is that either how you have Ubuntu set up is interfering, or you have some kind of physical problem with that computer. Loose cabling? Failing SATA controller? Lack of support for a hard drive of this size? Something else?

You could try putting it back in the enclosure and attaching it to your PC by USB. If that works, then it would seem to suggest an internal physical problem with your PC. If it doesn't, well... let's just take this one step at a time for the moment, shall we?

---

### Post by mzimmers on 2012-03-17
I guess what I was asking was, can we pretend that newDisk2 is brand-new, unformatted, etc. and do whatever someone would do to initialize a drive on ubuntu?

I'm assuming there's some ubuntu utility that finds and initializes hard drives, like Disk Utility on the Macintosh.

---

### Post by MisterGaribaldi on 2012-03-17
Yep. Install GParted. Easy to use and works well.

---

### Post by MisterGaribaldi on 2012-03-17
... *so* ... ?

:)

---

### Post by mzimmers on 2012-03-17
Been trying lots of things...still no luck. A couple of issues:

1. gparted has a rescue data feature, but it says something called "gpart" must be installed. I can't find that through the USC. (maybe it doesn't matter).

2. gparted won't allow me to format hfs+...the option is ghosted out. Can anything be done about this?

EDIT: I partitioned newDisk2 on a Mac, and installed it in ubuntu. I'm currently trying to copy from sickDisk to newDisk2 for the purpose of using newDisk2 for Migration Assistant. The copy is going slow (and it's telling me it's taking longer and longer) so I'm not optimistic. If this fails, I'm just going to grab individual folders from sickDisk and drag them onto newDisk2. I'll get as much as I can, move it over to the Mac, and that'll be the end of it.

---

### Post by MisterGaribaldi on 2012-03-17
> **mzimmers said:**
> Been trying lots of things...still no luck. A couple of issues:

1. gparted has a rescue data feature, but it says something called "gpart" must be installed. I can't find that through the USC. (maybe it doesn't matter).

2. gparted won't allow me to format hfs+...the option is ghosted out. Can anything be done about this?

EDIT: I partitioned newDisk2 on a Mac, and installed it in ubuntu. I'm currently trying to copy from sickDisk to newDisk2 for the purpose of using newDisk2 for Migration Assistant. The copy is going slow (and it's telling me it's taking longer and longer) so I'm not optimistic. If this fails, I'm just going to grab individual folders from sickDisk and drag them onto newDisk2. I'll get as much as I can, move it over to the Mac, and that'll be the end of it.

In reverse order...

If it's going slower-and-slower, that in this case probably is a symptom of a bad HDD.

GParted requires all related components plus all necessary HFS components to fully do what you're talking about. That being said, it sounds like it is "working" after a fashion, and that's good. It may be the best shot you'll get.

And last/firstly... when you are talking about setting up a fairly mainstream partition table setup (which MBR definitely is) and using a relatively mainstream partition format (which FAT32 also is) then it doesn't matter where you've set the thing up; it should just work anywhere.

The reason I had you set up MBR as well as a FAT32 partition is I didn't want to have to fool around on your Linux box having you set up a whole bunch of extra crap for an essentially one-shot use. Unless you had individual files which were >4GB, there's no counterindication in this situation for going with MBR/FAT32, since by definition it's fully supported on every platform you're going to let touch it (Linux and Mac OS X, but obviously Windows too).

First rule of being a computer tech: Don't make your life any more complicated than it has to be.

---

### Post by mzimmers on 2012-03-18
Thanks, MG. It was a good learning experience. I've gotten the files to the Mac, so ubuntu was a hero here. I've still got some technical issues on the Mac, but...those are for another forum.

I appreciate all the help, everyone.

---

