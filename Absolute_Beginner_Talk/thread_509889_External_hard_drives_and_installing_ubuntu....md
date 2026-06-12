---
title: "External hard drives and installing ubuntu..."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by sethm on 2007-07-26
I'm currently running XP and want to ditch it completely (no partition) and install Ubuntu. My understanding is that I have to download an install disc, burn it, and then install of the burned CD.  Correct?  

While I don't have much in the way of important files, my gf has tons of songs on itunes that she'd want backed up somewhere and then re-installed onto ubuntu.  So my questions are thus:

[LIST]
[*]which external hard drive do i need to take things off of xp, store, and then import onto ubuntu?  i saw some threads with people complaining about maxtor drives...
[*]will amarok (or something else) allow my gf to play songs downloaded from itunes, purchase songs from similar sites, and import/export to her ipod?
[*]
[/LIST]

I've obviously a noobie, so any help would be appreciated.

---

### Post by Ek0nomik on 2007-07-26
> **sethm said:**
> [LIST]
[*]which external hard drive do i need to take things off of xp, store, and then import onto ubuntu?  i saw some threads with people complaining about maxtor drives...
[/LIST]

The brand of your external hard drive doesn't matter, so long as it works.  You will see some people complaining about getting their hard drive to work out of the box after an Ubuntu installation if it is formatted as NTFS.  Linux can't read NTFS file system's natively, but you can get the support.  However, I would personally suggest, along with others, that you format it to a natively read file system such as FAT32 of EXT3.  FAT32 gives you the benefit of working in both Linux and Windows.  It's what I use for both of my external hard drives.

> **sethm said:**
> [LIST][*]will amarok (or something else) allow my gf to play songs downloaded from itunes, purchase songs from similar sites, and import/export to her ipod?
[*][/LIST]

You can use Amarok to control the media for your iPod, yes.

There is a lot of documentation on how to do it, and problems people have while trying to do it.  Here are a few tutorials I was able to find, but I am sure there are an abundance of others:

[http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

[http://doc.gwos.org/index.php/IPod](http://doc.gwos.org/index.php/IPod) (This one may be for an older version of Ubuntu, but I am not positive.  This website seems rather slow to be updated, in my opinion)

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

[http://ubuntuforums.org/showthread.php?t=103071&page=3](http://ubuntuforums.org/showthread.php?t=103071&page=3)

I hope I was of some assistance.

---

### Post by sethm on 2007-07-26
That is helpful, thanks. :)

When I get the external hard drive, does it come naturally formatted with FAT32, or do I have to do something to the external drive or XP so it formats with FAT32?

---

### Post by Ek0nomik on 2007-07-26
> **sethm said:**
> That is helpful, thanks. :)

When I get the external hard drive, does it come naturally formatted with FAT32, or do I have to do something to the external drive or XP so it formats with FAT32?

It depends on the manufacturer(s).  I own a 250GB and 500GB Western Digital hard drive.  One of them came formatted as NTFS, and the other FAT32.  You should be able to check by having the hard drive plugged in and opening gparted via the Live CD or an installed version of Ubuntu by running the command 'gksudo gparted' in the terminal.

If you have a Windows install working, you should be able to check it from My Computer.  If you simply right click on the external hard drive I believe it tells you what file system it is.  (I think it did on XP at least.  I switched to Linux before Vista was released, so I don't know it as well)

**Edit**:  Oh, one more note.  I just wanted to remind you that FAT32 can be used with Windows and Linux, so that is the real advantage of it.  It allows you to take it pretty much anywhere in the world and it will work.  However, if you need to have a single file greater than 4GB, than FAT32 won't be the file system for you.  (If you backup DVD's ;), etc)

---

