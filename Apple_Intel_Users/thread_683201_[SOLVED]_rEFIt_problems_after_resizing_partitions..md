---
title: "[SOLVED] rEFIt problems after resizing partitions."
date: 2008-01-30
forum: Apple Intel Users
---

### Post by MarcelloSav on 2008-01-30
Hello guys,
I have a problem with my MacBook and refit... A few hours ago I resized partitions with gparted and I had no problems, but when I rebooted Linux partition disappeared. I tried to search on refit site in troubleshooting documentation, but I've only found this:

[http://refit.sourceforge.net/doc/c4s5_parted.html](http://refit.sourceforge.net/doc/c4s5_parted.html)

that seems to be my problem but i can't solve it.
I tried to change the flag boot on gparted, but nothing changed. I only have to try with fdisk but i can't do it (i never needed to work with fdisk).
Can anybody help me?
It's very important for me...

PS:

My GPT table is

EFI SYSTEM
MAC OS HFS+
EFI SYSTEM (that is linux partition)
LINUX SWAP

my mbr table is

EFI PROTECTIVE
MAC OS HFS+
LINUX
LINUX SWAP...

Thanks you all guys,
Marcello

---

### Post by cyberdork33 on 2008-01-30
I don't know why you got that issue, it was kind of old. 

you should just be able to boot the Ubuntu CD, start the partition editor (gparted) select the partition and remove the boot flag. The "flags" are shown for each partition in the very far right column, and you can edit the flags by right-clicking on a partition and selecting "Manage Flags".

---

### Post by MarcelloSav on 2008-01-31
I already did... :cry:
If I remove the flag, at the refit boot appears a "Legacy Boot OS", but it's not linux. When I choose it I have an error "Missing operating system"...

I have to remove the boot flag only to linux or to macOs too?

---

### Post by hajk on 2008-01-31
Did you resynch GPT and the MBR partition table?

---

### Post by MarcelloSav on 2008-01-31
> **hajk said:**
> Did you resynch GPT and the MBR partition table?

Yes, but there is no change... I have the same problem... I will get home later, I will post you the differences between tables with boot flag active and not.

Bye ;)

---

### Post by cyberdork33 on 2008-01-31
> **MarcelloSav said:**
> Hello guys,
I have a problem with my MacBook and refit... A few hours ago I resized partitions with gparted and I had no problems, but when I rebooted Linux partition disappeared.
I just reread your initial post. When did you resize? Was this after you had already installed linux or did you resize your OSX partition to install Ubuntu? 


If you resized your partitions after install, then you may need to reinstall grub.

---

### Post by MarcelloSav on 2008-01-31
I resized after I already installed Ubuntu...
So do you think it's enough to reinstall Grub? It would be great!
I have to reinstall with boot flag non-active? 

Thanks ;)

---

### Post by cyberdork33 on 2008-01-31
> **MarcelloSav said:**
> I resized after I already installed Ubuntu...
So do you think it's enough to reinstall Grub? It would be great!
I have to reinstall with boot flag non-active? 

Thanks ;)
yea don't worry about the boot flag. There is no need for it on a GPT disk.
Try this:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

### Post by MarcelloSav on 2008-02-01
Ok, grub reinstallation solved my problem! :)

Thanks guys, you're so precious...

Bye...

---

### Post by cyberdork33 on 2008-02-01
please mark as solved!

---

### Post by MarcelloSav on 2008-02-02
> **cyberdork33 said:**
> please mark as solved!

Sorry, I forgot ;)

---

