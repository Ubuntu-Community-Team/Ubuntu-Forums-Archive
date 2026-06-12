---
title: "Bad checksums wrong"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by poppers1957 on 2007-04-10
22dbcd0958d5f19be4ae4f91410a1170 <<<<<<This is the checksum listed for xubuntu-6.10-desktop-i386.iso on the site...[http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/MD5SUMS](http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/MD5SUMS)

The checksum I got after downloading was 7cldcd7p978fcddd259c7f5711c0c19a7988

Because I kept getting the wrong checksum after downloading it 3 times, I deceided to burn it anyways and see what happened.  While booting I used the option to check cd integrity.  It came back with 0 checksums found bad.  SOOOOOOOOOOOOOOO either the checksums listed at the site are wrong or my sha1sum program is wrong.  When I downloaded Fedora Cores 6 disks, all the checksums came back right the first time for each.  I am kinda baffled, anyone have any suggestions as to what might be wrong?

---

### Post by PointSource on 2007-04-10
The checksum listed is a MD5 sum, not SHA1, so your sha1 program is fundamentally wrong

---

