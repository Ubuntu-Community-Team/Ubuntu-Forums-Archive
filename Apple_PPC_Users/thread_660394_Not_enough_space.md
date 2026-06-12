---
title: "Not enough space"
date: 2008-01-06
forum: Apple PPC Users
---

### Post by seedy on 2008-01-06
Update Manager gave me the option of upgrading from 6.something to 7.10, so I let it, things went a bit oddly, and things are a bit off ever since. Everytime I try to update further I get the following error message after it begins checking sources...

> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occured while processing tads2-dev (NewFileDesc2), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-powerpc_Packages, E:The package lists or status file could not be parsed or opened.'

I'm wondering how to find out which version I'm running now, and then how to get out of this endless upgrade-but-you-can't loop.

PB G4 1.25, file manager shows over 20GB left on the partition.

Thanks,
seedy

---

### Post by Robsteranium on 2008-01-09
Are you trying to update (i.e. packages) or upgrade (i.e. ubuntu)?

I used Ctrl+C to skip errors during the upgrade which then disappear on the next iteration (i.e. try, try and try again).

I'm no expert but I'd be curious about the file that is mentioned in the error message:
> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-powerpc_Package

What's in your package lists folder?
```
ls -l /var/lib/apt/lists/
```

Perhaps there's something wrong with permissions or file locks?  Have you tried moving the offending file (back-up not remove) and re-running the update manager?

Perhaps the tads2-dev package is faulty?

---

