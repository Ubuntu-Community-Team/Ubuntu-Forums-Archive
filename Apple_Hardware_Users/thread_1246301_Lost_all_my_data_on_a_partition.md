---
title: "Lost all my data on a partition"
date: 2009-08-21
forum: Apple Hardware Users
---

### Post by sawmaster on 2009-08-21
Hey.

I installed ubuntu on a partition on my macbook's HD. I never was able to access my ubuntu partition from mac os x. I later wanted to add a few more partitions, so I cloned my ubuntu partition using winclone and removed it. Later, I wanted to put it back (I decided to not make any new partitions), so I tried restoring with winclone, but it fails. I wondered if my partition was corrupt, so I restored Windows 7 (I had windows 7 earlier on my macbook before ubuntu) and it works great. 

Can anybody help me restore my ubuntu partition correctly? 

Thanks in advance.
-Ben

---

### Post by quixote on 2009-08-22
(This may be old news to you, but multibooting a Mac OS requires something like rEFIt.  There's an excellent explanation here: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) )

Re your ubuntu partition: have you tried restoring it to some other drive?  Possibly winclone messed up the clone somehow?

---

### Post by sawmaster on 2009-08-22
> **quixote said:**
> (This may be old news to you, but multibooting a Mac OS requires something like rEFIt.  There's an excellent explanation here: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) )

Re your ubuntu partition: have you tried restoring it to some other drive?  Possibly winclone messed up the clone somehow?

I already have rEFIt. I can't restore to another partition because all my drives will no longer partition ("No space left on device" on disk utility. Isn't that caused by my the HD being fragmented?).

The ubuntu partition never mounted in OSX. Do you think winclone may have never cloned it properly? If I try to mount the clone, it fails. The diskimagemounter  tells me "No mountable file systems."

---

### Post by quixote on 2009-08-24
I'm confused about what you're trying to do.  You're expecting to see your ubuntu partition from OSX?  Or are you expecting to both see and use it?  Is it your ubuntu system partition you're talking about?  (I.e. root, "/"?)  Or a data partition that you use with ubuntu?  Or your ubuntu /home partition?  (Assuming any of the latter are separate partitions.)

When you tried to use winclone on the ubuntu partition, which OS were you in?  Windows?  MacOSX?  For what it's worth, windows products tend to work okay with other windows products, but treat non-MS stuff somewhat carelessly.  If you have this to do over again, you might want to try something like [Clonezilla]("http://clonezilla.org") instead.

The "no space left on device" only means that all space is already allocated.  However, if some of that space isn't used -- for instance, the Win7 partition is 50GB, but only 20GB has files on it -- then you can turn some of that space into another partition if you want.  (You can only have 4 primary partitions, and it sounds like you're near that limit.  So you'd want to create it as a logical partition on an extended one.)

---

### Post by sawmaster on 2009-08-24
> **quixote said:**
> I'm confused about what you're trying to do.  You're expecting to see your ubuntu partition from OSX?  Or are you expecting to both see and use it?  Is it your ubuntu system partition you're talking about?  (I.e. root, "/"?)  Or a data partition that you use with ubuntu?  Or your ubuntu /home partition?  (Assuming any of the latter are separate partitions.)

When you tried to use winclone on the ubuntu partition, which OS were you in?  Windows?  MacOSX?  For what it's worth, windows products tend to work okay with other windows products, but treat non-MS stuff somewhat carelessly.  If you have this to do over again, you might want to try something like [Clonezilla]("http://clonezilla.org") instead.

The "no space left on device" only means that all space is already allocated.  However, if some of that space isn't used -- for instance, the Win7 partition is 50GB, but only 20GB has files on it -- then you can turn some of that space into another partition if you want.  (You can only have 4 primary partitions, and it sounds like you're near that limit.  So you'd want to create it as a logical partition on an extended one.)

Winclone is a OSX only app. I only have 2 partitions. My Mac's internal HD is 80GB. My windows partition (where Ubuntu was) is 16GB. After finding that my ubuntu partition **_CLONE_** did not restore, I restored an old Win7 clone I had, before Ubuntu came along.

Did that make any sense?

---

### Post by quixote on 2009-08-26
I guess we're going to have to wait for someone with a some experience with winclone.  I would think, if it's OSX only, it's probably corrupted the ubuntu clone it tried to make.  OSX uses HPFS filesystem (I think I have that right) and ubuntu uses ext3 (or ext4).  The cloning software would have to be aware of the different filesystems to make a valid clone, and I don't know if winclone does or not. (Win7 uses NTFS.  Maybe winclone understands that, but not ext3?  The documentation ought to say.)

Did you have data or something else that you wanted to get off the ubuntu partition?  

If not, it would make a lot of sense to just reinstall.  You could try wubi to put it with your Win7 install without having to worry about partitioning.

If you do have data you want on the ubuntu partition, then we need to concentrate on finding a way to read the image made by winclone, which is something I have no clue about. :(  Do you have that winclone ubuntu image on a CD?  On your Mac partition?  Or where?

---

### Post by sawmaster on 2009-08-26
> **quixote said:**
> I guess we're going to have to wait for someone with a some experience with winclone.  I would think, if it's OSX only, it's probably corrupted the ubuntu clone it tried to make.  OSX uses HPFS filesystem (I think I have that right) and ubuntu uses ext3 (or ext4).  The cloning software would have to be aware of the different filesystems to make a valid clone, and I don't know if winclone does or not. (Win7 uses NTFS.  Maybe winclone understands that, but not ext3?  The documentation ought to say.)

Did you have data or something else that you wanted to get off the ubuntu partition?  

If not, it would make a lot of sense to just reinstall.  You could try wubi to put it with your Win7 install without having to worry about partitioning.

If you do have data you want on the ubuntu partition, then we need to concentrate on finding a way to read the image made by winclone, which is something I have no clue about. :(  Do you have that winclone ubuntu image on a CD?  On your Mac partition?  Or where?

You're probably right. I didn't have much data on there, and nothing was probably lost. Just some customizations. I guess it probably makes sense to reinstall it on a fresh partition.

---

