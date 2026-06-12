---
title: "Can't unpack squashfs"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by talikarng on 2007-02-16
I am trying to create my own live cd based on my current installation of ubuntu 6.06 using the following walkthrough:
[https://help.ubuntu.com/community/Li...ization/6%2e06](https://help.ubuntu.com/community/Li...ization/6%2e06)

I can mount the squashfs filesystem fine but when i come to copy the contents of it to another folder i get a lot of error messages along the lines of;

cp: cannot create symbolic link `edit/usr/share/doc/ubuntu-artwork/html': Operation not permitted
cp: cannot create symbolic link `edit/usr/share/doc/unzip/changelog.gz': Operation not permitted
cp: cannot create symbolic link `edit/usr/share/doc/vim': Operation not permitted

Some files copy but others do not. I am working on a mounted fat32 drive when i do this.

Help?

P.S: I had the same troubles using reconstructor earlier; the same messages appeared in the terminal.

---

### Post by apjone on 2007-02-16
are u root?

---

### Post by talikarng on 2007-02-16
I have run the commands using sudo.

P.S> Thanks apjone for giving me a thought, I logged in as root (using the su command) but when i tried to copy the contents I got the same error messages plus a few I hadn't noticed (or missed) earlier. The new messages were "failed to preserve ownership.....operation not permitted" and "preserving ACL..... operation not permitted"

Do you think this has anything to do with the fact that I am trying to get this to work on a FAT32 drive?

---

### Post by talikarng on 2007-02-18
Thanks anyway,

The problem was that I was using a fat32 partition.

When i started again on an ext3 partition i had no problems unpackign squashfs.

---

