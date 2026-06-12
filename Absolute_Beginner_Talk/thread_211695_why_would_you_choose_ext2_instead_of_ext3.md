---
title: "why would you choose ext2 instead of ext3?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-08
i googled the differences between ext2 and ext3, and I found this piece of information:
>    	 	 	 	 	 	 	 	 	  [LIST=1]
[*][SIZE=2][FONT=Helvetica, Arial, sans-serif]***What 	is the difference between ext2 and ext3 filesystem?***
Ext3 	filesystem is essentially an ext2 filesystem except for the fact 	that Ext3 supports journaling for ext2. Ext3 has been structurally 	implemented same as ext2, i.e. The data structures are the same. 	This implies that a cleanly umounted Ext3 filesystem can be 	successfully mounted as ext2 filesystem and an ext2 filesystem can 	be successfully mounted as ext3 if it is journalled.[/FONT][/SIZE]
[*][SIZE=2][FONT=Helvetica, Arial, sans-serif]*** Ok. But what is journalling?***
In earlier days (ext2), a 	sudden power failure or another such condition could leave the 	filesystem in an inconsistent state. So after every boot the fsck 	program was run for every uncleanly unmounted filesystem. This took 	very long. Ext3 avoids this time consuming task by letting check 	only the specific areas that were recently accessed or modified. For 	this a log is kept which is called ï¿½Journalï¿½. 	This way filesystem checking time is drastically reduced.[/FONT][/SIZE][SIZE=2][FONT=Helvetica, Arial, sans-serif]okay i got that.  so why is ext2 even a choice anymore?  isn't ext3 ext2 but better? (because it has that "journaling" thing?)
[/FONT][/SIZE]
[/LIST]

---

### Post by user1397 on 2006-07-08
bump!

---

### Post by NeghVar on 2006-07-08
Because some may prefer it, just because something is technically better doesn't mean that everyone buys into it.

I'm still running my record player here while all you fools risk having your hard drives crash and loose all your mp3s...

---

### Post by user1397 on 2006-07-11
but still, its like:

ext2 = bread

ext3 = bread and butter!

---

### Post by krazykirk on 2006-07-11
well you can say the same thing a about fat32 and ntfs (in windows), ntfs is newer and better, but some people still prefer and use fat32.

---

### Post by FuzZy2006 on 2006-07-11
cos' it can share space with linux :D

---

### Post by user1397 on 2006-07-11
well yea, but fat32 has an advantage, like krazykirk said, it can be shared with linux.  ext2, however, seems to have no advantages at all.

please, if someone knows of one advanatge of ext2, i want your thoughts.

---

### Post by catlett on 2006-07-11
Just like windows doesn't keep you from formatting to fat32, linux doesn't keep you from formatting to ext2.
The reason appears to be the same. Windows 2000, Windows XP, Windows Server 2003 and Windows Vista all can run on ntfs. Any other version of windows cannot use ntfs. They have to use fat32 (and I suppose fat but I don't know, I'm not that old :D ) So I assume windows keeps fat32 as an option for the older systems.
Ext3 is not supported by older kernels. I am not a kernel expert but I think "old" and "new" is referring to pre and after 2.2 (this may be wrong but there are "old" kernels) The older kernels do not recognise ext3. They purposely made ext3 backwards compatible so it can run as ext2 to older kernels (kind of like using a USB 2 device in a USB 1.1 port, it will work but not have the performance of a 2.0 device) And like windows I suppose linux distros feel they should leave it as an option because there are older kernels  out there that run on ext2.
Plus why would you limit anything to anyone? Why just get rid of it?
There may be other reasons I don't know about but that is one that comes to my mind. This is all speculation on my part. I do not have any real knowledge as to why ext2 is still a choice for formatting. This just seemed  a likely possibility to me.


P.S. You always get me tthinking Erik. Now I am going to be bothered by this until I get a real answer. Thanks for keeping me up.;)

---

### Post by SkyNet2029 on 2006-07-11
The only one I can think of is this: ext2 is less CPU intensive when performing a Directory listing or File search, (also its a little slower than ext3 because of this ). Oh, and that it takes less CPU time to actually perform a mount/umount transaction. Is this a benefit? If you are using a fairly new (and Large) hard disk device whilst running a slower processor, then yes.  Given the low cost of todays higher performance hardware though, ext3 is better, while a safe bet for the old box is still ext2.

---

### Post by user1397 on 2006-07-11
> **catlett said:**
> Just like windows doesn't keep you from formatting to fat32, linux doesn't keep you from formatting to ext2.
The reason appears to be the same. Windows 2000, Windows XP, Windows Server 2003 and Windows Vista all can run on ntfs. Any other version of windows cannot use ntfs. They have to use fat32 (and I suppose fat but I don't know, I'm not that old :D ) So I assume windows keeps fat32 as an option for the older systems.
Ext3 is not supported by older kernels. I am not a kernel expert but I think "old" and "new" is referring to pre and after 2.2 (this may be wrong but there are "old" kernels) The older kernels do not recognise ext3. They purposely made ext3 backwards compatible so it can run as ext2 to older kernels (kind of like using a USB 2 device in a USB 1.1 port, it will work but not have the performance of a 2.0 device) And like windows I suppose linux distros feel they should leave it as an option because there are older kernels  out there that run on ext2.
Plus why would you limit anything to anyone? Why just get rid of it?
There may be other reasons I don't know about but that is one that comes to my mind. This is all speculation on my part. I do not have any real knowledge as to why ext2 is still a choice for formatting. This just seemed  a likely possibility to me.that makes sense, i didnt think of that.


[quote=catlett]P.S. You always get me tthinking Erik. Now I am going to be bothered by this until I get a real answer. Thanks for keeping me up.;)[/quote]no problem ;)

---

### Post by user1397 on 2006-07-11
> **SkyNet2029 said:**
> The only one I can think of is this: ext2 is less CPU intensive when performing a Directory listing or File search, (also its a little slower than ext3 because of this ). Oh, and that it takes less CPU time to actually perform a mount/umount transaction. Is this a benefit? If you are using a fairly new (and Large) hard disk device whilst running a slower processor, then yes.  Given the low cost of todays higher performance hardware though, ext3 is better, while a safe bet for the old box is still ext2.okay, thanks for reinforcing catlett's thought, i hope that calms you down, catlett. :D

---

