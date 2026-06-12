---
title: "rEFIt not syncing"
date: 2009-12-14
forum: Apple Hardware Users
---

### Post by pyro2927 on 2009-12-14
I know this has been posted alot, and I've been through all related posts.  I currently am triple booting OS X 10.6, Windows 7, and Ubuntu 9.10.

I installed rEFIt under OS X and it loads correctly, but I only have options for OS X and Windows on the selection screen.

My partition table:
1 - EFI System
2 - Mac OSX HFS+
3 - Windows
4 - Grub
5 - Ubuntu 9.10
6 - Linux Swap

When I start up the partition tool in rEFIt I get an error:
```
Status: GPT partition of type 'Unknown' found, will not touch this disk.
```

When I run ```
sudo gptsync /dev/sda
``` in my Ubuntu partition I get:
```
Status: Tables are synchronized, no need to sync.
```

I followed [this guide]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic") for setting everything up, and all features work.  I'm only having trouble with properly setting up rEFIt.

I've already reinstalled grub to /dev/sda

Any help would be greatly appreciated :)

Edit: in rEFIt if I choose the Windows partition to boot to, it loads into grub and I can select Ubuntu or Windows from that screen.

---

### Post by tom4everitt on 2009-12-14
It sounds like its interpreting you're grub as windows then. So maybe it's actually your windows entry that are missing?

---

### Post by _mario_ on 2009-12-15
> **tom4everitt said:**
> It sounds like its interpreting you're grub as windows then. So maybe it's actually your windows entry that are missing?

ack. Ubuntu Karmic uses Grub version 2, which isn't correctly recognized by rEFIt. instead rEFIt will display a generic windows-like icon. 

@op:
have a look at the text below the icons, that state where rEFIt will boot from, e.g: "MacOS X from Partition 2". then re-install the missing boot loader (either Grub or Windows) by following one of a thousand tutorials out there.

your error message may also indicate, that you have a GPT partition with unknown type GUID, so gptsync refuses to touch your disk. since, i have a partition with unknown type GUID as well, i ran gptsync, and can confirm the it worked for me.

btw: shouldn't windows be the last MBR-visible partition? can you boot your windows?

ciao,
Mario

---

### Post by jamesey on 2009-12-17
are the rEFIt people aware of this? they haven;t released an update since March. 

Would using Bootcamp fix this issue?

---

