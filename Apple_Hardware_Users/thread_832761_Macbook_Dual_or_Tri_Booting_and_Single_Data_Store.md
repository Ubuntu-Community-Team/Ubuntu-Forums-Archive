---
title: "Macbook Dual or Tri Booting and Single Data Store"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by keylimepie82 on 2008-06-18
Hello,

First of all, I must apologize ahead of time for my ignorance.  I've used Ubuntu for a while, and I've been able to set up a Ubuntu / XP dual boot on a Dell before with a help of a friend, but I'm not really familiar with the terminology, or in fact, with any of this. 

Basically, I would like to be able to use Mac OS, Ubuntu 8.04 Hardy Heron, and Windows XP on my macbook, in such a way that I can access all the data no matter which operating system I'm using.  If this is too difficult, I'd be happy with just dual booting with Mac OS and Ubuntu with the same file sharing thing.

Also, on the Dell I mentioned in the first paragraph, is there anyway to make it so that I can access the files on XP while I'm using ubuntu, and vice-versa?

---

### Post by cyberdork33 on 2008-06-18
> **keylimepie82 said:**
> Basically, I would like to be able to use Mac OS, Ubuntu 8.04 Hardy Heron, and Windows XP on my macbook, in such a way that I can access all the data no matter which operating system I'm using.  If this is too difficult, I'd be happy with just dual booting with Mac OS and Ubuntu with the same file sharing thing.
It can be done, but it is a little difficult since support for the various filesystems in the other OSs is often not that great.

Your best best would probably be to create a FAT32 partition that can easily be shared between all three systems.

The main Macbook wiki is here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

but they good triple-boot install guides are on the Macbook Pro wiki page here:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

> **keylimepie82 said:**
> Also, on the Dell I mentioned in the first paragraph, is there anyway to make it so that I can access the files on XP while I'm using ubuntu, and vice-versa?Your XP partition should easily be mountable from within Ubuntu. Check under the places menu. Mounting the Ubuntu partition in XP will require a little more work. There is an ext2/3 driver for Windows, but I do not know how well it works.

---

### Post by _alex_ on 2008-06-18
I used to have OS X (hfs+), Vista (ntfs), and Ubuntu (ext3) partitions setup. All of which could be accessed with read permissions from each of the respective OSs. Ubuntu can read/write to the ntfs partition (not sure about OS X), so I'd recommend ntfs over fat32, as it doesn't have the 4GB file limit, and I had no problems writing to it from Ubuntu.

I recently removed Vista as I had no need for it, by partitioning it to ext3. OS X can write to ext3, but I don't trust the driver, so I just set it to be read-only from OS X.

---

### Post by cyberdork33 on 2008-06-18
> **_alex_ said:**
> I used to have OS X (hfs+), Vista (ntfs), and Ubuntu (ext3) partitions setup. All of which could be accessed with read permissions from each of the respective OSs. Ubuntu can read/write to the ntfs partition (not sure about OS X), so I'd recommend ntfs over fat32, as it doesn't have the 4GB file limit, and I had no problems writing to it from Ubuntu.

I recently removed Vista as I had no need for it, by partitioning it to ext3. OS X can write to ext3, but I don't trust the driver, so I just set it to be read-only from OS X.
NTFS is a valid option, though, you have to use FUSE on both ubuntu and OS X which is not native support. FAT32 will be fast, though there is the 4gb filesize limit.

the ext3 read/write driver for OS X has been very broken for a while, it works better under Tiger though.

---

