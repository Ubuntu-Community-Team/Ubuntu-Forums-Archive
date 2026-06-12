---
title: "Beginner-friendly backup/restore for Feisty dual-boot?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-09-06
The immediate question is whether there is a simple, straightforward, "do this and this only" series of *steps* that a relative newbie can take to backup and then restore a Feisty / 7.04 partition on a dual-boot W2K / Linux hard disk.

I ask because two days ago, after a bit less than six months of running Dapper (6.06),  I upgraded to Feisty.  Now, Norton Ghost no longer restores the new Linux-Feisty *root* partition (although the boot / Grub partition _seems_ to work -- more on this later).

My attempts to then use existing Ubuntu Forum threads to answer my question has further  confused and discouraged me.

[B]_RESOURCES I HAVE -_
[/B]I have the following tools available to me:[LIST]
[*]Feisty / 7.04 CD-ROM.
[*]Two identical 80GB dual-boot drives in swappable trays; at present only one drive can be running in the computer at one time and I prefer to leave it that way if at all possible.[LIST]
[*]One of the drives -- the "source" drive -- contains a completely functional W2K / Feisty dual-boot system.
[*]One of the drives -- the "destination" drive -- can boot only into W2K; the Feisty root(?) partition is unusable after a Norton Ghost restore.[/LIST] 
[*]Norton Ghost 2003, and Ghost images of **(a)** readily restorable W2K / Dapper drive, **(b)** not wholly restorable  W2K / Feisty drive , **(c)** Dapper partition, **(d)** Feisty partition.
[*]External 180GB USB2 Hard disk, currently with an NTFS partition for use by Ghost and a FAT32 partition to permit the "drop box" exchange of files between the Windows and Linux partitions.
[*]Internal CD-RW burner.[/LIST][U][B]THE IMMEDIATE PROBLEM -
[/B][/U]With Dapper, I was able to use Ghost to image and restore my dual-boot W2K / Linux drive and readily boot into either operating system.

Now, with Feisty, after restoring the W2k / Feisty image, the root partition is unusable.  More specifically, the following occur:[LIST]
[*]I start the computer and receive my GRUB "choose o.s." display.  That is to say that the restored boot / GRUB partition appears readable and usable.
[*]The computer begins booting Ubuntu by displaying the Ubuntu Feisty graphic logotype with moving progress bar.
[*]After a few seconds, the boot process terminates and I receive a lengthy series of text-based error messages that say **(a)** the root (not boot) partition is broken, **(b)** that the root partition has been placed in read-only maintenance mode, and **(c)** that I need to run fsck in read-only mode without the "-a" and one other parameter.
[*]I run "fsck -y" to automatically respond to the *thousands* of yes/no prompts. fsck reports all kinds of missing nodes and weirdnesses.  At this point all is lost -- running fsck, at least in the uninformed "dumb" way I currently know how to run it, doesn't fix the problem but instead makes it worse.[/LIST]So the bottom line is that Ghost doesn't seem to work with Feisty as it did with Dapper, making it currently impossible for me to properly "clone" my Feisty partition.

[U][B]WHAT WON'T HELP -

[/B][/U][I]The Linux "Catch-22": One can experiment with a process only after one can first reliably produce a backup system to protect him or her against failed experiments.
[/I]
I've tried to research the problem, but literally all of the Ubuntu Forum threads that explain "how to" solve this problem **(a)** consist largely if not entirely of confusing caveats, ambiguously stated "ifs", and multi-participant arguments and counter-arguments for and against the suggested procedure, or **(b)** suggestions that are too terse or cryptic for a normal user / relative newbie to follow.  For example, one putative answer was of the form:

> All you need to do is boot to the Live CD (or alternate), mount the partition that you want to decompress your backup file onto, mount the external disk that contains your backup, and go to work like this.
That is to say that saying "all you need to do" is "mount this" and "mount that" omits essential intermediate steps. Note, too, that this somewhat cryptic suggestion engendered a wholly understandable follow-up question from another reader which in turn received the reply to "read the mount man page".  That's not really helpful -- mount, whether run from the rescue CD or not, is a complicated command; experimenting with it, guided only by too-often-impenetrable man pages, will most likely confuse rather than clarify and solve my immediate problem.

Similarly, I'm not at this point knowledgeable enough to guess which files I can safely exclude from a tar-based backup.

[U][B]The Bottom Line - 
[/B][/U]My Feisty upgrade and two days worth of downloads / updates / tweaks are about to become an exercise in wasted time and energy unless I can come up with a _sensible_, _straightforward_, step-based way to restore it from my working source drive to my backup / target drive.  Otherwise I'll be compelled to revert to Dapper which I'd prefer not to do...

