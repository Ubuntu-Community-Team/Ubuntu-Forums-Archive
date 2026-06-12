---
title: "Newbie All Over Again"
date: 2005-05-15
forum: Apple PPC Users
---

### Post by iJerome on 2005-05-15
I've been watching Linux for a while from a distance.  Like 'that sure sounds cool if I ever grow a brain big enough for it'.  Recently I read something about booting from a LiveCD and that it worked on a Mac.  I thought only YDL did that.  So I figured I'd give it a try, and wow, I was impressed!  Now I want to install it on my PowerBook.

But I'm a Mac guy.  Doesn't mean I'm an idiot, but I'm used to things being crazy easy.  When I went to install ubu, it started talking about partitions and what now.  I've never partioned my Mac drives ever, but I knew of the concept.

That's where I got stuck.  You know, what to do next.  Do I partition my Mac drive first?  Or do I let ubuntu create it's own partition.  Is this explained in detail somewhere?

I've already shown a few diehard Mac types and there were impressed.  

Thanks for any and all help y'all,

iJerome

---

### Post by arctic on 2005-05-15
hi there. :)

do you have only one hdd or do you have two? my mac has two drives, which made it easier to set up a dual-boot-system. i installed ubuntu on a spare 20gb hdb drive and yaboot made the rest for dual set up. but as you are still stuck at the partitioning of your hdd, the best thing would be to change the hdd partitions from within mac first, thus creating some free, (maybe) unformatted space and then do the rest of the partitioning (creating /, /swap and /home partitions) with the ubuntu installer.

---

### Post by iJerome on 2005-05-15
My Powerbook only has one drive.  I know DISC UTILITY on the Mac can create it's own partition.  But looking at the ubu installer I got the impression it could create it's own partition.  What I DON'T want to do is accidentally erase OS X to try this guy out.

 ;-)

---

### Post by shrimphead on 2005-05-15
Hi there! I did this recently on my iBook G4, the best approach that I found was to partition the MacHD first.  I used iPartition from a boot cd to resize the partitions on my 30Gb HDD partition non-destructively, squeezing my Mac OS X partition from 30Gb down to 15Gb and leaving 15Gb of blank space on my drive.
Then you can just boot from the Ubuntu CD and select the option in the auto partitioning section to "use available free space" (or something like that!).  

Think that should do it, it worked for me :)

---

### Post by chascon on 2005-05-17
[QUOTE=][/QUOTE]
 you should write a how to shrimphead.
Oh wait is ipartition a commercial program?  There is supposed to be a way to do it with the debian installer thru an altered version of parted, and posibly thru d-i.  I don't k now if ubuntu inherited this ability because everyone is silent.  If you don't care about OS X, or have backs ups of it, fiddling abround with ubuntu's version of d-i is a learning experience in itself and worth a few errors.  I think you have to choose manual configuration of partitions if memory serves, highlight and enter on the large HFS partition (OS X), and see if it'll let you change the size by punching in a new size, enter.

Now using parted, I assume involves jumping into a shell during the d-i process, and jumping back into the d-i process but at the right place, after partitioning I assume which isn't too hard.  I just don't know how to use parted. 

There is also a advanced mode of install that you can specify at the start of d-i.  But I wish someone made clear consise how tos on these matters.  I could figure these things out and post a wiki but I can't afford to mess around with 'system crucial' computers.  I gather it is up you new users who are best able take advantage of your new installs and write a wiki howTo on your experience.

---

