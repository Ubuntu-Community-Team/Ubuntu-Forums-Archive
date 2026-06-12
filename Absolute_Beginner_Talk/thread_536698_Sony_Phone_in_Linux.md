---
title: "Sony Phone in Linux"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-28
Hey all
I buying a phone today for my sis . ie Se W580i newly released .. Just wanna ask will it work in Linux as my other K790i and 750i works in Linux so what say :D

[http://www.sonyericsson.com/spg.jsp?cc=in&lc=en&ver=4000&template=pip1&pid=10856&zone=pp](http://www.sonyericsson.com/spg.jsp?cc=in&lc=en&ver=4000&template=pip1&pid=10856&zone=pp)

---

### Post by Dark Star on 2007-08-28
Any idea dudes :) WIll this phone be identified by Ubuntu :?

---

### Post by Belyel on 2007-10-21
Did you find out if it works?  I jsut bought one.  I'll try plugging it in after I get it all charged and post back here.

---

### Post by Belyel on 2007-10-22
I tried it this morning.  Ubuntu sees the phone when I type 'lsusb' but does not bring anything up like a file manager window.  I can also charge the phone using the USB cable.  I'll try again after I get a M2 memory card.  According to the book, with a memory card in the phone, it should be recognized as a removable disk drive (in windows, anyway).

---

### Post by FuturePilot on 2007-10-22
> **Belyel said:**
> I tried it this morning.  Ubuntu sees the phone when I type 'lsusb' but does not bring anything up like a file manager window.  I can also charge the phone using the USB cable.  I'll try again after I get a M2 memory card.  According to the book, with a memory card in the phone, it should be recognized as a removable disk drive (in windows, anyway).

Make sure you put it into file transfer mode, or else it won't show up.

---

### Post by CookieNinja on 2007-10-31
On my phone the drive was found, but not automatically mounted. I had to mount it manually. The reason appears to be related to these lines in /var/log/syslog

> Oct 31 13:41:44 xxxxx-desktop kernel: [842906.815816] FAT: bogus number of reserved sectors
Oct 31 13:41:44 xxxxx-desktop kernel: [842906.815824] VFS: Can't find a valid FAT filesystem on dev sde.

I think that re-formating the disk under Linux will fix this issue and allow it to auto mount. I've not tried this yet, though. I just mount it manually, put things on it and copy things off it, and it works fine. I have to specify the file system when I mount it for it to work, though.

Hope that helps.

---

### Post by Dark Star on 2007-10-31
> **FuturePilot said:**
> Make sure you put it into file transfer mode, or else it won't show up.
Yep it works here fine :)

---

### Post by Chonnawonga on 2007-11-05
I just bought this phone the other day. It has an M2 card, which loads up just fine when I plug it in and select "File Transfer".

The only problem I've had so far is that when transferring music files through Amarok, sometimes the artist/title/etc. don't get read properly by the phone, and come up abbreviated. (For example, instead of "Moby", it just says "Mo".) This isn't a big deal, but it's kinda stupid. Anyone else having this problem?

Other than that, by the way, I'm loving the phone so far, and Ubuntu seems quite happy to work with it.

---

