---
title: "rEFIt - Invalid Node Structure"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by jackbusch on 2009-04-01
It seems that I've severely pissed off my OS X partition. Here's how:

1) I re-partitioned my hard disk that had an existing OS X installation in order to make way for Intrepid.
2) Intrepid failed the first time round because I failed to install rEFIt first.
3) I installed rEFIt after the fact, again having to re-partition.
4) Everything worked fine for several weeks.
5) I decided to dally with Puppy Linux and burned a LiveCD. Then I got distracted and left it in the drive.
6) OS X went into suspend mode. I came back and:
7) The computer had shut itself off and whenever I tried to boot it up, it would give me the Apple logo and then the spinning "loading" thingy and then shut off after awhile.
8) Tried to run Disk Utility off of the OS X discs. Repair failed: Invalid Node Structure.
9) Booted off my rEFIt liveCD and successfully booted into Ubuntu.
10) Tried booting from rEFIt LiveCD into OS X and same result as 7.

So, I take it I've confuzzled my rEFIt partition, too? rEFIt doesn't pop up without the CD in it.

I did turn off journaling on my OS X partition, too, and have been sharing my iTunes library between Linux and OS X, but I haven't been attempting to write to the OS X partition from Linux...


Is there a quick fix for this that doesn't require a backup and reformat?

Thanks for your help

I'm on a macbook 2,1

---

### Post by jackbusch on 2009-04-01
Oh also, I get this...

```
jakc@jakc-laptop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb

```

I wanted to yank some important files off my OS X partition before reformatting, but I don't have proper permissions. Is there a way to force it?

---

### Post by cyberdork33 on 2009-04-02
> **jackbusch said:**
> Oh also, I get this...

```
jakc@jakc-laptop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb

```I wanted to yank some important files off my OS X partition before reformatting, but I don't have proper permissions. Is there a way to force it?
you have to use sudo with that command in Ubuntu.

I think you are screwed. That is just my opinion though. It sounds like some system file got messed up on the OSX side (updates?). This could also be the sign of a failing hard drive, so be sure to backup to something externally. Good Luck!

PS I really don't think that Ubuntu or rEFIt or anything else caused this... Crap like this happens sometimes, and without journaling, filesystem errors can occur that cannot then be fixed. If you google "Invalid Node Structure OSX" you will get a lot of hits. One is this:
[http://www.macosxhints.com/article.php?story=20070204134513557](http://www.macosxhints.com/article.php?story=20070204134513557)
Not a really good solution, but a solution none-the-less.

---

### Post by jackbusch on 2009-04-02
Thanks - I found that DIY solution, too, but I'm afraid it may not serve me very well as I'm unable to mount the volume in order to back it up.

---

### Post by cyberdork33 on 2009-04-02
> **jackbusch said:**
> Thanks - I found that DIY solution, too, but I'm afraid it may not serve me very well as I'm unable to mount the volume in order to back it up.
you shouldn't have to mount a partition to clone it.

I think that mounting it in Ubuntu (if you can) and copying files to an external hard drive is probably a good path to take. If you need help with mounting the partition, please try to mount it and post any error message here.

---

### Post by scotthep on 2009-04-02
I spent two days dealing with this exact same problem and finally got my system back and going as of today.

I had tried to install Ubuntu 9.04 64bit and the grub install failed so I'm not sure if the problem came from rEFIt or a combination of the install and rEFIt.

Anyhow, I eventually fixed it by booting into the OSX install disk and using the terminal. By running the mount command without options I noticed that the main OSX volume was mounted. Sure enough I was able to read from the drive as if nothing was wrong even though I was getting the "Invalid Node Structure" errors from diskutil (commandline diskutil reported the same errors, btw). 

I plugged in an external USB drive and copied over the data I needed and then ran a restore from my time machine backup. In case your wondering I don't have time machine backing EVERYTHING up by default. Unfortunately that bit me in this case and it won't happen again.

NOTES and things I learned - FYI:

1 - The fdisk included within OSX only works on the MBR which is not the same as the GPT partition table. I should have known this.

2 - Read the man pages for OSX UNIX command if your used to the Linux equivalents they ARE NOT the same, again I should have known

3 - Gparted, at least from what I can tell cannot resize HFS+ partitions, however it does seem to be GPT partition table aware

4 - Handy tools to understand within the OSX commandline: diskutil, gpt, and fdisk

5 - When using the OSX version of "cp" using the "cp -pvR" command preserves file creation dates, is verbose, and is recursive (in that order)

Hope some of this info helps everyone.

---

### Post by cyberdork33 on 2009-04-02
> **scotthep said:**
>  3 - Gparted, at least from what I can tell cannot resize HFS+ partitions, however it does seem to be GPT partition table aware
I think it can only shrink OSX partitions... If not the Ubuntu version, then there are other version out there that can (parted magic is one).

---

### Post by jackbusch on 2009-04-02
Thank you thank you! I'll try using your hints. My main issue is that my corrupted drive is 320 gb and my spare drive is 80 gb. So, cloning the whole thing isn't really an option. Anyway, I'll post if I get things working.

---

