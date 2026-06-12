---
title: "More than four partitions on a MacBook?"
date: 2009-12-22
forum: Apple Hardware Users
---

### Post by skullmunky on 2009-12-22
I have Macbook Pro (5,1), with an OSX partition and an Ubuntu partition.  I'd like to add one more Ubuntu partition, because I have some apps which have to be in AMD64 and some that have to be in i386.  

So I think what I need to do is turn the Ubuntu partition from a Primary to and Extended (I guess by resizing it, creating an Extended, copying everything over, and then deleting the original Primary one..?)  So I could see myself ending up with a partition table like this:

EFI
OSX
Extended
   Ubuntu amd64
   Ubuntu i386
   /home
   swap

will that work or will that create other problems syncing with EFI?

or should I be looking at trying to create an i386 chroot instead of going this route?

---

### Post by tom4everitt on 2009-12-23
Exactly why don't you just create your new partitions as extended and skip the shuffling of files and deletion of the original one?

Otherwise I can only say that I think refit partition tool should be able to sync your partition afterwards, but its slightly risky of course... Do a backup before ;)

---

### Post by renkinjutsu on 2009-12-23
you can run both amd64 and i386 programs on a 64bit OS. Why not just have one Ubuntu partition?

edit: you can also create your own i386 environment with [debootstrap]("https://help.ubuntu.com/community/DebootstrapChroot")

---

### Post by skullmunky on 2009-12-24
The reason for wanting 32 bit is just that I'm doing dev work on something that has to link against a 32 bit library, which is proprietary and unfortunately also abandonware ;) so I'm stuck with it for archival reasons.  But I think renkinjutsu is right, deboostrap is probably the more sane solution.  

It didn't seem to me like I could create new partitions as extended and get anywhere with that because I already have 4 primaries ... I thought the idea with the extended partitions is that you use up one of your 4 slots and it has more logical partitions inside it, but I may be misunderstanding that.

---

### Post by mickie.kext on 2009-12-24
Hi skullmunky,

Macs are formated in GUID Partition Table (GPT) by default, not MBR, and that means that there is no extended and logical partions, just primary ones. On GPT disk, you can have up to 128 partitions. 

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

OS X (hackintosh distros aside) can not even install on MBR disks, so you positively have GPT. So no wories, just make as much primary partition you need.

PS: Unless... did you used GPTsync/rEFIt/BootCamp for making hybrid of GPT/MBR? If you did then you can have problems if you create more that 4 partitions.

---

### Post by skullmunky on 2009-12-29
yeah, the extra partition is certainly there; it's visible from OSX and also in Ubuntu it shows up automagically in the Dolphin sidebar.  I did use refit to create an MBR table too ... of course it won't sync that anymore, though it claims it is.  

Hm, what problems will that create?

If a partition is there in the GPT but not in MBR, does the MBR even matter?  How do I add the partition to fstab?  And, can I boot it from grub?

thanks,

--skullmunky

---

### Post by _mario_ on 2009-12-30
> **skullmunky said:**
> yeah, the extra partition is certainly there; it's visible from OSX and also in Ubuntu it shows up automagically in the Dolphin sidebar.  I did use refit to create an MBR table too ... of course it won't sync that anymore, though it claims it is.  

Hm, what problems will that create?

you cannot boot an OS off a partition past the first 4 using legacy BIOS emulation, e.g.: Windows or Linux using Grub version 1. Linux with Grub version 2 (Karmic default) works. 

> **skullmunky said:**
> 
If a partition is there in the GPT but not in MBR, does the MBR even matter? 

Legacy boot loaders will need it.

> **skullmunky said:**
> 
And, can I boot it from grub?

If you use Grub version 2.

ciao,
Mario

---

### Post by skullmunky on 2009-12-30
ok, I think I'm getting closer to understanding ... 

First, I'm only planning on having osx and various linux flavors, no windows on here.  So if I use Grub 2, then I can just use GPT and forget all about the MBR partitions?

Now let's say I can't use grub 2 just yet - would something like this work ?

1. EFI
2. OSX
3. root ( ubuntu 9.04 x86_64)
4. root ( fedora 12 i386 )
5. home
6. swap

everything after the 4th one will be left out of the MBR table, but it shouldn't matter because grub is on partition 3  ... ?

---

### Post by _mario_ on 2009-12-30
> **skullmunky said:**
> 
First, I'm only planning on having osx and various linux flavors, no windows on here.  So if I use Grub 2, then I can just use GPT and forget all about the MBR partitions?

yes.

> **skullmunky said:**
> 
Now let's say I can't use grub 2 just yet - would something like this work?

1. EFI
2. OSX
3. root ( ubuntu 9.04 x86_64)
4. root ( fedora 12 i386 )
5. home
6. swap

everything after the 4th one will be left out of the MBR table, but it shouldn't matter because grub is on partition 3  ... ?

yes. but no more room for a 3rd linux installation ;-)

ciao,
Mario

---

### Post by skullmunky on 2009-12-30
:)  ok one more:  will this work?  because it seems like fedora wants a separate /boot partition.

1. EFI
2. OSX
3. /boot
4. /  (Ubuntu)
5. /  (Fedora)
6. /home
7. swap

---

### Post by _mario_ on 2009-12-30
> **skullmunky said:**
> :)  ok one more:  will this work?  because it seems like fedora wants a separate /boot partition.
1. EFI
2. OSX
3. /boot
4. /  (Ubuntu)
5. /  (Fedora)
6. /home
7. swap
yes. in fact it's the partition the linux kernel resides, i.e. the boot partition (mounted to /boot) or the root partition (that contains /boot) if setting up without a separate boot partition.

ciao,
Mario

---

### Post by skullmunky on 2009-12-31
So I just wanted to report on what I ended up with, which works just fine despite a couple odd quirks.

1. EFI
2. OSX
3. Ubuntu Jaunty 64 bit
4. Fedora 12 32 bit
5. Ubuntu Karmic 32 bit
6. data 
7. swap

All of those are primary GPT partitions.  refit will let me boot sda2, sda3, and sda4, but not sda5 - it says "No operating system".  

I tried adding the line for my Karmic 32 into the Grub menu in my Jaunty 64 install, but somehow borked it and couldn't boot it anymore.  Not to worry, though, the Grub on my Fedora install can boot all of them, including the Karmic install on sda5 using the chainloader option.  

This does result in a slightly confusing boot process where I go through 3 levels of menus, which have essentially the same options in them with various levels of detail, but since it's my own machine and not one that has to make sense to anyone else that's just fine :)

---

### Post by bkadoctaj on 2010-02-21
> **_mario_ said:**
> yes.


yes. but no more room for a 3rd linux installation ;-)

ciao,
Mario

Hi, I'm wondering why there would be no more room for a third Linux OS.

---

