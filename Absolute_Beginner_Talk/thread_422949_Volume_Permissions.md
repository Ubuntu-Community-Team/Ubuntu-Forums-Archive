---
title: "Volume Permissions"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by flashbuntu on 2007-04-25
Hi, I've just install the latest version (7.04) of Ubuntu and have a volume (ext3 format) for storing Data located at /media/linux_data.

My problem is the permissions are under root only and I'd like to access (read/write) under all users.

As I  understanding it, to change permissions of a volume is different to a file/folder.

Can someone point me in the right direct here, Cheers

---

### Post by flashbuntu on 2007-04-25
silly me, should have looked around, found this post and will give it a go later.

cheers.



Re: How do I change permission on ext3 formatted drive 

--------------------------------------------------------------------------------

i'm new at this as well but here is what i just did, it worked (pre req) the drive is formatted ext3 and mounted at /media/hdf1, (hdf1) is the name i gave the hard drive.

sudo -i 

this will get you to the root prompt (use your administrative user password when prompted)

chown -hR dave /media/hdf1

-hR refers to the mounted drive and subdirectories ( i think) and the dave is my username. After these two commands were completed i was able to use the second hard drive without any problems. Good Luck,
Mike
__________________
Mike W.

---

