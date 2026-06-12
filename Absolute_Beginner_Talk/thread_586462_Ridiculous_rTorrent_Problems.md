---
title: "Ridiculous rTorrent Problems"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Stringsy on 2007-10-22
I've had a hopeless time with Linux trying to get this working and it's driving me up the wall.

Please don't ask why it has to be the most up to date version of rTorrent... it just does.

I should be running Lenny on my box, but I have rtorrent pinned to Unstable.

Sometimes it crashes and I get this message:

Caught Segmentation fault, dumping stack:
0 rtorrent [0x8078cf1]
1 rtorrent [0x807dd05]
2 [0xb7eee420]
3 /usr/lib/i686/cmov/libcrypto.so.0.9.8(BN_num_bits+0x1c) [0xb7be7aac]
4 /usr/lib/libtorrent.so.10 [0xb7d48fa4]
5 /usr/lib/libtorrent.so.10 [0xb7d2c175]
6 /usr/lib/libtorrent.so.10 [0xb7d2e353]
7 /usr/lib/libtorrent.so.10(_ZN7torrent9PollEPoll7performEv+0xad) [0xb7cea93d]
8 rtorrent [0x80bf7a6]
9 rtorrent [0x8079377]
10 /lib/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb78eb050]
11 rtorrent(_ZNK7torrent8FileList14free_diskspaceEv+0x91) [0x8052c81]
Aborted

Other times it starts up fine but I get "Couldn't Resolve Hostname" in front of every torrent.

I'm completely new to Linux, but I don't see why I'm having so many damn issues with this.

Please help.

---

### Post by hyper_ch on 2007-10-22
do you want to compile rTorrent from the latest SVN repo?

---

### Post by Stringsy on 2007-10-22
I just grabbed it from the unstable debian repository.

If there's a way for me to manually compile it (i have no idea how) and it will work.. then yeh, that'd be great, how do I do it?

---

### Post by realvz on 2007-10-22
[http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html#more-122](http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html#more-122)

---

### Post by hyper_ch on 2007-10-22
If you have Feisty Fawn:

[http://www.howtoforge.com/compile_rtorrent_from_svn_ubuntu](http://www.howtoforge.com/compile_rtorrent_from_svn_ubuntu)

If you have Gutsy:

[http://www.howtoforge.com/node/2701](http://www.howtoforge.com/node/2701)  (not yet officially published)

---

### Post by Stringsy on 2007-10-22
Using Debian.

Linux dorchester.vectoral.info 2.6.18-5-686-bigmem #1 SMP Wed Sep 26 19:03:46 UTC 2007 i686 GNU/Linux

That's my system info.

---

### Post by hyper_ch on 2007-10-22
The gutsy info should also work for debian (I did it last weekend on my server). However those two packages "libsigc++-2.0-0c2a libsigc++-2.0-dev " are different. Maybe it's only one of those that are different.

---

### Post by Stringsy on 2007-10-22
It seems to be working now that I've deleted a lot of stuff from my server.

Is it feasible that that Segmentation fault arose because there was insufficient room on my HDD?

---

### Post by hyper_ch on 2007-10-22
Why do you actually post here for debian problems?

---

