---
title: "Can I use same swap partition for Ubuntu &amp; OS X?"
date: 2005-04-02
forum: Apple PPC Users
---

### Post by gti_guy on 2005-04-02
The second hard drive on my G4 died recently so I replaced it with a larger drive and installed Hoary on it with the requisite swap partition and it works just fine.

The old drive that died had a UFS partition I used for swap for OS X (Panther).

Is there some way I can use the same swap partition for both Hoary & Panther?  I've Google'd and seen articles about sharing Linux and *BSD swap partitions but I'm not sure sure how applicable they are to this situation.

Does anyone have any experience or suggestions in getting this to work?

Thanks.

---

### Post by askreet on 2005-04-02
They use different formats for their swap, I suppose if there was a way to make your bootloader reformat the partition appropriatly then It would work just fine.. But I dont think it's possible to share one filesystem type between the two.

---

### Post by gti_guy on 2005-04-03
Well, you can always share ext2/ext3 between them, but that doesn't buy me swap.

It looks like I can probably adapt the advice given in [http://www.resexcellence.com/hack_html_01/06-01-01.shtml](http://www.resexcellence.com/hack_html_01/06-01-01.shtml) 

but editing Hoary's /etc/init.d/mountall.sh and umountfs scripts instead of the LinuxPPC scripts mentioned in the article's "UPDATED (6-4-01)" section.

I was just hoping that I didn't have to be the guinea pig.  :wink:

---

### Post by gti_guy on 2005-04-03
Well, I tried it without success.  There's no way to format the swap partition as UFS or HFS+  from Ubuntu... just plain old HFS.  And Panther thinks the resulting HFS partition is corrupted because it doesn't have the usual .Trashes et. al. files on it.

I suppose one could install EXT2 support in Panther via [Ext2 Filesystem 1.3](http://http://www.macupdate.com/info.php/id/11657) , reformat the Ubuntu swap as EXT2 at shutdown and then use that partition for swap in Panther, but I'll leave that exercise to someone else. 

Too bad someone doesn't write an app that allows OS X to use Linux swap since it's probably more efficient then what Darwin/OS X uses.

---

