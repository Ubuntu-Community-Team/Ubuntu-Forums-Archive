---
title: "Dual Boot Problem"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Thierrylafronde on 2008-03-10
Hi People,
I wonder if one of you could help me.
I have been trying to dual boot a box running XP and Ubuntu 7.10.
Invariably, I am faced with the same problem, grub loads, the boot menu appears but if I choose 
Windows XP, it states "Starting up", then nothing.
If I choose Ubuntu, it boots to it fine.
It seems to me that somehow, Grub has screwed up my MBR.
Any tip would be welcome.
I need to keep both Oss as my 3 year old son plays games which do not work on Linux.
Cheers

---

### Post by mikewhatever on 2008-03-10
Please post the following additional info:
output of <sudo fdisk -l>
output of <cat /boot/grub/device.map>
output of <cat /boot/grub/menu.lst>

---

### Post by Thierrylafronde on 2008-03-10
Thanks Mike.
Unfortunately, in my infinite wisdom I forgot to update the post.
In a rare moment of foolishness I used Fixmbr form the XP console using the XP cd
and now nothing boots at all.
Sorry for being a cock.

---

### Post by mikewhatever on 2008-03-10
Well, you can reinstall GRUB from Ubuntu live CD [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29).
When Ubuntu boots again, post the requested info.

---

### Post by Thierrylafronde on 2008-03-11
Hi Mike,
I had reformatted the HD recently so did not have much data to retrieve. I booted using Hirens boot cd and restored the partition table so then booting on Ubuntu Live DVD I was able to transfer all my files to an external drive.
I now want this dual boot to be configured properly from scratch.
Could you recommend a step by step process (i.e.which OS do I install first).Or point to a link?:guitar:
I have 250GB ready to be formatted, I just want 75GB for XP and the rest for Ubuntu.
Thanking you in advance.
Cheers

---

### Post by jan quark on 2008-03-11
check this out:

I would install windows first, and then ubuntu
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by Thierrylafronde on 2008-03-11
Thanks Jan.Will try it out tonight and let you know what happened.
Cheers
:)

---

### Post by sandysandy on 2008-03-11
> **Thierrylafronde said:**
> Hi Mike,
I had reformatted the HD recently so did not have much data to retrieve. I booted using Hirens boot cd and restored the partition table so then booting on Ubuntu Live DVD I was able to transfer all my files to an external drive.
I now want this dual boot to be configured properly from scratch.
Could you recommend a step by step process (i.e.which OS do I install first).Or point to a link?:guitar:
I have 250GB ready to be formatted, I just want 75GB for XP and the rest for Ubuntu.
Thanking you in advance.
Cheers

win XP installs on NTFS partition, Ubuntu on ext3 partition. u can either do partitioning in advance or later. if u are comfortable with third party utility like gparted u can use it to partition ur disk. u can make max 4 primary partitions. u can also make one extended partition (inlieu of one primary partition) which can be further partitioned. ubuntu root [COLOR="Blue"]/[/COLOR] partition can be about 10gb, SWAP twice ur RAM size.
1. partition ur disk 
2.  install Win XP first (NTFS partition)
3.  install Ubuntu to other partition ( ext3 partition)
4. at end of install ubuntu will give u option to install to MBR.
5. once ubuntu installation finishes on rebooting u should get option to boot ubuntu and winXP.

heres a good link to dual booting

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by Thierrylafronde on 2008-03-11
Thank you muchly Sandy.
:popcorn:

---

### Post by Thierrylafronde on 2008-03-12
Well, I reformatted the HD, reinstalled XP then Ubuntu only this time I chose "Advanced" and unticiked "Install a BootLoader" as Grub caused me aggro last time round.
Now when I boot, I get "Error Loading OS", seems I have a problem with NT loader now.
What's next, Fixmbr from the XP console or else?
Cheers

---

### Post by jan quark on 2008-03-12
try this app to restore or repair the boot loader

[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

### Post by Thierrylafronde on 2008-03-12
Thanks Jan, I will try it out tonight as I am at work right now although I reiterate that I did not install Grub in the first place.
Cheers

---

### Post by ugokcu on 2008-03-12
hello people;
&#305; just setup ubuntu but I have a problem. If I don't delete splash quite, black screen appears and my computer freezes. Do I have to delete splash quite every time before booting or is there another easyway?

---

### Post by jan quark on 2008-03-12
you can probably edit the menu.lst file

make a backup of it first with

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

then open it with
```

gksudo gedit /boot/grub/menu.lst
```

and change it according to your needs

---

### Post by ugokcu on 2008-03-12
thanks a lot jan. I will try.

---

### Post by Thierrylafronde on 2008-03-13
Well, I tried again the same process to no avail so I deleted the Linux Partition, rewrote both the Boot sector and the MBR on the NTFS partition, NTLoader failed to work.
Reformatted the NTFS, reinstalled XP then Ubuntu with Grub and everything works now.
Thank you all for your suggestions.
Think Pengouin.:guitar:

---

