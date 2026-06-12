---
title: "YA HFS+ mounting problem"
date: 2012-01-31
forum: Apple Hardware Users
---

### Post by xilod on 2012-01-31
Hi all! I have Ubuntu 11.10 installed with packages: hfsplus hfsprogs hfsutils and also sda4 drive with HFS+ filesystem on it, my purpose is to write some files onto that drive, I know that to do that I must disable journaling, but I even can't mount it just to read the contents, _I've tried all the ways I found in google and in this forum_, of course, all I get is the following error:
"mount: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error".

Could anyone help me to deal with that?

---

### Post by Lars Noodén on 2012-01-31
What do the last few lines from [font=Courier New]/var/log/syslog[/font] say when you get the error?

---

### Post by xilod on 2012-01-31
> **Lars Noodén said:**
> What do the last few lines from [FONT=Courier New]/var/log/syslog[/FONT] say when you get the error?
Jan 31 14:42:48 colix-netbook kernel: [ 5021.325038] hfs: invalid secondary volume header
Jan 31 14:42:48 colix-netbook kernel: [ 5021.325050] hfs: unable to find HFS+ superblock

---

### Post by flitter2009 on 2012-06-12
Hi,

Has anyone seen a resolution to this type of problem? I've got a non-journalled HFS+ partition that I can't seem to get to mount no matter what I try! Same symptoms as above...

Oh - this is on Pangolin, which I thought was going to fix all my problems ... :-)

---

