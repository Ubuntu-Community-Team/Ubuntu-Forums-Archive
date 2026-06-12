---
title: "MegaRAID 511 IDE in 5.10"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by jkpq45 on 2006-10-09
Hello All,

Attempting to install a MegaRAID 511/i4 IDE RAID5 adapter into my 5.10 system; the drivers were automatically installed with the OS and are found under "SCSI", though it is an IDE adapter.  The OS does not recognize the array and mount it for me in the same folder as my Floppy, CDRW and Filesystem, which I expected.

Any help would be appreciated.  All I need this box to do is be a file server, so controlling that RAID card is absolutely necessary.

Thanks for the help,
jkpq45

---

### Post by furiousV on 2006-10-09
I don't know much about getting RAID to work, but MegaRAID caught my eye, and I remembered reading an article on the [SUSE Linux Rants](http://www.suseblog.com/?p=156) site.

It might help, it might not, here it is anyway

[http://www.suseblog.com/?p=156](http://www.suseblog.com/?p=156)

Sorry I can't give any more personal advice.

I would suggest you post some system info on the forums, so others know what system you have when they try and help you.

Specs, *dmesg*, *lspci* and *mount*

When mounting RAID arrays, shouldn't the device be mda, mdb and so on, instead of sda, sdb - which are the actual drives?

Again, sorry I can't help any more.

---

### Post by jkpq45 on 2006-10-09
I'm a complete n00b, can't it be easier than that?  I thought it would be simple.

When I try to cp the megaraid.ko he has compiled into the /scsi and /ide driver folders, they change file format from object code into something else.

Do I need to recompile after adding a file into these directories?  How do I do that if I need to?

-jkpq45

---

