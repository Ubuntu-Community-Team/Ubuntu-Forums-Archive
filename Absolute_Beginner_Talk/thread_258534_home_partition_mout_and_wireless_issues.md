---
title: "/home partition mout and wireless issues"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Stochastic on 2006-09-16
Ok, so i'm in a relatively fresh ubuntu dapper (I ran easyUbuntu for certain file types and some other features - did not do any 3d stuff) and my box is a Compaq v2346 or at least a v2300 series other than that.  There are two issues I'd like to get setup properly:

1st)  I have all my files (music/text/etc..) located on a second partition (fat32) and I would like it to become my /home folder but it's not allowing me to create a propper 'username' file that my current user is able to log in with (it's currently mounted as '/media/hda4'). What step-by-step process do I need to do to get it to be mounted as /home?


2nd)  I've got the infamous Broadcom 4318 built-in wireless; I've given up on getting it to work, so I went out and bought a D-Link DWL-G650 ver.B5  PCMCIA card to get wireless working.  I've got both cards to see the networks in range (essid) but the Broadcom won't connect such that Network Monitor sees it.  The D-Link is able to be connected to networks - according to both the Network Monitor and my router (although I can only see that it has a wireless lease when I am wired in by ethernet cable) - but when I open firefox it doesn't even reach 192.168.0.1 and there's absolutely no webpages loading by name or IP#.  I did once connect through this card (just after I bought it by a cafe) but not anymore.  Since then I did nothing but reboot and then it wouldn't work again. In an attempt to get home network running, I did attempt to refresh some of the DNS server info in Networking by deleting some of them assuming they'd come back (they didn't).  If anyone can help on this it'd be great.  Thanks.


Oh, and if anyone knows if the ATI Radeon XPRESS 200M 5955 (PCIE) card is easy to setup compiz / 3d with, would you like to run that info by me.  Thanks.

---

### Post by kidders on 2006-09-16
Wow, lots of issues! Let me take the first one.

Mounting /home on a FAT32 partition is a *really* terrible idea. Fluid permissions control in /home is pretty critical to Linux's security model (ie it's not satisfactory to tar all files with the same ownership & access privilege settings).

Having said that, I imagine that the reason you're doing it is so that you can share your personal files with a Windoze install. The best approach may be to create individual FAT32 partitions for all your users and mount them at "/home/username" and "C:\Documents and Settings\username". That way, you can lessen the impact of FAT32's crappy support for access control.

---

### Post by Stochastic on 2006-09-16
Would it be possible to have my Fat32 as my /home/stochastic and have another user's /home/user folder merely be a shortcut(is the linux term for this symlink) to a folder on the Fat32 partition?

---

### Post by Stochastic on 2006-09-16
Just an update, I've managed to fix the little bug I was running into with my wireless, now all I need to do is get my mount issue sorted and think about doing some xgl stuff.

---

### Post by kidders on 2006-09-16
> Would it be possible to have my Fat32 as my /home/stochastic and have another user's /home/user folder merely be a shortcut(is the linux term for this symlink) to a folder on the Fat32 partition?

Pretty much anything you'd like to do is possible, but the problem with this suggestion is the same as your original one, in that using FAT32 denies you the ability to apply distinct ownership/permissions to anything on the partition. For many purposes, this makes no difference ... but users' personal files are quite a different story, by and large.

Essentially, to store more than one user's stuff on the same FAT32 partition, you would have to grant totally unrestricted access to *all* of them. Not a pretty thought :-( If you really want to share a single /home partition with Windoze, perhaps HFS+ is worth serious consideration?

---

### Post by Stochastic on 2006-09-16
Well the reason its FAT32 is because it used to be shared with windoze but now I've deleted that security risk from my comp.  Is there any way to reformat the partition without loosing the data within?

---

### Post by kidders on 2006-09-17
> Is there any way to reformat the partition without loosing the data within?

That would be far too convenient lol. Afaik there's no reliable way to do that. You would need to move your data someplace else, reformat the partition, and copy your stuff back ... which can be quite awkward when the partition is big :-(

Having a separate /home like you want can be tremendously useful though.

The commands for creating filesystems all start with "mkfs". If you want to find out what filesystems your computer knows how to make, open a console, type "mkfs." and hit tab twice.

---

### Post by compwiz18 on 2006-09-17
howdy

I've got a good ol' v2000 as well.  I also have a script that automatically installs 3d and sets up compiz for ya.  I've got to fix a few things in it first (for instance, the compiz install script is outdated), I'll put it up tomorrow Japan time (w/e that is where you live, I don't know)  You may wish to only run part of it, otherwise it will try and set up your wifi too, and if you have that working you don't want my script to screw it up for you.

It will also mod your sources.list and add the multiverse/universe repos too, that can be edited out as well.

If you interested, post a message, and I'll fix it up for you.  It is sort of large (50MB), so if you have a slow connection it might not be a good idea.  It does, however, include the ATI drivers and what not, and those make up 99% (literally) of it.

---

### Post by Stochastic on 2006-09-17
That's ok, I've actually spent a few hours just now getting compiz working and configured somewhat correctly, and since my wireless is now working, I'm a happy man.  Oh, but out of curiosity, in compiz my right ctrl and alt are not recognized as ctrl or alt, only the left ones are.  Is there any way to fix this or any explanation for it?  And when using Compiz Settings Manager, how do I turn down the wobble on menus? Thanks.

---

### Post by Oblong_Cheese on 2006-09-17
> **Stochastic said:**
> Just an update, I've managed to fix the little bug I was running into with my wireless

What did you do to fix this issue? I am having similar troubles with the exact same PCMCIA card.

---

### Post by Stochastic on 2006-09-22
> **Oblong_Cheese said:**
> What did you do to fix this issue? I am having similar troubles with the exact same PCMCIA card.

It was a simple issue of an incorrectly typed password in the network setup.  I retyped my password and I'm now surfing fine.  I can confirm that this card D-Link DWL-G650 ver.B5 works great without any extra setup in Dapper (for me anyways).

---

