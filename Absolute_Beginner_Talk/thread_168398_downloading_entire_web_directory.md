---
title: "downloading entire web directory"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-04-30
hey how do i use wget to download an entire directory from an ftp site?

---

### Post by delta32 on 2006-04-30
Try the recursive option.

wget -r url

The man pages say that it'll only go down 5 folders so you'd have to change the default level to something else if you want it to go deeper. 

From the man page: -l depth --level=depth

Setting it to 0 would make it unlimited.

---

### Post by malavar on 2006-04-30
yea i read the man pages before posting, and i also tried wget -r url before posting, but it doesnt download the entire ftp directory. im trying to download openbsd and theres no iso image. 
heres the ouput:

wget -r [ftp://mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/](ftp://mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/)
--11:58:47--  [ftp://mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/](ftp://mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/)
           => `mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/.listing'
Resolving mirror.iawnet.sandia.gov... 192.160.227.246
Connecting to mirror.iawnet.sandia.gov|192.160.227.246|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/OpenBSD/3.8/i386 ... done.
==> PASV ... done.    ==> LIST ... done.
mirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386: No such file or directorymirror.iawnet.sandia.gov/pub/OpenBSD/3.8/i386/.listing: No such file or directory
unlink: No such file or directory

FINISHED --11:58:48--
Downloaded: 0 bytes in 0 files

---

### Post by delta32 on 2006-04-30
Strange. I tried it and it works fine for me. Does it do the same thing on other mirrors?

---

### Post by malavar on 2006-04-30
wow i feel so stupid , my working directory was deleted while i was transfering files to another pc hehe. thanks delta32 problem solved!

---

### Post by malavar on 2006-04-30
btw do you know how to make bootable disks from these files? ive never made a bootable cdrom unless it was an ISO image...and i didnt have any luck finding articles.

---