### Post by Rxke on 2005-05-21
iPartition is commercial... $$$$ :(

The most foolproof/newbie way to install Ubuntu, I think is to back up your OSX stuff first, then partition your disk under OSX, without fiddling what kind of formatting, just choose the standard stuff (HFS+) and yes you`ll lose everything... You will have to re-install your OSX then from your backup...

and the 'trick' to make it super-easy/less confusing is to partition your disk in 2 partitions with a *different* size, so when you reach the weird mumbo-jumbo ;) under the Ubuntu-install process, you will see at a glance which partition you will write your Ubuntu stuff on, just by the size of it. 
So say as an example you partitionded 20/30Gb, with the 30Gb part for OSX, in the Ubuntu installler youll see a list of partitions, some small, some big, and one being bout 20GB. You choose to erase that one, and it should change to FREE SPACE, then you can choose that one to let the installer repartition that partition again for you automatically, and then it should subdivide it in 3 parts...
If you`re happy with what you see, go to the next step, if in doubt, don`t apply the changes. Nothing will be written on the disk yet, so you can stop the install, go back to OSX and ask for more info/look things up etc... If you go to the next step and *did* something wrong, the installer will tell you. As long as you leave that 30GB partition alone, you won`t be doing much damage anyway...

Oh BTW, if you have internet, keep it plugged in, it makes thing easier later. The installer configures your network etc.

---

### Post by chascon on 2005-06-26
> You can use GNU parted with the new HFS+ resize patch. Just download the patched tarball from the link for the patch, since I don't think this patch has already been included in the ebuild (ebuild has hfs resizing though).
Then boot from a CD (not sure, but current gentoo live cds might already include that patch) and get the patched version of parted.
Once in parted "resize" is the command you are looking for.
Code:
$ parted
[...]
resize PartitionNumber StartMB EndMB

e.g.
Code:
resize 10 100 2000

resizes partition No. 10 to start at 100 MB from beginning to disk and end at 2 GB.

Oh, and I can't guarantee that you won't screw up your MP3 collection... Always backup :!: - you know the drill. Which, on a sidenote, makes this whole partition resizing thing kind of unnecessary IMHO. Since you are backing up your files anyway, why not get nice and shiny newly formatted partitions? :wink:

Have fun,
Disk

[http://forums.gentoo.org/viewtopic.php?t=123556&highlight=parted](http://forums.gentoo.org/viewtopic.php?t=123556&highlight=parted)

> > Wow. I had never heard of iPartition until just now, nor was I aware of
> the patched version of parted on the Gentoo LiveCD. So at the MacWorld
> Expo, when Prosoft Engineering told me that their new product Drive Genius
> is the only program that resizes HFS+, I only told them about VolumeWorks.
> They still didn't believe me. I think I might go back there today and tell
> them about these other programs. So there are exactly four that will do
> this job:
> 1) VolumeWorks: <http://www.subrosasoft.com/thestore/product_info.php?products_id=431>
> 2) iPartition: <http://www.coriolis-systems.com/iPartition.html>
> 3) Drive Genius: <http://www.prosofteng.com/products/drive_genius_info.php>
> 4) Gentoo parted: <http://gentoo.osuosl.org/releases/ppc/2004.3/livecd/>
> 
[http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2005-January/017587.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2005-January/017587.html)

As I written elsewhere, debian's parted resizes HFS+, and possibly their d-i also.  Last I heard you stil had to disable HFS+'s journalling from within OS X first.

Check out parted's website and manual on how to use this.
[http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html)
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC1](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC1)

If ubuntu doesn't support this, try to download debian's buss card install (very small), and use that to shrink parttions.

Try an installer from:
[http://www.nl.debian.org/releases/sarge/debian-installer/](http://www.nl.debian.org/releases/sarge/debian-installer/)

---

### Post by chascon on 2005-06-28
"# Parted can only shrink hfs and hfs+ filesystems."
[http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html)

But I also read that each distro regularily usees their own patches so I would not doubt it if debian has patched it to enlarge  aswell, although there are not guarentees.

---

### Post by chascon on 2005-07-27
> Just disable the journal and use the faily-build debian-installer, and it
should work fine. Backup your data first, obviously.

Friendly,

Sven Luther
[http://lists.debian.org/debian-powerpc/2005/02/msg00568.html](http://lists.debian.org/debian-powerpc/2005/02/msg00568.html)

> This is Chris from Kearney - I came to the InstallFest and left somewhat 
empty handed.

Just thought I should share with all of you I managed to successfully 
resize my HFS+ partition using parted.  I first had to disable 
journalling on the drive by entering 'sudo diskutil disableJournal 
/dev/disk0s3' from the Mac OS X Terminal, then I booted my iBook using 
the Kubuntu 5.04 live cd to have access to the drive from Linux.  After 
that, it was a matter of googling to learn to use parted and all was 
well.  After I finished and saved changes, I re-enabled journalling by 
typing 'sudo diskutil enableJournal /dev/disk0s3' from the OS X 
Terminal.  I now have nearly 8 gigs of free space to use for Linux on my 
iBook G4!

Chris

[http://lists.olug.org/pipermail/olug/2005-July/016921.html](http://lists.olug.org/pipermail/olug/2005-July/016921.html)

---

### Post by imnes on 2005-08-17
Okay so I shrank my hfs+ partition to make room for Ubuntu.  Now I need to remove ubuntu and regrow that hfs+ partition to get my space back.  How can I do that?

Nick

---

