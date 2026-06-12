---
title: "Home folder sharing OSX/Ubuntu?"
date: 2008-01-27
forum: Apple Intel Users
---

### Post by smocksturr on 2008-01-27
I have a working triple boot with Mac, Ubuntu, and Windows.
I'd like to be able to access my media in my Mac home folder from Ubuntu.
I would not like to change UID and GID, Ive heard this can be disastrous and tricky.
Can someone suggest a way to use aliases or something so that I can read/write into my Mac home folder?
Either that or give me direct terminal commands to change my Linux UID?

---

### Post by davim on 2008-01-30
I would be interested in a solution for this one :)

---

### Post by cyberdork33 on 2008-01-30
disable journaling in OSX 
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

Then you just mount the partition in Ubuntu. That's it.

Keep in mind that the HFS+ filesystem uses *nix style permissions so your Mac user's files are 'owned' by another user other than your Ubuntu user and the permissions must be changed to allow access to other users.

---

### Post by ronocdh on 2008-01-31
> **cyberdork33 said:**
> Keep in mind that the HFS+ filesystem uses *nix style permissions so your Mac user's files are 'owned' by another user other than your Ubuntu user and the permissions must be changed to allow access to other users.
IIRC, this is as simple as managing the folder properties in OS X for your home folder there. I don't often need to access things on my OS X partition these days, but when I do I can, given that I've disabled journaling and modified the permissions, enabling r/w.

You can disable journaling on HFS+ external drives too, to use in Ubuntu. Problem is, because I think the HFS+ support is isn't integrated in the kernel, a bad unmount will mess up your permissions. Safest way to resolve this (you can't write to the drive anymore) would be booting into OS X and letting the fsck process run when you attach the hard drive. You might have to then manually disable permissions on the drive, the same way you do with your home directory.

---

### Post by cyberdork33 on 2008-01-31
> **ronocdh said:**
> I think the HFS+ support is isn't integrated in the kernel

It is, just not very well... but good considering the information available.

---

### Post by mcoyle on 2008-02-10
I have done this and I have ONE small problem I can't solve. Here is what I did.

On MacOS X my UID=501 and GID=501. After installing linux, which creates the first default user with IDs of 1001, I create a new user with the same MacOS X user name, and then changed the user/group IDs to 501. 

In fstab, this is my entry to mount the hfs partition:

/dev/sda2 /mnt/mac hfsplus uid=501,gid=501,auto,rw,users 0 0

This works flawlessly except for one problem: I can't get the flash plugin to work in either Firefox or Konquerer. I've create other users on the ext3 partition and the plugin installs and works 100% of the time. 

I find it hard to believe the plugin cares if it's on an HFS vs ext3 partition, but I'm out of ideas.

If I solve it, I'll return to post.


MIchael

---

