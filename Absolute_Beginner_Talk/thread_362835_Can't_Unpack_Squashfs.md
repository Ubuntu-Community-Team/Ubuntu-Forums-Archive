---
title: "Can't Unpack Squashfs"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by talikarng on 2007-02-16
I am trying to create my own live cd based on my current installation of ubuntu 6.06 using the following walkthrough:
[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)

I can mount the squashfs filesystem fine but when i come to copy the contents of it to another folder i get a lot of error messages along the lines of;
 
cp: cannot create symbolic link `edit/usr/share/doc/ubuntu-artwork/html': Operation not permitted
cp: cannot create symbolic link `edit/usr/share/doc/unzip/changelog.gz': Operation not permitted
cp: cannot create symbolic link `edit/usr/share/doc/vim': Operation not permitted

Some files copy but others do not. I am working on a mounted fat32 drive when i do this. 

Help?

---

### Post by talikarng on 2007-02-16
Sorry, I forgot to mention that I have tried using Reconstructor and saw the same messages in the terminal.
After i burnt the cd it hung every time i tried to use it to boot my laptop.

---

