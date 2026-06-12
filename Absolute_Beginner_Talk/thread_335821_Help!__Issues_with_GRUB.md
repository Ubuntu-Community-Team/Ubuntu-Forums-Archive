---
title: "Help!  Issues with GRUB"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by humphry on 2007-01-10
Hi,

I have an older computer that, until today, ran Suse and Windows (dual boot).  I want to keep the Windows and install Ubuntu, and I think I went about it the wrong way.  

I used Acronis (partition software) to delete my 2 Suse partitions, leaving room to make new partitions for Ubuntu.  I forgot to deal with my MBR, however.  Grub was apparently on the Suse side and when I deleted the partition, now I can't boot.  Now I get a prompt:
```

grub>
```

and I have no idea how to make it boot.  Help?

---

### Post by scrooge_74 on 2007-01-10
Put the Live CD in, boot from it and when installing it should detect your windows and fix the GRUB

---

### Post by Frak on 2007-01-10
Let me look up the right commands, but from that prompt you can boot from windows from there, but try these for now, this is assuming Windows is on your first harddrive

```
root (hd0,0)
savedefault
makeactive
chainloader +1
boot

```

Enter those one line at a time, as in root (hd0,0), then savedefault, makeactive, etc.

---

### Post by humphry on 2007-01-10
Thanks, but I can't get root (hda0,0) to work.  The windows partition is the second on the drive (after a diagnostic one) but combinations of hda0,0 all the way through hda2,2 don't work.  Neither does sda.

---

### Post by confused57 on 2007-01-10
You can restore the Windows mbr to boot Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or

You can go ahead and install Ubuntu on the partition(s) that contained Suse, Ubuntu will install grub to the mbr & you should be able to boot Windows or Ubuntu.

Here's an excellent guide for grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

