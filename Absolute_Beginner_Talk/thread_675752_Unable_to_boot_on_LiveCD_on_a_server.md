---
title: "Unable to boot on LiveCD on a server"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by zedtux on 2008-01-23
Hi all !!

I got an old server at home ( PIII 850Mhz, 512Mo SDRAM ) with a SCSI controller card with 6 disks.
I'm trying to boot on LiveCD ... But after that I've boot menu and select Launch or install Ubuntu, the launch stop and I got at my screen :

```
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initranfs)
```

I have never work with a SCSI controler ... So I think that's the problem ... ?

Can you help me please ? Many thanks. :)

---

### Post by kellemes on 2008-01-23
Hhmm.. don't know really.

Maybe you should try the alternate installcd?
The liveCD is quit a big boy, it isn't really made with older hardware in mind.
To get the alternate installer visit the Ubuntu downloadpage and tick the checkbox somewhere at the bottom.

Edit: Or.. if you're only interested in a livesystem go look at some other options like Xubuntu, Zenwalk or one of the many other lighter distro's with a livecd.

---

### Post by mikeyphi on 2008-01-23
Are you trying to install the Desktop or Server version?

---

### Post by zedtux on 2008-01-23
Hi !

Many Thanks all for your reply !

**@ kellemes :**I've think about alternate edition ... OK I download it and I try it.
Thanks kellemes !

**@ mikeyphi :** I'm trying to install Desktop version.

---

### Post by zedtux on 2008-01-25
Ok, with the Alternate version, Ubuntu kernel boot ( with error on my sda disk ).

Now, my new problem is that ... the setup who come from the cd-rom ... can't find my ... cd-rom :confused:

My CD-ROM is an IDE CD-ROM, and sda is my SCSI disks...
Is that the problem ??

Thanks in advance :)

---

### Post by mikeyphi on 2008-01-25
Could you post the contents of    /etc/fstab

---

### Post by zedtux on 2008-01-25
Thanks for your quick answer !!

I've change CD-ROM drive, and now I can install Ubuntu !!! :guitar:
So I think this very old drive need driver.. (very strange... I allready think that old hardware are supported natively...)

So Now I can rock !! :lolflag:

---