So -- can anyone please -- PLEASE -- suggest a fairly specific, non-ambiguous procedure that I can perform to accomplish the formerly straightforward process of imaging and restoring a dual-boot Linux partition without first having to become an expert in the tar and mount utilities?

Cheers & sincere thanks for your help,
Ric
SFO

---

### Post by x64Jimbo on 2007-09-06
Mounting partitions from your livecd is not difficult at all. This is the way that pretty much all rescue operations are performed - even on crashed windows systems. 
the command to mount a drive is this:
sudo mount /dev/hda1 /media/hda1
this assumes that you have a mountpoint in /media named hda1
hda1 is the first partition on the hda device, which is the first IDE hard disk. hda2 is the second partition on that first disk. hdb is the second, and the number formats follow that. 
When users tell you to read the manpage on something, it's because the manpages have been written to help you, and there is no sense in repeating what has already been said elsewhere. Linux is a great operating system, but there is a learning curve, just like any other OS. If someone had never seen windows before but they were told to open the Display Properties or Control Panel, they would have no idea. The good thing about Linux is that it comes with plenty of documentation in the manpages, whereas Windows makes you have to pay for an IT support geek or a Dummies book.

---

### Post by Phrawm48 on 2007-09-06
Jimbo:

Thanks -- so the basic form of the mount command I'll need to run after booting up on the Live CD will be:

```
sudo mount /dev/[identifier] /media/[identifer]
```

Where [identifier] is a device reported by *df*(?) or the like  If yes, that seems straightforward and unambiguous enough, even for me...

Now I need to disambiguate the command or commands that I can use to back up then restore my boot and root partitions, ala an image-like backup / restore.

Cheers & sincere thanks,
Ric
SFO

---

### Post by x64Jimbo on 2007-09-06
You won't be using an imaging command if you have filesystem corruption. You'll just want to open up nautilus windows for the two locations (source and destination) then just click-n-drag just like you do in Windows.

---

### Post by Phrawm48 on 2007-09-07
*         You won't be using an imaging command if you have filesystem corruption.*

Well one assumption I've been making is that somewhere along the way I'll have to reformat the damaged EXT3 root partition.  Or something...

In the meantime, I'm still trying to learn some relatively straightforward, easily repeatable, task for backing the entire boot and root partitions -- i.e. the complete system -- up so I can "clone" the complete system to a backup.


Long story short, what my research has revealed so far is that backing up and restoring a Feisty system is a problem, or at least another "Linux moment", for several *users*.  Dual-boot Feisty systems are an especial problem insofar as the best, most easily used tool for cloning a backup -- Norton Ghost -- seems unable to handle Feisty's EXT3 file system...(?)

As for me, at this point I'd have to say at this point that my "upgrade" to Feisty has been a failure.  The best, most straightforward, easiest to perform "solution" to my Feisty  backup-restore problem seems to be to revert to Dapper.  What a mess!

Cheers, thanks for your help, & have a GREAT weekend,
Ric
SFO

------

EDIT:  After posting, I noticed the link on x64's contribution [Samba share problems? Fix them!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")   That link pointed to a Feisty Guide, which in turn contained this page:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Backup_Ubuntu_System](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Backup_Ubuntu_System)

So there does seem to be a tool for backing up.  Using my runnable Windows partition, I'll investigate this further...

---

### Post by Phrawm48 on 2007-09-09
Note -- I'm writing this under a "cloned" image of Feisty Linux.  Ta da!

The essential piece of information was that I imaged my Feisty boot and root partitions with Norton Ghost 2003 and the program's "-ial" command line switch.

The "-ial" switch is a variation of the "-ia" switch that performs sector-by-sector copying or a source partition; the "-ial" switch limits sector-by-sector copying to Linux partitions whereas the "-ia" switch does not.

Note, too, that the "-ial" switch (like the "-ia" switch) requires that the geometries of the source and destination partitions be identical!  So the "-ial" solution is perhaps not as complete as one might wish.

Finally, note that I've only done this once.  So I for one don't at this point imagine that I have uncovered The One True Solution to the problem.

Stated another way, I fully intend to keep researching alternatives such as those graciously offered in response to my original query on the subject.

Nevertheless, it does preliminarily appear that once can indeed use Norton Ghost 2003 in conjunction with the program's "-ial" switch to create Feisty EXT3 Ghost images that can be restored and run.  That's worth knowing, I think...

Cheers & hope this helps,
Ric
SFO

---

