---
title: "Read OS X in Ubuntu: correct fstab format"
date: 2007-01-23
forum: Apple PPC Users
---

### Post by three-cushion on 2007-01-23
I was able to manually 'mount' my Tiger volume dirs (Read-only) with the following:

[INDENT] mkdir /mnt/macosx[/INDENT]
[INDENT]mount /dev/hda10 /mnt/macosx -t hfsplus[/INDENT]

What I want to do is make this automatic each boot of Ubuntu.

My /etc/fstab file is:
**(See Thumbnail gif)**


What does the line look like for  the Tiger system (my Tiger volume) = /dev/hda10  ?? 
I looked at man pages but could not understand what is needed...
such as <mount point> <type> ... etc.....



Thanx in advance...Jim B

---

### Post by grazie on 2007-01-23
You've pretty well got it. However the ordering of parameters when using mount is important

$ sudo mount -t hfsplus /dev/hda10 /mnt/macosx 

My /etc/fstab entry for read only access to my Tiger drive is similar to below. You could mount with write access, but you MUST disable journaling on the HFS+ drive first. I'd recommend staying with read only. I'll let you look up the other parameters with man fstab and man mount.
```

#<file system> <mount point> <type> <options>                                                <dump> <pass>
/dev/hda3           /mnt/macosx     hfsplus  ro,gid=1000,umask=000,users,exec  0              0

```

---

### Post by three-cushion on 2007-01-25
Grazie: Your mount for reading Tiger folders is:
> ```

#<file system> <mount point> <type> <options>                                                <dump> <pass>
/dev/hda3           /mnt/macosx     hfsplus  ro,gid=1000,umask=000,users,exec  0              0

```

What works for reading my Tiger folders is:

```

#<file system> <mount point> <type> <options>                                                <dump> <pass>
/dev/hda10        /mnt/macosx     hfsplus  ro,gid=20,uid=501,umask=000,users,exec  0              0
```

I found the gid,uid from my Tiger NetinfoManager, the umask basically says 'no,no,no' and user,exec are to replace nousers,noexec. 

And, I think this is a great way to "share" info FROM Tiger TO Ubuntu.. (NEO Office, desktop, any txt,rtf, pdf file i.e.)..:D 

Thanx again for your guidance.... 

Cheers

---

