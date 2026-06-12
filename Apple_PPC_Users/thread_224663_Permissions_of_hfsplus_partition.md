---
title: "Permissions of hfsplus partition"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by merman on 2006-07-28
Hi

Using [this guide ]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") my /etc/fstab has the following line...

```
/dev/hda3 /media/hda3 hfsplus ro,user,file_umask=0111,dir_umask=0000 0 0
```

However it won't mount and dmesg gives

```
[  167.790709] HFS+-fs: unable to parse mount options
```

I can mount the partition without the file_umask and dir_umask options, but then the permissions don't allow access to most of the drive. file_umask and dir_umask are both listed as options for hfs(plus?) in the man page for mount, yet obviously aren't being recognised. I'm using Ubuntu 6.06 ppc.

Hopefully someone has some advice...

Cheers - Tom

---

### Post by avtolle on 2006-07-28
[http://ubuntuforums.org/showthread.php?t=206926&highlight=hfs](http://ubuntuforums.org/showthread.php?t=206926&highlight=hfs) is a somewhat related thread, and offered for your information. What are you exactly wanting/needing to do in the partition?

---

### Post by merman on 2006-07-28
> **avtolle said:**
> What are you exactly wanting/needing to do in the partition?

Thanks - seems the problem in that thread is different - in that for me mount seems to be objecting to the file_umask and dir_umask options.

I'm trying to mount the partition with permissions such that all (or even just my) users in Ubuntu can access all of it. Mounting it with no options works, but permissions on it are such that I can't access most of the drive (eg most of the contents of my Mac OS home directory).

---

### Post by avtolle on 2006-07-28
Thanks for your reply. [http://ubuntuforums.org/showthread.php?t=220742&highlight=hfs](http://ubuntuforums.org/showthread.php?t=220742&highlight=hfs) is another thread dealing with hfs+, hope it has some information that helps. My memory is that there are problems accessing the hfs+ file system from Linux, something to do with it being journaled. I don't dual boot, don't have Mac OS files to access, so is something with which I don't have familiarity. Will see if I can come up with other threads later; gotta get back to work.

---

### Post by avtolle on 2006-07-28
Merman, perhaps elderly eyes are failing me, but in the code snippet you provided in your first post, the zeroes at the end appear to be separated by spaces, but when referencing the guide linked in said post, in the example, seems these are separated by a tab. How far off am I. And, if I'm even close to correct, I would try separation w/ a Tab, not a space and see what happens.

---

### Post by merman on 2006-07-28
> **avtolle said:**
> the zeroes at the end appear to be separated by spaces

No, they're a tab. The problem is with file_umask=0111,dir_umask=0000 as when I remove these options it works...but obviously without the permissions they should be setting.

---

### Post by avtolle on 2006-07-28
merman, my read of the man pages for mount is that the discussion is limited to hfs, and not hfs+. May have read too quickly, but that is my impression. Will post back if I can find anything of value.

---

### Post by avtolle on 2006-07-28
[http://www.jonh.net/lppcfom-serve/cache/761.html](http://www.jonh.net/lppcfom-serve/cache/761.html) found on google; doesn't sound promising.

---

### Post by merman on 2006-07-28
> **avtolle said:**
> [http://www.jonh.net/lppcfom-serve/cache/761.html](http://www.jonh.net/lppcfom-serve/cache/761.html) found on google; doesn't sound promising.

Out of date. hfsplus support has been in the kernel for some time now.

---

### Post by avtolle on 2006-07-28
My bad; should have looked at the date closer.

---

### Post by avtolle on 2006-07-28
Merman: While this thread [http://ubuntuforums.org/showthread.php?t=212182&highlight=hfs+permissions](http://ubuntuforums.org/showthread.php?t=212182&highlight=hfs+permissions) deals with an external HDD, I wonder if the solution in the second post would have any merit for your situation?

---

### Post by tokyovigilante on 2006-08-08
I am seeing the same issue trying to access my HFS+ partitions on my AMD64 system.([Don't ask ;)]("http://www.osx86project.org"))

The partition mounts fine, but the Kernel is respecting the HFS+ permissions and disallowing access by non-root users to directories not marked public under OS X. 

The easy way round this is to sudo -s and copy any files you need to an ext3 partition elsewhere on your drive. 

Read/write access is perilous from Linux because of the proprietary nature of the journalling used on HFS+. I see others have had corruption while attempting to force write access. The above solution works fine, but a better way would be as the OP has tried to do - find a way to let users access the privileged directories directly. I'm sure there's a way round this, I'll see what I can find over the course of the week.

---

### Post by joachim.j on 2006-08-19
It seems like before you can get proper read AND write acces to a HFS+-formatted volume you need to make sure that journaling is disabled.

To disable journaling in the OS X terminal:

[FONT="Courier New"]diskutil disableJournal /Volumes/TheNameOfYourVolume/[/FONT]

There is no need to sudo to do this.

---

### Post by domino on 2006-08-19
I bet if you ran Nautilus as root you would have read/write perms ;). You would have to enable root in OS X first, and also enable root in Ubuntu. That way, I would think both has the same UID and GID. Any other user name in Ubuntu wold only give you read perms.

cheers

---

### Post by zazzman on 2006-08-22
I have to preface my entry with the warning that I am a complete newbie. I was having the same problem with accessing my files on my hfs+ partition. What I discovered is that by default OSX doesn't allow any access for the gid for files and folders in your User's folders. I don't know if this is the wisest thing, but I went into the Finder, did a "Get Info" on all the files/folders I wanted to access in Ubuntu, I then went under permissions and switched the Group ID to something I could use in Ubuntu. I then made sure that the line in the fstab that mounts my hfs+ partition had a "gid=XXX" statement that matched what I set in OSX. I also made sure that the user I was using in Ubuntu was part of the group mentioned above. If this doesn't make sense, let me know and I will clarify. Also, if you need help with OSX permissions, here is a link to an Apple KB article: [http://docs.info.apple.com/article.html?artnum=107039]("http://docs.info.apple.com/article.html?artnum=107039")

---

### Post by zazzman on 2006-08-22
One more thing...

I didn't turn of journaling in OSX, but I only set my hfs+ partition to ro in Ubuntu.

---

### Post by zazzman on 2006-08-22
One more thing...

I didn't turn off journaling in OSX, but I only set my hfs+ partition to ro in Ubuntu. I want to do more research before I try to write to hfs+ from linux.

---

