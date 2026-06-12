---
title: "install &amp;/or partition move/resize w/o optical drive but w/external hdd"
date: 2009-10-01
forum: Apple Hardware Users
---

### Post by mrelektron on 2009-10-01
Hi all,

I'm trying to install Ubuntu (9.04) on a powerpc mac laptop and set it up as a dual-boot.

I upgraded my internal hdd, divvied it up into hfs+ and ext3, put the old hdd in an enclosure, transferred the old hdd with Mac OS X onto the hfs+ partition (using SuperDuper!) on the new internal hdd, and it (OS X) works great. Unfortunately, I figured I'd put ubuntu on the ext3 partition, but could not figure out how to tell installer how to use it - so it ended up using some free space on the drive, like 2.5 Gigs (ouch!), NOT the 140 Gig partition I had in mind for it. Install works fine BTW but it's, ah, 95% full already, of course.

I am now having problems with optical drive (OD). OD seems dead (long story - old internal OD died; I replaced it; new OD worked fine this morning but now doesn't work, just makes a ton of noise - every CD I put in it was pristine and clean; go figure) I therefore can't do anything like run gparted from a liveCD or redo the install from a live CD or anything like that.

I do, however, have the old internal hdd now as an external firewire hdd.

I've tried to no avail to make a bootable USB flash drive from ISO9660 image.

Note that boot is bootstrapped from hfs bootstrap partition first (not the OS X hfs+ partition) and then to root (/) ext3 partition, which if yer running linux then becomes the active partition. And that's the problem, 'cause I can't resize an active partition, and I can't resize it from within OS X since OS X can't make heads or tails of any partition besides its own.

The only remaining options, while I'm RMA'ing the new OD, are either:
(1) somehow put ISO9660 image for liveCD install disk on external firewire hdd and make it bootable (which I tried before, but failed; maybe I should try again),
(2) figure out how - using dd, perhaps? - to move install from the 2.5 Gig partition to the 140 Gig partition. But then I'm sure you can't do that, can you - it'd mess up the boot process, right?
(3) Somehow move everything but /boot from the small 2.5 Gig ext3 partition, and put everything else onto the 140 Gig ext3 partition, and adjust fstab to mount remainder of fs properly.
(4) resize/move active partition (the 2.5 Gig ext3 one) while running linux, which so far as I can tell isn't possible, but perhaps I'm mistaken.

Thoughts?
Thanks,
Peter

---

### Post by mrelektron on 2009-10-02
I'm leaning towards (3), since a couple more hours of fiddling along various other lines came up short. Still can't get unetbootin to create bootable ISO 9660 image that powerpc mac recognizes, e.g.

So, I have everything - full install - in, say, /dev/hda4, which is only 2.3GiB, and I've created a new partition, /dev/hda5, which is 146.60 GiB. I'd have to edit the bootstrap parition, I'm sure, if I wanted to put the full install in /dev/hda5, but what might work is to leave - what - /boot on /dev/hda4, and move everything else to /dev/hda5, and edit /etc/fstab appropriately. Does that sound like something that would work?

Thanks,
Peter

---

### Post by mrelektron on 2009-10-02
Done.

This is for newworld powerpc.

The problem is that I *already* have a working Ubuntu install on my hdd, but the partition's full, I have another much larger partition, and I want to move the install to that partition. Also have a working OS X partition. But, I can't resize the working linux partition when running linux since it's then an active partition, can't resize it from OS X, and I can't resize it from a liveCD since....

the optical drive's not functional.

Being a bit afraid of locking myself out of my computer irretrievably, I did the move via an external firewire hdd. BTW despite numerous attempts using various partition tables &c, unetbootin *never* worked for me.

I don't claim any level of technical competency or correctness in what follows other than that I eventually got it to work.

---

Boot into Mac OS X. Create Apple partition table (not MBR, not GUID) on external hdd.

Reboot into linux on internal hdd. Use mac-fdisk to edit partition table on external hdd. gparted won't work btw. Create new bootstrap partition using command "b"; create linux parition using command "c". (BTW in the process I later found I had to edit this partition table which I was able to do eventually with gparted, b/c apple wants some buffer space between partitions for some reason - sorry, I don't pretend to understand, but without leaving a bunch of cylinders between partitions on the external hdd, nothing worked. I dunno why. I also don't know why initially I couldn't format partitions using gparted but later I could. Sorry. After many hours and many missteps, one loses track.)

Reboot into linux again. New linux partition on external hdd should automount (in my case, only if external hdd is on at boot).

Copy everything from working internal hdd linux partition to new external partition. I tried using dd and dd_rescue (googling "clone") and these did NOT work; they would copy stuff over but it was unreadable/mountable/bootable. So I copied just using cp -R. Should use --preserve flag too.

Also mount bootstrap partition of external hdd. Edit yaboot.conf's entries ("partition" and "root") and make sure they're pointing to where you're going to put your linux install on the external hdd. Also edit /etc/fstab on external hdd's new linux partition, too; use blkid to get uuid's for this.

Now try rebooting, holding down appropriate keys (opt in my case) to boot from external hdd. I had various problems re permissions, which required me to boot back from old internal partition numerous times and chmod things. E.g,  .dmrc (should be 644), or
mkdtemp: private socket dir: Permission denied
....which came down to wrong permissions on .gvfs in home dir, or:
sudo: must be setuid root
....which means you can't sudo things; this is fixed  by logging out/ logging back in to old partition, mounting new partition, editing permissions &c:
chown root:root path-to-new-mounted-partition/usr/bin/sudo
chmod 4755 ..../usr/bin/sudo

Lots of this stuff. Finally, I was able to boot off the external firewire hdd. (This is the compressed version. It took me from 6pm last night until 1 pm today to do all of this.)

*then* you can run gparted and edit the full partition table of the internal hdd. Eventually you'll mount the two internal partitions, copy everything from one to the other (just using cp, surprisingly enough), and finally edit yaboot.conf on the bootstrap partition on the internal hdd.

Shutdown, disconnect external hdd, powerup, cross fingers and... voila.

Regards,
Peter

---

