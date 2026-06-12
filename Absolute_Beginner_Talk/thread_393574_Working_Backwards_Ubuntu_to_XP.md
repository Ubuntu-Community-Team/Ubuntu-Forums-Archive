---
title: "Working Backwards: Ubuntu to XP"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by googanhiem on 2007-03-25
I have installed Xubuntu on an old computer and it works great, but would like to have the option to use XP. This computer too old and slow to really use a windows emulator. 

This seems like the backwards way of doing this, as there is a lot of how-to and such on going from windows to window/ubuntu dual boot system, but I'd like to go from Ubuntu to a ubuntu/windows dual-boot system and cant really find a guild on how I'd go about doing this. 

Would somebody be able to outline how I would going about partitioning my single hard drive and installing windows without deleting xubuntu. Any help would be appreciated.

---

### Post by slayerboy on 2007-03-25
What you're looking for is essentially the same thing.  The major thing is that when you install Windows, it messes with the master boot record, which is where Grub is stored.  You'll have to reinstall grub back to the MBR in order to boot into Ubuntu again.

The way I see it, you have two options (maybe more depending on how you look at things):

1.  Wipe the whole disk and install windows, then once you have windows installed you can install xubuntu again.  You'll lose all your data, so make sure to back everything up

or

2.  You could keep it the way you have it now, but you'll have to get a boot disk or use your live cd to get back into your xubuntu installation.

---

### Post by johnc4510 on 2007-03-25
To the best of my knowledge, windows must be installed in the first position on the hard drive to be able to dual boot linux.

---

### Post by googanhiem on 2007-03-25
Well I definitely don't want to erase Xubuntu now that I've got it just the way I like it. So I'm guessing to install windows I'll have to adjust the partition before I put in the Windows cd, cause I can only imagine that Fdisk would format the whole thing. I just got gparted, but it doesnt appear to have a "create new partition option" and I'm assuming I need to keep my linus swap drive, so i shouldn't/couldn't install on to that part. Any tips?

---

### Post by zvacet on 2007-03-26
[http://ubuntuforums.org/showthread.php?t=358183&highlight=windows]("http://ubuntuforums.org/showthread.php?t=358183&highlight=windows")

---

### Post by googanhiem on 2007-03-26
Thanks a lot for pointing me towards that. I'll give it a go.

---

