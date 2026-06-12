---
title: "Repartition on iMac G3, Ubuntu is the ONLY available OS"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by stir-crazy on 2008-11-11
Hi there,

I'd like to repartition my 8.04 install so I can put the /home directory on its own partition...thought I did this at setup but apparently not.  I'd like to use gparted or some equivalent, but can't get any of the Ubuntu Live CD's to run, nor can I find any Gparted Live CDs for a PPC architecture (tried the i386 version, no go).

Any ideas?  Can I use gparted over the network maybe?  Thanks!

---

### Post by stream303 on 2008-11-11
Without a lot of ram, the live-cd's for PPC won't run, and you may be stuck with using the "alternate" images.

Are you doing this because of the 8gb or 128gb firmware limitation for /root on the early machines, and have a lot of unused space left over on a larger replacement drive?

---

### Post by Coreigh on 2008-11-11
Can you create a bootable USB drive, install gparted there and resize the unmounted hard disks? I do not know if G3 supports USB booting but I think it does.

---

### Post by stir-crazy on 2008-11-11
I did use the alternate install partitioner to resize the partition, then was able to use gparted to create a new partition for the /home directory.  However, I ran into all sorts of problems trying to modify the fstab to recognize that the new partition should be /home.

Since this was a relatively new install anyway, I'm going through the tedious process of reinstalling all over again, though this time I was able to create the separate /home partition.  I want to do this in case I ever need to reinstall the OS, or am not happy with an "upgrade" (like 8.10...it's awfull, even on my Dell).  Nothing to do with the 128 Gb firmware limit; drive's only 40 Gb.

On a side note, I've also never been able to install 7.10 or more recent distros on a PPC.  Several iMac's and an iBook have attempted MANY variations (kubuntu, ubuntu, xubuntu, live and alternates), but always had fatal errors during the install, or ended up with partitions like /media/ and /media/home, etc.  I've always had to start with 7.04, update and upgrade.  Just me?

Thanks all who responded.

---

### Post by stream303 on 2008-11-12
Sounds like a clean install was the way to go, and 7.04 was one of my favorite releases.  Unfortunately, it has EOL'ed, so no more updates, and if you reinstall, I'm not sure if you can get the last of the updates or if the update repos even work since they have been changed to ports.ubuntu.com rather than archive.ubuntu.com....

(One of the reasons I'm a fan of installing "AptonCD" - makes it easy and convenient to keep all the incremental upgrades backed up in case something goes haywire and the repos are gone and you want to reinstall...)

I guess if you are using it to upgrade, and that goes well - great.  Are you planning to upgrade all the way to 8.04 LTS?

And, as much as I like to support Ubuntu, I can also vouch for Debian 4.0r5 working well on ppc, if you like the stable, albeit somewhat older software - and there are still updates coming down the pike.  One can wander back and forth between Ubuntu and Debian pretty easily.

---

### Post by stir-crazy on 2008-11-12
Going all the way to 8.04LTS.  Still get updates despite it being a PPC...an issue I wish there were enough numbers to reopen.  But 8.04 is great (I liked 7.10 better than 7.04), but I'm not liking my experience with 8.10 so far; will likely downgrade soon.

And an edit.  Last night I WAS finally able to cleanly install 7.10 on a 400mhz g3 iMac...woo hoo!  That is one "consistant" thing I've noticed about these machines...if it doesn't take the first several attempts...keep trying until it does!

---

### Post by stir-crazy on 2008-11-12
Going all the way to 8.04LTS.  Still get updates despite it being a PPC...an issue I wish there were enough numbers to reopen.  But 8.04 is great (I liked 7.10 better than 7.04), but I'm not liking my experience with 8.10 so far; will likely downgrade soon.

And an edit.  Last night I WAS finally able to cleanly install 7.10 on a 400mhz g3 iMac...woo hoo!  That is one "consistant" thing I've noticed about these machines...if it doesn't take the first several attempts...keep trying until it does!

---

### Post by stream303 on 2008-11-12
Cool - Hardy 8.04 is fine.  As a safety measure, I'd write or print out the existing /etc/X11/xorg.conf file before each release upgrade - you may need it or reference it later on.

On another machine of mine that's sticking to Hardy, I've got the backports repository enabled - mainly to grab the latest version of Gimp in the 2.4 series.

As a reminder, "LTS" is no guarantee for PPC.  The plug could be pulled anytime, so I tend to do an AptonCD archive pretty regularly.  Am I paranoid much? :)

Anyway, glad to hear it's working for you, especially about being able to use the rest of your drive with the /home partition..

---

### Post by stream303 on 2008-11-13
> **stir-crazy said:**
> I did use the alternate install partitioner to resize the partition, then was able to use gparted to create a new partition for the /home directory.  However, I ran into all sorts of problems trying to modify the fstab to recognize that the new partition should be /home.

Guess what I just found!

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Nice job!

---

