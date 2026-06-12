---
title: "new partition write access"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2007-05-22
I just used G parted live cd to create some new partitions, by the way it worked great.

Well anyway now I have logged back in and I discovered I don't have access to the new partition, I can see it, but I can't write to it. 

Any Ideas?

---

### Post by LaRoza on 2007-05-22
What OS(s) are you using?

What is the new partition formatted as?

What error messages, if any, are you getting?

---

### Post by taurus on 2007-05-22
If it is ntfs, then you need to install ntfs-3g before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

But if it is ext3, then you just have to change the ownership from root to your login name so you would have full access, read/write, to it with the chown command.

---

### Post by Jason Weiss on 2007-05-22
> What OS(s) are you using?

What is the new partition formatted as?

What error messages, if any, are you getting?
Reply With Quote


Feisty Fawn 

ext2

> Error while copying to "/media/disk".

You do not have permissions to write to this folder.

---

### Post by taurus on 2007-05-22
Since it's ext2, just change the ownership then.

```
sudo chown -R **jason**:**jason** /media/disk
ls -la /media
```
_assuming_ **jason** is your login name.

---

### Post by Jason Weiss on 2007-05-22
> **taurus said:**
> Since it's ext2, just change the ownership then.

```
sudo chown -R **jason**:**jason** /media/disk
ls -la /media
```
_assuming_ **jason** is your login name.

Wow it worked, I am surprised you could identify the drive from the information I provided 

Thanks

---

