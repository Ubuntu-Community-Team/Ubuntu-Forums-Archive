---
title: "[SOLVED] LILO needs installation I have no way to the 'net"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-13
I need to install LILO in order to get my removeable media to mount.

This UF post shows how and why:

DVD burner not recognized after upgrade to Feisty
[http://ubuntuforums.org/showthread.php?p=2706945#post2706945](http://ubuntuforums.org/showthread.php?p=2706945#post2706945)

it says to replace grub with lilo.

I can't get on the net with the laptop, because I can't run the cd, which is needed to install the ndiswrapper package. I tried installing the individual files for the wrapper, but that failed.

---

### Post by Tommy on 2007-07-13
the thread also mentions a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706)

which says it has been fixed in an update. (if you were online you might have to be sure the repositories are turned on.)

one option would be to "downgrade" then upgrade ... install from an Edgy CD and upgrade to Feisty using the update manager.

---

### Post by Mark_in_Hollywood on 2007-07-13
Bless you for this. I've been 16 hours trying to resolve a problem only related to this post.

Putting in the Canonical 6.06 LTS Dapper Drake fixed the failed combo DVD-ROM/CD-rw immediately.

I could not get the Toshiba Laptop model 1905-s304 to read either the combo drive or the floppy.

---

### Post by Tommy on 2007-07-13
> **Mark_in_Hollywood said:**
> Bless you for this. I've been 16 hours trying to resolve a problem only related to this post.

Putting in the Canonical 6.06 LTS Dapper Drake fixed the failed combo DVD-ROM/CD-rw immediately.

I could not get the Toshiba Laptop model 1905-s304 to read either the combo drive or the floppy.

Great! But if you install and upgrade from Dapper, be sure to upgrade through Edgy and then Feisty... you don't want to try to skip a version using the automatic upgrade tool.

---

