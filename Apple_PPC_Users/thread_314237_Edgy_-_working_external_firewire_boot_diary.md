---
title: "Edgy - working external firewire boot diary"
date: 2006-12-07
forum: Apple PPC Users
---

### Post by stream303 on 2006-12-07
I got my little external firewire 400 hard drive to boot properly with Edgy!

(Update Feb 2008:  if you are just trying to boot/install from an external cd firewire drive, see here: [http://ubuntuforums.org/showthread.php?t=698290](http://ubuntuforums.org/showthread.php?t=698290))


My setup:  I have a working Edgy Ubuntu installation from the live-cd with firewire support dedicated to my G5 iMac's internal hard drive.  Works great once some of the usual stuff was taken care of, like fans, resolution, etc.  (see other threads for screaming fans etc)  

My firewire drive:  I chickened out and got a small firewire drive from Apple, the G-tech "G-drive".  40gb.  already formatted and partitioned for OSX usage.  I put OSX on it just to check it out, and it works.  Snooze.  OSX is going away shortly. (note - nice little drive so far!)

My partitioning scheme - guided partitioning where you use the whole disk.  Nothing fancy needed for me, so I let Edgy do it's thing with guided partitioning on /dev/sdb.  In both cases you get the apple boot partition in 2, and linux native and swap in 3 and 4 automatically.  No manual partitioning, I prefer the kiss concept. :)

What didn't work:  Installing the "alternate" text-based edgy went ok onto the firewire drive (had to disconnect mouse and not autodetect keyboard during install), but like everyone else, it wouldn't boot afterwards.  The install warned me by complaining that it couldn't complete the yaboot blessing sequence so I just finished up the install anyway.

**What I had to do:**

Boot the live-cd, (or alternate cd in rescue mode) and let Ubuntu detect the external firewire drive.  This enables you to run a find command to determine the ofboot and device path of the firewire drive.

In a terminal, I ran:

```
find /proc/device-tree -name 'sbp-2@*'
```
(single apostraphe's, not backticks `)

This was the result:
**/proc/device-tree/ht@0,f2000000/pci@3/firewire@e/node@0001d202e0a60004/sbp-2@c000**

Went into the **/media/disk/etc** directory on the firewire drive and edited the yaboot.conf that the new install put there.  I added **ofboot** and **device** lines which were essentially the same.  I got most of the info from the previous find command. Note that I used only about half of the info from the resulting line and added a bit at the end in the two lines below. Here's a snippet of my firewire's yaboot.conf file with **my edits in bold:**

(I'm running Ubuntu on the internal drive as well, so some of you may have to change your boot and root lines to /dev/sda2 and /dev/sda3 if you have internal drives that are hdx drives.)

*<snip>*
**boot=/dev/sdb2**
partition=3
[B]ofboot=fw/node@0001d202e0a60004/sbp-2@c000/disk@0:
device=fw/node@0001d202e0a60004/sbp-2@c000/disk@0:[/B]
**root=/dev/sdb3**
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
*<snip>*

Basically, for the ofboot and device lines I used everything after the *node,* and added **/disk@0:** to the end.  (Don't forget the trailing colon)

**Still not done.**  

```
sudo mkofboot -v -C /media/disk/etc/yaboot.conf

sudo ybin -v -C /media/disk/etc/yaboot.conf
```

Be sure to check your /media/disk/etc/fstab file to make sure it is pointing to the right drive for boot as well.

Reboot.

If the firewire drive is on, and I boot while holding down the Option or Alt key, I can choose either one to boot from.  Just be patient and wait for the wristwatch-icon to turn back into a mouse pointer and click on the right-arrow icon.

Right now I have a very custom Edgy on the internal drive, and a standard Alternative-install on the firewire. I'm set for experimenting with other distros like Feisty on the firewire, etc without risking my working internal setup.

Again, thanks to all the forum members who provided all this info in the first place.  PPC'ers - never say never. :)

---

### Post by stream303 on 2006-12-08
Update: Although I was very careful about ejecting the drive, not shutting down power etc, for some reason my root partition /dev/sdb3 on the firewire got corrupted.  No amount of fsck'ing would resurrect it.

I have reinstalled Ubuntu on the firewire drive with the alternate-cd, but this time I used ext2 instead of the default ext3 for /dev/sdb3.  (I just used guided partitioning, and then backed up one screen to change the format to ext2 and continued on...)

It doesn't seem to make sense going from a journaled to a non-journaled format for a boot drive, but we'll see if any corruption occurs after a few days.

Fortunately, I didn't have to play around with mkofboot or ybin - the drive stayed blessed from my first install so the reinstall was easy.

I'll keep everyone posted on how well the ext2 format does.

---

### Post by stream303 on 2006-12-18
I'm back to using ext3.  It must have been a single event since ext3 is now working fine.  Hmmmm

---

### Post by stream303 on 2008-02-18
> **stream303 said:**
> **Still not done.**  To make this fresh edit of the firewire's yaboot.conf work, I had to:

WHAT A MESS! :)

Why not just do this after editing the yaboot.conf file on the firewire drive:

```
sudo mkofboot -v -C /media/disk/etc/yaboot.conf

sudo ybin -v -C /media/disk/etc/yaboot.conf
```

I crack myself up. :)

---

### Post by joshtheiss@gmail.com on 2008-03-04
Greetings,

I am extremely new to linux (ie, discovered it a few days ago, tried the live cd, and would like to do a trial install), but i am running an ibook G4 and would rather not touch the internal drive.  I DO, however, have an external firewire drive, and am quite interested to install to that.  I, like you, had issues with the "blessing process" (as you call it) of yaboot, and was following your instructions to fix it.  

However, since i don't have an internal ubuntu loaded, i used the live cd to make the changes you called for.  I got to the point of saving the changes to yaboot.conf, and it wouldn't let me, as apparently it was write protected?  I tried changing the write permissions on the file, but didn't have sufficient privileges to do so.  Is there a way around this, or am i doing something wrong?  Here's the information I can think of listing, but if you'd need more, i'd be happy to provide it:

internal-> OS X 10.4.11
external firewire-> Ubuntu 6.10 PPC

Thanks in advance,

josh

---

### Post by stream303 on 2008-03-04
No need to change the permissions on the file - that's an OSX trick to be avoided. :)

You need to be root, either directly or prefixing your commands with sudo.

What I'd do is boot the live-cd in rescue mode (aka single-user mode).

I'm pretty sure that if you just

```
cd /etc
```

you'll be able to see yaboot.conf.  If not, you may have to 
```

cd /media/disk/etc
```

see if it is there:

```
ls yaboot.conf
```

While we're here, you can run the 

```
find /proc/device-tree -name 'sbp-2@*'
```

command to find the relevant part that needs to go into your yaboot.conf to later issue the *ofboot* and *ybin* commands.

After rebooting, hold down the Option or Alt key and choose the firewire drive.

If we still are in a bind (I've never done it with an internal OSX partition), we might have to change the drives from sdb to sda in yaboot.conf and start again.

Happy to help get this up and running!

---

### Post by stream303 on 2008-03-04
Now that I think about it, you probably don't need to unmount the firewire drive, so try it without unmounting it.

I think that was part of my half-brained "just copy it over" technique until I found the -C option of mkofboot and ybin. :)

---

### Post by joshtheiss on 2008-03-04
Holy Penguin Pee, Batman!!

Ok, so the good news is, my external firewire drive is just drenched in holy penguin pee... (and that's the GOOD news?)

I followed your directions for using the sudo command, and then used your two line technique for gaining favour from the penguin gods.

I restarted, held down alt, and was quite thrilled to see OS X, as well as "Y" (yaboot?).  I selected Y, and sure enough, it was yaboot loader.  I hit "l" for linux....... but it just kicked me back to the previous screen, with my option of OS X or yaboot.  I tried going into to OS X, but it didn't seem to like that, so i restarted, and booted straight into OS X without problems.

You mentioned changing things from sdb to sda as a solution.  Care to elaborate?  (also, keep in mind the last time i used CLI was DOS 6.0, so "simple" things may not be so simple for me :)

Anyhow, i thank you so much for your help thus far, and eagerly await your response.

---

### Post by stream303 on 2008-03-04
We're very close.  Using the live-cd should make it easier, just boot it and use it normally.

To edit the /etc/yaboot.conf file, just type this in a terminal to bring up the editor with root priveleges temporarily:

```
gksudo gedit /etc/yaboot.conf
```

Here is what part of my firewire yaboot.conf looks like with my edits.  I #commented out the lines that needed fixing on my system.  My own additions are in bold.

```

#boot=/dev/sda2
**boot=/dev/sdb2**
#device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
[B]ofboot=fw/node@0001d202e0a60004/sbp-2@c000/disk@0:
device=fw/node@0001d202e0a60004/sbp-2@c000/disk@0:[/B]
partition=3
#root=/dev/sda3
**root=/dev/sdb3**
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
```

The original device yaboot found was my internal drive, sda, and used that when it was confused about the firewire.  I commented out that original device line, added my own custom ofboot and device line,  and had to manually change the boot and root partitions to sdb2 and sdb3.  

Your ofboot and device lines will look a little different than mine.

now with yaboot.conf edited from the live-cd,  you can

```
sudo mkofboot -v -C /etc/yaboot.conf
and
sudo ybin -v -C /etc/yaboot.conf
```

Let's see if this helps..

---

### Post by joshtheiss on 2008-03-04
Victory! (mostly)

Ok, so i went to change the things you said to change, and noticed that i had an extra "device=" just hanging out... well, i deleted that, and changed what you suggested, and went to run the next scripts and it wouldn't go... said it couldn't find sdb2... so i changed them back to sda's, and tried again... now i get two yaboots at startup (?), so i selected the first, and hit "l" for linux... it gave me a CLI interface... i typed "Linux" and it booted right up.  

So... yes, it's a bit awkward to start up, but yes, it works!  Definitely not perfect, but certainly good enough to try out for awhile and see if i like it well enough make the switch...

Thanks again!  You've been most helpful!

---

### Post by stream303 on 2008-03-04
Allright!!

When you get a chance, could you post your yaboot.conf here so we can take a gander and see if we can clean that up?

I also edited my original post to save someone else a big headache from copying, unmounting, etc.  It was a real mess.

---

### Post by joshtheiss on 2008-03-04
Ok, i hope this is all the info you're looking for.


```
boot=/dev/sda2
ofboot=fw/node@0050770e400009c8/sbp-2@4000/disk@0:
device=fw/node@0050770e400009c8/sbp-2@4000/disk@0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

---

### Post by stream303 on 2008-03-04
Looks good!

Be sure to make a copy of this golden file, ie

```
sudo cp /etc/yaboot.conf  /etc/yaboot.conf.firewire
```

Trust me - print this puppy. :)

Any time I change anything in yaboot.conf, I always follow up with the mkofboot and ybin commandline sequence.

I'm not using OSX anymore, but there is a line you can add to yaboot.conf to be able to boot OSX as well.  I'm sure I've seen it here in the ppc forums.

Thing is, I'm not a firewire guru, this is just what I found to get my drive working - hopefully someone can point out anything that is redundant, or questionable.

On my system when I use the Option / Alt key on boot, I always see TWO firewire icons, rather than one, so that has me puzzled, but I just boot away. :)

I'm glad it's up and running, and this yaboot.conf should work on your system for any distro that uses yaboot.  The only thing that might change is your root and boot lines if you change partitioning schemes in the future instead of letting guided partitioning use the whole disk, do dual/triple boots, etc.

Have fun!

---

### Post by joshtheiss on 2008-03-05
Update:  So, apparently I don't have to do anything at all if my firewire drive is plugged in.  If it's plugged in and on, it loads straight to Ubuntu.  If it's unplugged, for a split second there's a little file symbol w/ a "?" on it, but then it loads straight into OS X.  

Also, do you have any wisdom to dispense about getting my airport card to work?  I've checked around the forums, and apparently i need to somehow utilize some firmware, but there don't seem to be working links or something?  Maybe i'm missing something?

---

### Post by stream303 on 2008-03-05
That's how mine works too - although it boots to an internal Ubuntu.  I love my external firewire drive and use it for testing out all sorts of stuff - I just keep my yaboot.conf handy. :)

I can't help you with wireless since I'm still in the stone-age, but glad you brought that up.  On my iBook, Ubuntu was running sluggishly and it turns out that NetworkManager was eating all my resources.

After an install, I like to run top in a terminal, and saw that Network Manager was using nearly 100% of my cpu.  If your ibook is suffering from the same, you can *disable* NetworkManager (don't just remove it) like so:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

and then just restart your wired connection.

Problem is, with your need to go wireless, this will limit you to finding another network manager.  Hopefully you don't have this problem.

The other recommendation I have is that unless you need forensic security, I like to save some wear and tear on hard drives by adding noatime to my /etc/fstab :

[http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime](http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime)

I'm so glad to see that this technique got someone else's firewire drive booting and running.

---

### Post by joshtheiss on 2008-03-05
Well, i don't NEED wireless, but as a perspective trial to use only Ubuntu some day in the future, it's something on my list of things to figure out.  If i'm already tethered to my external firewire to load linux, then i guess i can be tethered to my ethernet as well.

The booting, however, works great.  Even though the the self-loading external Ubuntu seems clumsy (it boots straight to yaboot... waits for a second... boots to a CLI... waits a second... then boots Ubuntu), but it'll do everything fairly quickly without me touching it, so i certainly have no cause for complaint!

I might try to partition part of the external (i let ubuntu have the whole thing) and set up a common drive to swap files between OS X and Ubuntu.  I should be able to do that with the install disk, eh?  I know fat32 works with everything... is there another file system that you know of, or would recommend above that?

---

### Post by stream303 on 2008-03-06
I've seen some thread about allowing systems to see each other's hfs+ and ext3 partitions, but I don't have any real info at hand.

I'm sure you could resize the existing partition, and make a new one with something like vfat32.  I'm not sure if "gparted" is on the live cd, that would make things convenient as a visual partition manager...

Or worst case now that you have a golden yaboot.conf file, and know how to bring it to life, you could reinstall and opt for manual partitioning...

Wireless is great if you can get it to work. Sometimes it works right out of the box, or like our firewire boot project, it can take a little work, so don't get too frustrated.

Wish I knew more, but I just am too lazy since my cat-5 ethernet is doing fine :)

---

### Post by joshtheiss on 2008-03-06
Since you seem interested in finding solutions and becoming more knowledgeable, so i'll briefly tell you what i ended up doing:

So, i used the Alternate CD to resize the partition that i had Ubuntu on (ie, "reinstall" until it loaded the partitioner, then did my thing and exited out) down to about 15G, left 20G free after the 15G partition (because maybe i'll want more space for Ubuntu, or maybe i'll end up setting up Ubuntu as a trial for somebody's PC), and set the rest to be my "universal" drive.

In the end of it all, i couldn't make OS X like whatever version of VFAT that Ubuntu was trying to use... So i formatted it as an ext2, and went on the search to make OS X read it.  Now, wouldn't you know it, THAT was an easy fix!  As it turns out, sourceforge makes something called Ext2 Filesystem (v. 1.4d1) and allows OS X to manually mount an ext filesystem, and read/write to it!  Just make sure to grab 1.4d1 instead of 1.3, as it grants OS X.4 usability.  

All in all, i was pleased with the process as a whole, but was surprised that Ubuntu was able to resize the partition while leaving the OS intact!  I mean, if it says it can, it likely can, but I guess i'm oldschool enough to think that resize=format.  Now i can share various files to easily test for compatibility, while also being able to let Ubuntu see my music collection (which makes life just grand, if you ask me)!

---

### Post by stream303 on 2008-03-06
That's great!

What a cool tip.  I'm going to download that utility, but pick up the 1.4d4 version, which is neat because it seems to have gone "universal" so even the Intel-Mac guys can use it:

[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)

I know it's a little late in the game, but with an external firewire drive there is a way to avoid all this yaboot pain - install OSX onto the firewire drive, and install Ubuntu onto your internal drive - if you've got the OSX firewire attached and running when you install Ubuntu onto the internal drive, the yaboot.conf menu should be perfect.  For me, I've got one of my smaller firewire drives sitting in a drawer with OSX on it, and I'll boot it if there are any Apple firmware updates.

Looks like you are all set for doing all sorts of customized setups.  You could manually partition that firewire drive for all sorts of things now, multiple ppc distributions, etc to pick from at boot time.

Since you are on a G4, you may find

**yabootconfig**

a very handy utility to run to help write those pesky yaboot.conf files.  This utility doesn't work for me with a G5, so I have to do it manually.

Thanks for the ext2 tip!

---

### Post by stream303 on 2008-03-11
Wow, thanks to the **Gentoo** forums, they tipped me off to the fact that **my fstab might be wrong on the firewire drive too.**

And it was!

I'm running Ubuntu on the internal drive, and a variety of other ppc distros on the external firewire.  I go through all the manual yaboot.conf editing, finding my device lines, etc and discover that my /etc/fstab on the firewire drive is still pointing to the partitions on my internal drive.

I'm amazed that it booted (although both drives use the same partitioning scheme and are sd devices), and I just changed any references in fstab from sda to sdb.

Somehow I think I found my random file corruption problem. :)

Moral:  When you manually do a yaboot.conf edit, also check your /etc/fstab !

Thanks to Gentoo PPC for the big tip! - since my system never failed outright, I never would have thought to look here.

---

### Post by joshtheiss on 2008-03-17
Sorry for no reply in awhile... i've been away.

Anyhow, my external firewire ubuntu ended up corrupting as well, but i checked the fstab file and didn't see anything that looked like it needed changing?  Perhaps my own newbness aided the corruption.  Regardless, i started over with 7.04 and everything seems to be working just great (except for my wireless, which i've made progress with, but still am generally unsuccessful.  oh well)

On another note, that ext2FSmanager thing is kinda quirky.  It worked great the first time, but i can't seem to make it work again.  After a bit of researching, i found out that ubuntu can read/write to HFS+ (unjournaled) with a small bit of tweaking (basically using ubuntu terminal to take ownership of the partition for permission to write/modify).  I know it doesn't directly matter to you either way, but i figured you'd like to be "in the know" on behalf of your mac buddies.  

Thanks once again for all your help in getting ubuntu loaded up for me.  The second time around was SO much quicker and easier than the first, and went without issues at all!

---

### Post by stream303 on 2008-03-17
Nice!

I take it you are manually changing the default filesystem from ext3 to ext2 during install to cope with that utility, or are you still using ext3 default?

Yep - ext2 is a little less forgiving without the journaling of ext3..

---

### Post by joshtheiss on 2008-03-17
My current config on the Firewire drive is a 15G partition of ext3 as my Ubuntu partition, and 100G HFS+ partition to basically hold files (music, videos, etc) and to transfer between the OS's.  I *was* manually changing the 100G partition to ext2 in order to use the ext2FSmanager utility, but the utility was getting quirky or something, as i could mount the partition in OS X, but not write/modify it.  Decided HFS+ was an easier alternative (once i found out that HFS+ = Mac OS Extended) once i figured out Ubuntu could read/write to the unjournaled, case sensitive flavour.

**edit**
I upgraded to Gutsy, and now wireless is happy.  Most of my research on the topic dictates that WPA is sketchy, but WEP works well, but after fighting WEP for days, i swapped back to WPA and it worked the first time.  Go figure.  Regardless, i'm a happy camper right about now. :)

---

### Post by strayrooster on 2008-07-22
Hi,

I am planning on installing Ubuntu on my ext fw hd, and really hope your instructions work with Hardy!  I installed Gutsy with a triple boot on my gen 2 MBP a few months ago, but alas, the small hard disk (120) was incredibly limiting for 3 operating systems..... So hopefully the firewire install works!

I will post my results/issues here (if thats ok with you!)

Thanks!

update - so yeah, after some digging on Hardy, maybe I'll just stick with trying to install Gutsy... 
[http://ubuntuforums.org/showthread.php?t=768200](http://ubuntuforums.org/showthread.php?t=768200)

---

### Post by stream303 on 2008-07-22
No problem - hope it works out.

Nevermind the naysayers - it always happens that the latest release is the "worst ever". :)

Be sure to update as soon as you can.  Note that lockups and bugs in general get smoothed out over time, and I haven't experienced anything like that, other than some ppc-specific quirks.

The beauty about Linux is that you don't have to run Ubuntu if it won't work on your hardware immediately.  You can always use another distro like Debian, but like everything else, it may have "different" bugs. :)  Or you can wait a month or two and try again with updates.

Some bugs are upstream of all the distros, so you just gotta' put it on your machine and make your own evaluation.

---

