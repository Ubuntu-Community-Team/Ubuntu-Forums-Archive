---
title: "Swapping hdd but keeping installed stuff"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by Brad wilkinson on 2005-06-28
Ok, I set up Ubuntu on a old 4 gig hdd, and have been playing with configurations and so on. I also have a SETI/BOINC client installed.

Now I have a nice new 2.5" hdd (quiet) and I want to just move all the data from the old hdd to the new hdd. If i just hook the new hdd up as a secondary drive (hda?), how do I copy the whole drive across (including MBR) so I can take out the old one, and plug the new in as a primary? (hd0?)

Also, with my old PIII/dual mobo, will it just accept the 2.5" hdd with no master/slave jumper on it?

EDIT

And also, how come my winXP machine shows up with its name in the SETI machines list, but my ubuntu boxes just show up as localhost.localdomain? 

I suppose it has to do with the NAT on my ADSL modem, but I gave my ubuntu boxes names just like i did with the winXP. They show up as those names inside my network.

---

### Post by Darkscot on 2005-06-28
The manufacturer of your new HDD may provide the software to copy (clone) your hard drive.  I did this recently when I installed a new Maxtor 200Gb drive.  Maxtor provide a software package called Maxblast which does the job.  It is a Windows package but you can create a boot disk so you could run it from startup.  It will only work if one of the drives is a Maxtor but I am sure all the other leading brands do something similar.

---

### Post by Brad wilkinson on 2005-06-28
well i found the user guide, but no software to copy the hdd, or image the old one onto the new one......

but now I do know how to set the master/slave relationship, and i have all the pinouts for the disk! :grin:

---

### Post by Brad wilkinson on 2005-06-28
ok, so i google/linuxed this and came up with this

[http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html](http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html)

but it is 2000 vintage. so is it still reasonable, or is it so far out of date to be laughable? :confused:

---

### Post by Darkscot on 2005-06-28
If I were you I would probably try Clone Maxx.  It is a free and according to the reviews it works...

[http://www.download.com/PC-Inspector-Clone-Maxx/3000-2248-10216112.html](http://www.download.com/PC-Inspector-Clone-Maxx/3000-2248-10216112.html)

---

### Post by Brad wilkinson on 2005-06-28
ok, well i'll try it tomorrow (sleepy now), but it looks like a windows prog to me.

have you used it on a *nix system?

---

### Post by Darkscot on 2005-06-28
[QUOTE=Brad wilkinson]ok, well i'll try it tomorrow (sleepy now), but it looks like a windows prog to me.

have you used it on a *nix system?[/QUOTE]

I haven't tried it at all.  But I am just saying if I were you I would try it, but that is the kind of guy I am!

---

### Post by Kvark on 2005-06-28
Shouldn't it just be to make a complete backup of the old disk and then restore the backup to the new disk?

---

### Post by Brad wilkinson on 2005-06-28
ok, well i've been searching about a bit, and I have a number of possible ideas, but I would like someone to confirm/deny the feasability of each for me.....

1) could I just copy the whole disk to a *.tar on a drive on another machine on the network, then remove old drive, install new drive, boot from live cd and untar across the network onto the new drive? would the new drive need to be formatted first? would the *.tar have the bootloader included?

2) if I remove old drive, install new, do fresh install from cd, would I then be able to put old drive in as slave and copy across? would the fact that there was a bootloader on each drive bork things totally or would the new drive being on primary channel/master make it boot and leave the old drive on secondary/master as just another drive?

3) should I just copy the contents of /user/me to another machine on the network, then do a clean install and just download updates/extra packages again? most of the reason I am trying to do this is to avoid d/l'ing the extra packages again, but I havn't set up a local repository for source/binary packages yet (going on how much trouble i'm having with this, that could be an even bigger stretch).

cheers,
Brad

---

### Post by Kvark on 2005-06-29
[QUOTE=Brad wilkinson]1) could I just copy the whole disk to a *.tar on a drive on another machine on the network, then remove old drive, install new drive, boot from live cd and untar across the network onto the new drive? would the new drive need to be formatted first? would the *.tar have the bootloader included?[/QUOTE]

The tar idea won't work, the bootloader would end up in the wrong place on the disk.

[QUOTE=Brad wilkinson]2) if I remove old drive, install new, do fresh install from cd, would I then be able to put old drive in as slave and copy across? would the fact that there was a bootloader on each drive bork things totally or would the new drive being on primary channel/master make it boot and leave the old drive on secondary/master as just another drive?[/QUOTE]

Having both disks in at once works fine. Perferably give them a cable each so they can both be masters, it's faster that way. But making them share the same cable and put one as slave works too. The worst thing dual booting two ubuntu installs can cause is making you choose between booting ubuntu and booting ubuntu on startup without any indication of which one is the new one.

That way you can copy over all your files from the old one to the new one. But I doubt you can install packages on the new one using already installed packages on the old one as source.


[QUOTE=Brad wilkinson]3) should I just copy the contents of /user/me to another machine on the network, then do a clean install and just download updates/extra packages again? most of the reason I am trying to do this is to avoid d/l'ing the extra packages again, but I havn't set up a local repository for source/binary packages yet (going on how much trouble i'm having with this, that could be an even bigger stretch).[/QUOTE]

This is what I'd do. Not all of it though, not the hidden /home/me/.program/ thingys many programs make. Only the parts that are your documents.



but...

If you get a complete hard disk chrash with hardware fried and everything. Then you need to restore the backup to a new disk. So it must be possible to use a backup for this. I think the easiest way would be to find a backup program that makes a backup of the whole disk and not just your documents. Make backup from old one, restore to new one.

---

### Post by savage on 2005-07-12
I am interested in doing this and see that this thread is still dangling.

"Really only useful if you mess up grub, or copy your installation to a new hard drive and need to reinstall grub."
[ HOWTO: Make a Ubuntu Boot-CD (Like a boot floppy)](http://www.ubuntuforums.org/showthread.php?t=19428)

"...like rebooting, are Windows CrazyThings(tm)."
[Howto: Backup and restore your system!](http://www.ubuntuforums.org/showthread.php?t=35087)

"Restore GRUB quite simple in Ubuntu"
[ HOWTO: Restore GRUB (if your MBR is messed up)](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

---

