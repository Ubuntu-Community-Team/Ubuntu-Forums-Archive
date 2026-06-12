---
title: "help on encrypted dvd's"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-10
I have installed the codecs and libraries that I need to read an encrypted DVD. My drive will recognize the disk. the automount function is workind and places and icon on my desktop that is labled the name of the dvd. when I try to play it nothing happens and I get a msg saying the disk cannot be read. I can watch ripped dvds just fine.

I ran dpkg --list | grep libdvd and below is the output:


rdsii64@rdsii64-Ubuntu:~$ dpkg --list | grep libdvd
ii  libdvdcss2                                 1.2.9-2medibuntu2+build1               Library for accessing DVDs like block device
ii  libdvdnav4                                 0.1.10-0.1                             The DVD navigation library
ii  libdvdread3                                0.9.7-2ubuntu1                         library for reading DVDs
rdsii64@rdsii64-Ubuntu:~$ 

is there anything I am missing.
thanks

---

### Post by skipb on 2007-10-10
You might take a look at this. I followed it and my dvd's play perfect.
[Restricted Formats/Playing DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by rdsii64 on 2007-10-10
> **skipb said:**
> You might take a look at this. I followed it and my dvd's play perfect.
[Restricted Formats/Playing DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

have that page bookmarked.  I followed their instructions and I still can't play them yet.

---

