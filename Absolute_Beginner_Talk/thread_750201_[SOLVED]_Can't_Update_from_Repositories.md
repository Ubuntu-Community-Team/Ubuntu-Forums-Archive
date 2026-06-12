---
title: "[SOLVED] Can't Update from Repositories"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2008-04-09
Hi,

So I just got my new Dell Inspiron 1525 with Ubuntu pre-installed.

I've added all the repository DVDs to Synaptic using the 'Add' bit. It seemed to read correctly, and the correct lines are in 'sources.list'. (I've commented out any reference to the repositories I don't want / need.)

(I'd better explain that all my repositories are on DVD, as I don't have the 'Net.)

When I try to 'Reload' Synaptic, it errors on the DVD entries, saying
> Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used be used to add new CD-ROMs 

So I tried 'apt-cdrom add' and it too seemed to read the disk OK, then errored at the end with a message about being unable to write to the location.

This is not the first time I'd done this procudure, but it is the first time I've done it on a Dell with pre-installed Ubuntu.

Any ideas, or am I better off wiping all the Dell stuff off the HD and doing my own install from scratch ?

---

### Post by forrestcupp on 2008-04-09
Did you try going to System->Administration->Software Sources?  In the Ubuntu Software tab make sure the CD box is checked and that everything else is unchecked.  Click the Updates tab and make sure the Pre-released updates and Unsupported updates are unchecked.  Then with the DVD in the drive, try doing a ```
sudo apt-get update
```

---

### Post by WorldTripping on 2008-04-09
> **forrestcupp said:**
> Did you try going to System->Administration->Software Sources?  In the Ubuntu Software tab make sure the CD box is checked and that everything else is unchecked.  Click the Updates tab and make sure the Pre-released updates and Unsupported updates are unchecked.  Then with the DVD in the drive, try doing a ```
sudo apt-get update
```

In the Ubuntu Software tab, everything is unchecked, apart from the one and only item in 'Installable from CD-ROM / DVD.

The sudo 'apt-get update' just returns the ame errors as before:
> Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used be used to add new CD-ROMs 

I'm thinking that maybe Dell did something, and I'm tempted to just wipe the drives and start from a proper Ubuntu install.


EDIT:
Wiped the Dell install and reinstalled from a LiveCD. All repositories now working.

---

