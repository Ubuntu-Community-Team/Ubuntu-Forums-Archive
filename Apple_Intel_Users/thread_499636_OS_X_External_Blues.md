---
title: "OS X: External Blues"
date: 2007-07-12
forum: Apple Intel Users
---

### Post by makaira on 2007-07-12
Well, after following the wiki on how to format an external harddrive with ext3, and having OS X pop-up a window saying that the drive couldn't be read, I decided to reformat the drive with the Mac Journaling file system. I would love to know if anybody knows why OS X was unable to read the drive...

Anyway, this question has to do with OS X exclusively. Is there any way to remove the reserved space on my drive? It's a 320GB external and I'm only getting 289. I know in Linux you can :

```

sudo tune2fs -m 1 /dev/sdb

```

but that doesn't seem to be a possibility on OS X.

Thanks.

---

### Post by makaira on 2007-07-19
Well, I believe I was unable to read/write to the ext3 external drive because I didn't have the proper drivers installed. Anyway, the external is still hfsplus and I have a question:

Basically, this drive is being used for bittorrent and to back-up cd's and dvd's. Is there any way that I can use the torrent files and the other information on the disk (let's say, an incomplete torrent) through both the Linux and OS X partition?

For instance, if I was downloading a CD and had it incomplete on the OS X partition, could I move over to Linux and open up my bittorrent client and finish the torrent? Mind you, both the torrent and the information it's writing will be on the external drive. If I can't do this with hfs+, is it possible at all? What steps do I need to take?

Thanks

---

### Post by [woodstock] on 2007-07-19
I am no expert but it should be possible. [Here at gentoo]("http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling") is a very shot descrition how to mount hfs+ file systems.
I read somewhere that the *user ID*s have to be *identical* for conjointly access. Linux usually starts numbering at 1000, for MacOS 500 is the starting point. 
There is a howto somewhere to achieve that (identical user IDs that is) but I can't find the page at the moment**. It was probably related to gentoo, maybe you start your search there.

**as always I am only able to find things once and then never again. Maybe another one of Murphys laws.

---

### Post by cyberdork33 on 2007-07-19
> **'[woodstock] said:**
> I am no expert but it should be possible. [Here at gentoo]("http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling") is a very shot descrition how to mount hfs+ file systems.
I read somewhere that the *user ID*s have to be *identical* for conjointly access. Linux usually starts numbering at 1000, for MacOS 500 is the starting point. 
There is a howto somewhere to achieve that (identical user IDs that is) but I can't find the page at the moment**. It was probably related to gentoo, maybe you start your search there.

**as always I am only able to find things once and then never again. Maybe another one of Murphys laws.

You just have to make sure to change the permissions on the files to allow all users. You do not have to fiddle with UIDs

---

### Post by [woodstock] on 2007-07-20
Yes, that is possible too, and its the simpliest solution if the computer is used by one person only.
However, if there is more than one user, one might not like to give write permission to all the others. Then one have change the user IDs.

---

### Post by cyberdork33 on 2007-07-20
read permissions to everyone vs screwing up your system.

---

### Post by cevans on 2007-07-21
> **cyberdork33 said:**
> read permissions to everyone vs screwing up your system.

Changing uids is rather simple, and giving read permissions to everyone could very well be considered "screwing up the system" in some circumstances.

If I recall correctly, all that I needed to do to change the uid in Ubuntu to allow proper access (I am far more comfortable with GNU/Linux than OS X) was change my user's UID in /etc/passwd, and then chown -R my home directory. You won't want to have said user logged in at the time, of course, and might also want to remove everything in /tmp after the change in order to ensure that various files there don't need to have permissions changed.

I would much rather change OS X to use the same, reasonable, uids (1000+n) that nearly every other *nix system uses, but I'm rather wary in considering such changes, since OS X has bizarre ways of dealing with users and passwords involving NIS. However, I only use HFS for my OS X partition, so this isn't a major issue for me.

---

### Post by cyberdork33 on 2007-07-21
> **cevans said:**
> Changing uids is rather simple, and giving read permissions to everyone could very well be considered "screwing up the system" in some circumstances.

If I recall correctly, all that I needed to do to change the uid in Ubuntu to allow proper access (I am far more comfortable with GNU/Linux than OS X) was change my user's UID in /etc/passwd, and then chown -R my home directory. You won't want to have said user logged in at the time, of course, and might also want to remove everything in /tmp after the change in order to ensure that various files there don't need to have permissions changed.

I would much rather change OS X to use the same, reasonable, uids (1000+n) that nearly every other *nix system uses, but I'm rather wary in considering such changes, since OS X has bizarre ways of dealing with users and passwords involving NIS. However, I only use HFS for my OS X partition, so this isn't a major issue for me.

I agree that this is probably the best way... but if you look through the threads here, it seems like a bit of trouble to go through just to get access to some files. Take your pick.

---

